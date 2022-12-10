---
description: Geef de artist pictures weer op je website en style deze volgens het ontwerp!
---

# Structureer en style de pictures van je Artist page template

![Pictures op je Artist template page](<../../.gitbook/assets/image (114).png>)

## Taak: Voeg de JSX structuur toe voor je pictures op je Artist template page

Voeg de onderstaande JSX toe aan de return waarde van je page component:

{% code title="src/pages/artists/{wpArtist.slug}.js" %}
```jsx
// imports

const ArtistPage = ({
  data: {
    wpArtist: {
      artistMeta: artist,
      roles: { nodes: roles },
    },
  },
}) => {
  const image = getImage(artist.profilePicture.localFile)
  const picture1 = getImage(artist.picture1.localFile)
  const picture2 = getImage(artist.picture2.localFile)
  const picture3 = getImage(artist.picture3.localFile)

  return (
    <Layout pageTitle="Artist Template">
      // artist header JSX
      <section>
        {picture1 && (
          <GatsbyImage
            image={picture1}
            alt={artist.picture1.altText}
          />
        )}
        {picture2 && (
          <GatsbyImage
            image={picture2}
            alt={artist.picture2.altText}
          />
        )}
        {picture3 && (
          <GatsbyImage
            image={picture3}
            alt={artist.picture3.altText}
          />
        )}
      </section>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

## Taak: Sprinkle wat CSS op je Artist page template pictures  ✨

* Navigeer naar je page.module.css en voeg onderstaande CSS classes toe onderaan je file.

{% code title="src/page.module.css" %}
```css
.artist-pictures {
  position: relative;
  display: flex;
  justify-content: space-between;
  margin-top: 120px;
}

.artist-pictures::before,
.artist-pictures::after {
  position: absolute;
  display: inline-flex;
  content: "";

  z-index: -1;
  transform-origin: 50%;
  transform: rotate(90);
}

.artist-pictures::before {
  top: -10%;
  left: 0%;
  background-size: 450px 450px;
  height: 450px;
  width: 450px;
  background-image: url("./images/blob-1.svg");
}

.artist-pictures::after {
  bottom: -10%;
  right: 0%;
  background-size: 350px 350px;
  height: 350px;
  width: 350px;
  background-image: url("./images/blob-2.svg");
}

.artist-picture {
  border-radius: 50%;
  width: 28vw;
  height: 50vw;
  max-width: 350px;
  max-height: 500px;
}
```
{% endcode %}

* Importeer je `page.module.css` in je artist page template file.&#x20;

{% code title="src/pages/artists/{wpArtist.slug}.js" %}
```jsx
import * as React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../../components/layout"
import {
  header,
  headerInfo,
  headerPicture,
  artistName,
  fullName,
  artistRoles,
  artistDescription,
  artistInfo,
  artistPictures,
  artistPicture,
} from "../../page.module.css"

// ArtistPage Component
```
{% endcode %}

* Voeg de CSS classes toe aan je page component zoals hieronder weergegeven:

{% code title="src/pages/artists/{wpArtist.slug}.js" %}
```jsx
// Imports

const ArtistPage = ({
  data: {
    wpArtist: {
      artistMeta: artist,
      roles: { nodes: roles },
    },
  },
}) => {
  const image = getImage(artist.profilePicture.localFile)

  return (
    <Layout pageTitle="Artist Template">
      // Header JSX
      <section className={artistPictures}>
       {picture1 && (
          <GatsbyImage
            className={artistPicture}
            image={picture1}
            alt={artist.picture1.altText}
          />
        )}
        {picture2 && (
          <GatsbyImage
            className={artistPicture}
            image={picture2}
            alt={artist.picture2.altText}
          />
        )}
        {picture3 && (
          <GatsbyImage
            className={artistPicture}
            image={picture3}
            alt={artist.picture3.altText}
          />
        )}
      </section>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

![Artist template page pictures resultaat](<../../.gitbook/assets/image (114) (1).png>)

Super je bent klaar met het stylen van je Artist template page! 🏆Je hebt het einde van dit hoofdstuk bereikt! Je artist template page is volledig gestyled. In het volgende hoofdstuk zal je de About Us page herstructuren en stylen! ✨
