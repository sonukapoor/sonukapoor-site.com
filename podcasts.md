---
layout: page
title: "Podcasts – Sonu Kapoor (Angular Catch-Up co-host)"
page_title: Podcasts Featuring Sonu Kapoor – Angular Catch-Up & Guest Appearances
permalink: /podcasts/
image: /images/og/podcasts-og.png
description: "Podcasts featuring Sonu Kapoor — co-founder and co-host of Angular Catch-Up — covering Signals, SSR & Hydration, SignalStore, httpResource, and modern Angular releases."
keywords:
  - Sonu Kapoor
  - Podcasts
  - Angular podcast
  - Angular Catch-Up
  - Signals
  - SSR
  - Hydration
  - SignalStore
  - httpResource
  - Angular v18
  - Angular v19
  - Angular v20
  - Web Performance
schema:
  "@context": "https://schema.org"
  "@graph":
    - "@type": "CollectionPage"
      "@id": "https://sonukapoor.com/podcasts/#collectionpage"
      url: "https://sonukapoor.com/podcasts/"
      name: "Podcasts – Sonu Kapoor"
      description: "A curated list of podcasts co-hosted by or featuring Sonu Kapoor."
      isPartOf: { "@id": "https://sonukapoor.com/#website" }
      mainEntity: { "@id": "https://sonukapoor.com/podcasts/#itemlist" }
      about: { "@id": "https://sonukapoor.com/#person" }

    # Podcast series nodes
    - "@type": "PodcastSeries"
      "@id": "https://angular-catch-up.podbean.com/#series"
      name: "Angular Catch-Up"
      url: "https://angular-catch-up.podbean.com/"
      sameAs: ["https://angular-catch-up.podbean.com/"]
      producer: { "@id": "https://sonukapoor.com/#person" }
      inLanguage: "en"

    - "@type": "CreativeWorkSeries"
      "@id": "https://www.youtube.com/@ThisIsTechTalks#series"
      name: "This is Tech Talks"
      url: "https://www.youtube.com/@ThisIsTechTalks"
      sameAs: ["https://www.youtube.com/@ThisIsTechTalks"]
      inLanguage: "en"

    # The item list of episodes/series links on this page
    - "@type": "ItemList"
      "@id": "https://sonukapoor.com/podcasts/#itemlist"
      itemListElement:
        - "@type": "ListItem"
          position: 1
          item:
            "@type": "PodcastEpisode"
            name: "httpResource in Angular — The Future of API Communication (with Alex Rickabaugh)"
            url: "https://angular-catch-up.podbean.com/e/httpresource-in-angular-the-future-of-api-communication/"
            isPartOf: { "@id": "https://angular-catch-up.podbean.com/#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
            potentialAction:
              "@type": "ListenAction"
              target: "https://angular-catch-up.podbean.com/e/httpresource-in-angular-the-future-of-api-communication/"
        - "@type": "ListItem"
          position: 2
          item:
            "@type": "PodcastEpisode"
            name: "Testing Done Right (with Rainer Hahnekamp)"
            url: "https://angular-catch-up.podbean.com/e/testing-done-right-where-to-start-what-to-use-and-what-s-next-with-rainer-hahnekamp/"
            isPartOf: { "@id": "https://angular-catch-up.podbean.com/#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
            potentialAction:
              "@type": "ListenAction"
              target: "https://angular-catch-up.podbean.com/e/testing-done-right-where-to-start-what-to-use-and-what-s-next-with-rainer-hahnekamp/"
        - "@type": "ListItem"
          position: 3
          item:
            "@type": "PodcastEpisode"
            name: "Angular v19 — Advanced Features (with Minko Gechev)"
            url: "https://angular-catch-up.podbean.com/e/angular-v19-advanced-features-with-minko-gechev/"
            isPartOf: { "@id": "https://angular-catch-up.podbean.com/#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
            potentialAction:
              "@type": "ListenAction"
              target: "https://angular-catch-up.podbean.com/e/angular-v19-advanced-features-with-minko-gechev/"
        - "@type": "ListItem"
          position: 4
          item:
            "@type": "PodcastEpisode"
            name: "SSR in Angular v19 (with Alan Agius)"
            url: "https://angular-catch-up.podbean.com/e/ssr-in-angular-v19-a-new-era-of-performance-with-alan-agius/"
            isPartOf: { "@id": "https://angular-catch-up.podbean.com/#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
            potentialAction:
              "@type": "ListenAction"
              target: "https://angular-catch-up.podbean.com/e/ssr-in-angular-v19-a-new-era-of-performance-with-alan-agius/"
        - "@type": "ListItem"
          position: 5
          item:
            "@type": "PodcastEpisode"
            name: "Hydration — A Fresh Take on the Future of SSR (with Jessica Janiuk)"
            url: "https://angular-catch-up.podbean.com/e/angular-ssr-deep-dive-with-jessica-janiuk/"
            isPartOf: { "@id": "https://angular-catch-up.podbean.com/#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
            potentialAction:
              "@type": "ListenAction"
              target: "https://angular-catch-up.podbean.com/e/angular-ssr-deep-dive-with-jessica-janiuk/"
        - "@type": "ListItem"
          position: 6
          item:
            "@type": "PodcastEpisode"
            name: "Unpacking SignalStore (with Alex Okrushko & Marko Stanimirović)"
            url: "https://angular-catch-up.podbean.com/e/unpacking-signalstore-the-future-of-reactive-state-management-in-angular/"
            isPartOf: { "@id": "https://angular-catch-up.podbean.com/#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
            potentialAction:
              "@type": "ListenAction"
              target: "https://angular-catch-up.podbean.com/e/unpacking-signalstore-the-future-of-reactive-state-management-in-angular/"
        - "@type": "ListItem"
          position: 7
          item:
            "@type": "WebSite"
            name: "This is Tech Talks — Channel"
            url: "https://www.youtube.com/@ThisIsTechTalks"
            isPartOf: { "@id": "https://www.youtube.com/@ThisIsTechTalks#series" }
            about: { "@id": "https://sonukapoor.com/#person" }
---

I co-host shows and appear on podcasts to talk Angular, Signals, SSR, and modern frontend architecture. Here’s a curated list of episodes and series.

<div class="media-grid">

  <!-- Angular Catchup (series) -->
  <div class="card">
    <h3>Angular Catchup — Co-hosted Series</h3>
    <div class="card-meta">Podcast Series</div>
    <p class="card-desc">A show I co-host covering Angular, performance, SSR, and modern patterns with leaders from the Angular team and community.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/" target="_blank" rel="noopener">Listen to the show →</a>
    </div>
  </div>

  <!-- Individual episodes from README -->
  <div class="card">
    <h3>httpResource in Angular — The Future of API Communication</h3>
    <div class="card-meta">Guest: Alex Rickabaugh • Angular Catchup</div>
    <p class="card-desc">Deep dive into the signal-based <code>HttpResource</code> API and how it simplifies async state and type-safe data flows.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/httpresource-in-angular-the-future-of-api-communication/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>Testing Done Right: Where to Start, What to Use, and What’s Next</h3>
    <div class="card-meta">Guest: Rainer Hahnekamp • Angular Catchup</div>
    <p class="card-desc">Avoid flaky tests and maintenance nightmares with practical strategies that actually add value.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/testing-done-right-where-to-start-what-to-use-and-what-s-next-with-rainer-hahnekamp/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>Angular v19 — Advanced Features</h3>
    <div class="card-meta">Guest: Minko Gechev • Angular Catchup</div>
    <p class="card-desc">Partial Hydration, Reactivity, security, HMR and more—what’s landing and how to use it.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/angular-v19-advanced-features-with-minko-gechev/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>SSR in Angular v19 — A New Era of Performance</h3>
    <div class="card-meta">Guest: Alan Agius • Angular Catchup</div>
    <p class="card-desc">What the latest SSR updates mean for performance, SEO, and developer experience.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/ssr-in-angular-v19-a-new-era-of-performance-with-alan-agius/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>Angular SSR Deep Dive</h3>
    <div class="card-meta">Guest: Jessica Janiuk • Angular Catchup</div>
    <p class="card-desc">Hydration, scaling SSR apps, AnalogJS support, and real-world tips.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/angular-ssr-deep-dive-with-jessica-janiuk/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>Unpacking SignalStore</h3>
    <div class="card-meta">Guests: Alex Okrushko &amp; Marko Stanimirović • Angular Catchup</div>
    <p class="card-desc">Why SignalStore is shaping the future of state management and how to adopt it.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/unpacking-signalstore-the-future-of-reactive-state-management-in-angular/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>Angular v18 — Advanced Features</h3>
    <div class="card-meta">Guest: Minko Gechev • Angular Catchup</div>
    <p class="card-desc">What shipped in v18 and how it changes app architecture and DX.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/angular-v18-advanced-features-with-minko-gechev/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <div class="card">
    <h3>Signals with Paweł Kozłowski</h3>
    <div class="card-meta">Guest: Paweł Kozłowski • Angular Catchup</div>
    <p class="card-desc">Signals best practices, capabilities, challenges, and future direction.</p>
    <div class="card-actions">
      <a href="https://angular-catch-up.podbean.com/e/signals-with-pawel-kozlowski-from-the-angular-team/" target="_blank" rel="noopener">Listen →</a>
    </div>
  </div>

  <!-- This is Tech Talks (series) -->
  <div class="card">
    <h3>This is Tech Talks — Co-hosted Series</h3>
    <div class="card-meta">YouTube Live Show</div>
    <p class="card-desc">A live talk show co-hosted with Santosh Yadav featuring conversations across the web platform and adjacent tech.</p>
    <div class="card-actions">
      <a href="https://www.youtube.com/@ThisIsTechTalks" target="_blank" rel="noopener">Watch on YouTube →</a>
    </div>
  </div>

</div>
