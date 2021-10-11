---
description: >-
  Geef de artists page data weer op je website en style deze volgens het
  ontwerp!
---

# Structureer en style de Artists page JSX

## Taak: Voeg toe en pas de JSX structuur aan voor je Artists Page

Importeer de `GatsbyImage` component en de `getImage` hulpfunctie. Voeg de onderstaande JSX toe aan de return waarde van je page component:

{% code title="src/pages/artists/index.js" %}
```jsx
// imports
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Artist from "../../components/artist"

const ArtistsPage = ({
  data: {
    allWpArtist: { edges: artistsInfo },
    wpPage: { artistsPage },
  },
}) => {
  const image = getImage(artistsPage.headerArtists.picture.localFile)
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      <GatsbyImage
        image={image}
        alt={artistsPage.headerArtists.picture.altText}
      />
      <div>
        <h2>{artistsPage.headerArtists.title}</h2>
        <div
          dangerouslySetInnerHTML={{
            __html: artistsPage.headerArtists.description,
          }}
        />
        <div>
          {artistsInfo.map(({ node: artist }) => (
            <Artist key={artist.id} slug={artist.slug} artist={artist} />
          ))}
        </div>
      </div>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

Vergeet niet je `Artist` component te importeren!

{% hint style="info" %}
**Pro tip 🧙‍♂**: In de `map`-functie deconstrueer je elk element waarover je itereert. Je haalt er de `node` uit en geeft het een nieuwe naam namelijk `artist`.
{% endhint %}

## Taak: Voeg CSS toe aan je Artists page JSX  ✨

Verschillende CSS classes uit je `page.module.css` kan je hergebruiken.

* Navigeer naar je CSS bestand voor je page in je `src`-directory `page.module.css`.
* Voeg volgende CSS classes vanonder in je file toe.

{% code title="src/page.module.css" %}
```css
// Page CSS

.hero {
  width: 120vw;
  height: 500px;
  transform: translateX(calc((-120vw + 1080px) / 2));
  border-bottom-left-radius: 50%;
  border-bottom-right-radius: 50%;
}

.description {
  max-width: 600px;
  margin: auto;
}

@media screen and (max-width: 1200px) {
  .hero {
    transform: translateX(-5%);
  }
}
```
{% endcode %}

* Importeer de CSS classes in je `src/pages/artists/index.js`.

{% code title="src/pages/artists/index.js" %}
```jsx
import * as React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../../components/layout"
import Artist from "../../components/artist"
import {
  hero,
  section,
  subtitle,
  artists,
  description,
} from "../../page.module.css"

// Artists Page Component
```
{% endcode %}

* Voeg de CSS classes toe aan je page component zoals hieronder weergegeven:

{% code title="src/pages/artists/index.js" %}
```jsx
// Imports

const ArtistsPage = ({
  data: {
    allWpArtist: { edges: artistsInfo },
    wpPage: { artistsPage },
  },
}) => {
  const image = getImage(artistsPage.headerArtists.picture.localFile)
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      <GatsbyImage
        className={hero}
        image={image}
        alt={artistsPage.headerArtists.picture.altText}
      />
      <div className={section}>
        <h2 className={subtitle}>{artistsPage.headerArtists.title}</h2>
        <div
          className={description}
          dangerouslySetInnerHTML={{
            __html: artistsPage.headerArtists.description,
          }}
        />
        <div className={artists}>
          {artistsInfo.map(({ node: artist }) => (
            <Artist key={artist.id} slug={artist.slug} artist={artist} />
          ))}
        </div>
      </div>
    </Layout>
  )
}
// Page Query
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

Proficiat! 🏆Je hebt het einde bereikt van dit hoofdstuk! Je artists page is volledig gestyled. In het volgende hoofdstuk zal je de individuele Artist page herstructuren en stylen! ✨
