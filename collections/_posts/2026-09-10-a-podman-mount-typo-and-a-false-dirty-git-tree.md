---
layout: post
title: "A small setup for using podman with Jenkins"
categories: [ci, jenkins, podman]
---

*This post was partly written with the help of AI.*

If you're new to podman, or still not sure whether to switch from Docker, this is a good primer: [Is Docker Still Worth It in 2026? Or Should You Switch to Podman?](https://medium.com/@surbhi19/is-docker-still-worth-it-in-2026-or-should-you-switch-to-podman-29d89b42dc80)

Unlike Docker, podman doesn't have an official Jenkins plugin. There's no dedicated node type, no registry/credential DSL, nothing to install from the plugin manager. In practice that's not a big loss — it just means every podman command is a plain shell invocation inside a `steps { sh "..." }` block, like any other CLI tool on the agent.

## A minimal pipeline

Here's the shape of a pipeline that builds an image and pushes it:

```groovy
pipeline {
    agent {
        label 'my-agent'
    }

    environment {
        IMAGE_NAME = "my-image"
        REGISTRY   = "registry.example.com"
    }

    stages {
        stage('Build') {
            steps {
                sh """
                    podman build --tag ${REGISTRY}/${IMAGE_NAME}:latest .
                """
            }
        }

        stage('Push') {
            steps {
                sh "podman push ${REGISTRY}/${IMAGE_NAME}:latest"
            }
        }
    }
}
```

Nothing exotic — `podman` behaves the same on the CLI whether Jenkins is calling it or you are. But one thing bit me while wiring this up for real, worth knowing before you hit it yourself.

## The minor problem

If a stage needs to inspect the repo — for example, running a versioning tool inside its own container — the natural move is to bind-mount the workspace in:

```groovy
sh "podman run --rm -v \"${WORKSPACE}\":/repo ${REGISTRY}/misc/get-version:1.2.1"
```

It's tempting to "simplify" that to `-v "${WORKSPACE}"`, since the host and container path feel redundant. Don't. `-v /host/path` with no `:dest` isn't shorthand for "mount at the same path" — podman creates a brand-new **anonymous volume** and mounts it at that path inside the container instead, completely empty. The tool inside sees an empty directory, not your repo, and fails or falls back silently rather than erroring loudly. Always write both sides of the mount: `<host-path>:<container-path>[:ro]`.