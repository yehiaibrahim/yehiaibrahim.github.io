---
layout: about
permalink: /about/
title: A little bit about me.
tags: about
---

### Origins

I was born and raised in Giza, Egypt — a place most known for the pyramids, but more recently, the grand egyptian museum.

<div class="hero-images-container">
  <div class="hero-images">
    <div>
      <img src="/images/about/pyramids.jpg" alt="The Pyramids of Giza, Egypt" style="border-radius: 0.4em;">
      <div style="color: #777; font-size: 0.96em; padding-top: 0.4em; text-align: center;">
        The Pyramids of Giza, Egypt &mdash;.
      </div>
    </div>
    <div>
      <img src="/images/about/grand_museum.jpg" alt="The Grand Museum" style="border-radius: 0.4em;">
      <div style="color: #777; font-size: 0.96em; padding-top: 0.4em; text-align: center;">
        The Grand Museum, Giza.
      </div>
    </div>
  </div>
</div>

Even though I live 20 minutes away from the pyramids, I have been there only once in my life as a kid, I guess you do not really know
how important something is, if you are used to it.

<style>
.hero-images-container {
  width: 100vw;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  margin-bottom: 2em;
}

.hero-images {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.hero-images img {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

@media screen and (max-width: 768px) {
  .hero-images {
    grid-template-columns: 1fr;
  }

  .hero-images img {
    height: 300px;
  }
}

.modal-images-container {
  width: 100vw;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  margin-bottom: 2em;
}

.modal-images {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

.modal-images img {
  width: 100%;
  height: 400px;
  object-fit: cover;
}

.modal-captions {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  max-width: 1200px;
  margin: 0.5rem auto 0;
  padding: 0 1rem;
}

.modal-captions figcaption {
  text-align: center;
}

@media screen and (max-width: 768px) {
  .modal-images {
    grid-template-columns: 1fr;
  }

  .modal-images img {
    height: 300px;
  }

  .modal-captions {
    grid-template-columns: 1fr;
  }
}

.highlight-face {
  position: relative;
}

.highlight-face img {
  position: relative;
}

.highlight-face::after {
  content: '';
  position: absolute;
  top: 40%;
  left: 50%;
  width: 30px;
  height: 30px;
  border: 3px solid rgba(255, 87, 34, 0.9);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none;
  box-shadow: 0 0 10px rgba(255, 87, 34, 0.5);
}

.highlight-face:hover::after {
  opacity: 1;
}
</style>





### Day-by-day

Currently, I work at Kontron AG, I joined in October 2023, and since Then I help build Embedded Linux devices, such as switches.
I work mainly on the build system and on the switch application. Even though my time at Kontron has not been that long, I feel
like having a second family.


### Where

<figure style="margin: 0; margin-bottom: 1em;">
  <img src="/images/about/saarbruecken.jpg" alt="Saarbrücken, Saarland" style="border-radius: 0.4em;">
</figure>

Today, I live in Saarbrücken. When I'm not working, you can find me - if it is not raining - walking in the altstadt. Even though the city is small, there's a lot to love in it, espcially in its approximity to other lovely cities.


### Past

Before working at Kontron, I worked at MRS Electronic as an Embedded systems Engineer, I worked there for only three month, still,
my time there was lovely.

Previous to MRS Electronic, I worked as working student at Fachhochschule Südwestfalen during my Master's studies. I helped developing
MLPro, an ML framework for standardized Machine Learning.

### Life

2025 was capped off with my marriage to Naira, the loveliest and sweetest person I have ever known. We're pretty excited about what's next.


<figure style="margin: 0; margin-bottom: 1em;">
  <img src="/images/about/proposal.jpg" alt="Proposal"
       style="border-radius: 0.4em; object-fit: cover; object-position: bottom; width: 100%; height: 600px;">
</figure>

<div id="stats" class="hidden">

<h3 id="dashboard"><code>#dashboard</code></h3>

<h2>Just finished.</h2>

<p>Curious what I'm reading? Here's my most recent reads, updating daily. And my <a href="https://www.goodreads.com/user/show/88184044-jonathon-belotti)" target="_blank" rel="noopener noreferrer">Goodreads profile</a> has more history.</p>

<div id="recent-finished-books"></div>

<h2>Top tracks.</h2>

<p>Curious what I'm currently listening to? Here's my top tracks on Spotify, updating daily.</p>

<ol id="top-spotify-tracks"></ol>

</div>

<script>
/**
 * @param {String} HTML representing a single element
 * @return {Element}
 */
function htmlToElement(html) {
    var template = document.createElement('template');
    /* Never return a text node of whitespace as the result */
    html = html.trim();
    template.innerHTML = html;
    return template.content.firstChild;
}

function populateDashboardHTML(data) {
    const topSpotifyTracksList = document.querySelector('#top-spotify-tracks');
    data.spotify.forEach(track => {
        topSpotifyTracksList.appendChild(htmlToElement(`
            <li>
                <a target="_blank" rel="noopener noreferrer" href="${track.link}"><strong>${track.name}</strong></a>
                <p>${track.artist}</p>
            </li>
        `));
    });

    const recentFinishedBooks = document.querySelector('#recent-finished-books');
    data.goodreads.slice(0, 3).forEach(book => {
        recentFinishedBooks.appendChild(htmlToElement(`
            <a target="_blank" rel="noopener noreferrer" class="book-item" target="_blank" rel="noopener noreferrer" href="${book.link}">
            <div class="cover-container">
                <img class="grow-me" src="${book.cover_image_link}">
            </div>
            <div class="book-info">
                <h4>${book.title}</h4>
                <p>${book.authors[0]}</p>
            </div>
            </a>
        `));
    });
}

fetch('https://thundergolfer--thundergolferdotcom-about-page-web.modal.run')
  .then((response) => {
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    return response.json();
  })
  .then((data) => {
    populateDashboardHTML(data);
    /* Reveal the now populated stats section. */
    document.getElementById("stats").classList.remove("hidden");
  });

</script>

<style>
#stats {
  background-color: #e8e4d9;
  border-radius: 1rem;
  padding: 1.5em;
  margin-top: 2.5em;
}

#dashboard {
  margin: 0rem;
}

#dashboard code {
  background-color: #e8e4d9;
}

#recent-finished-books {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: center;
}

#recent-finished-books a {
    color: #111;
}

.book-item {
    margin-left: 0.4em;
    margin-right: 0.4em;
}

.book-item div {
    width: 200px;
}

.book-info h4 {
    color: #222;
}

.book-info p {
    color: #555;
}

.grow-me {
  border-radius: 4px;
  transition: all .2s ease-in-out;
}

.grow-me:hover {
  transform: scale(1.02);
}

#top-spotify-tracks {
    padding-left: 1em;
}

#top-spotify-tracks li {
    color: #888;
    border-bottom: 1px solid #ededed;
    margin-top: 1rem;
}

#top-spotify-tracks a {
    color: #111;
}

#top-spotify-tracks a:hover {
    color: #1DB954; /* Spotify green */
}

#top-spotify-tracks p {
    color: #555;
}

.hidden {
    display: none;
}

@media screen and (max-width: 900px) {


  #recent-finished-books {
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .book-item div {
    width: 400px;
  }

  .book-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .cover-container, .book-info {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 80%;
  }

  #top-spotify-tracks {
    padding-left: 1.2em;
  }
}
</style>
