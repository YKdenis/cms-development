---
description: >-
  Geef je Featured Artists data weer op je website en style deze volgens het
  design voorbeeld!
---

# Structureer en style de Featured Artists JSX

![Featured artists sectie](<../../.gitbook/assets/image (145).png>)

### Taak: Giet je featured artists data in een JSX structuur

Je featured artists data bestaat uit een `title`, `description` en een array van artiesten genaamd `artists`. Itereer over je artiesten array met behulp van een `map`-functie. Voor elke artiest zal je een Gatsby `Link` component moeten terugsturen dat een link legt met de `{wpArtist.slug}.js` page template.

{% code title="src/pages/index.js" %}
```jsx
// IndexPage

<Layout>

// Home Page Header JSX
  
  <div>
    <h2>{homePage.featuredArtists.title}</h2>
    <p>{homePage.featuredArtists.description}</p>
    <div>
      {homePage.featuredArtists.artists.map(artist => {
        const profile = getImage(artist.artistMeta.profilePicture.localFile)
  
        return (
          <Link to={`artists/${artist.slug}`}>
            <GatsbyImage
              image={profile}
              alt={artist.artistMeta.profilePicture.altText}
            />
            <div>
              {artist.artistMeta.artistName && (
                <p>{artist.artistMeta.artistName}</p>
              )}
              <p>
                {artist.artistMeta.firstName} {artist.artistMeta.lastName}
              </p>
            </div>
          </Link>
          )
      })}
    </div>
  </div>
</Layout>

// Page Query
```
{% endcode %}

Het `Link`-component dat je hierboven hebt gedefinieerd zal je hergebruiken op de Artists page. In plaats van het te kopiëren, en zo dubbele code te hebben, kan je van het `Link`-component een **Building Block component** maken.

#### Maak een nieuwe file aan in je `src/components` map genaamd `artist.js`. 

* Definieer een nieuw component met de naam `Artist` en plak de code binnen je `map`-functie in je featured artists sectie in het component.
* Vergeet niet je `Link`-component, `GatsbyImage` en `getImage` te importeren!
* Deconstrueer de `props` in je functiedefinitie en haal er de variabele `artist` en `slug` uit.

{% code title="src/components/artist.js" %}
```jsx
import React from "react"
import { Link } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"

export const Artist = ({ artist, slug }) => {
  const profile = getImage(artist.artistMeta.profilePicture.localFile)
  return (
    <Link to={slug}>
      <GatsbyImage
        image={profile}
        alt={artist.artistMeta.profilePicture.altText}
      />
      <div>
        {artist.artistMeta.artistName && <p>{artist.artistMeta.artistName}</p>}
        <p>
          {artist.artistMeta.firstName} {artist.artistMeta.lastName}
        </p>
      </div>
    </Link>
  )
}

export default Artist;
```
{% endcode %}

**Je Artist component kan nu worden herbruikt!** Importeer Artist in je home page en vervang het `Link`-component met `<Artist key={artist.id} slug={slug} artist={artist} />`.

{% code title="src/pages/index.js" %}
```jsx
// IndexPage

<Layout>

// Home Page Header JSX
  
  <div>
    <h2>{homePage.featuredArtists.title}</h2>
    <p>{homePage.featuredArtists.description}</p>
    <div>
      {homePage.featuredArtists.artists.map(artist => (
            <Artist slug={`artists/${slug}`} key={artist.id} artist={artist} />
          ))}
    </div>
  </div>
</Layout>

// Page Query
```
{% endcode %}

### Taak: Sprinkle wat CSS op je Artist JSX  ✨

De CSS voor de Featured Artists zal worden opgesplitst in twee bestanden. `src/components/artist.module.css` en `src/page.module.css`. Aangezien je `Artist.js`-bestand een Building Block component is kunnen we hiervoor een apart CSS-bestand voor voorzien. 

* Begin met het maken van een nieuw CSS-bestand in je `src/components` genaamd `artist.module.css`.
* Voeg volgende CSS classes toe aan `artist.module.css`.

{% code title="src/components/artist.module.css" %}
```css
.wrapper {
  display: block;
  position: relative;
  width: 28vw;
  height: 28vw;
  max-width: 350px;
  max-height: 350px;
  margin: auto;
  margin-top: 10px;
  overflow: hidden;
}

.image {
  width: 100%;
  height: 100%;
}

.artist-info {
  display: block;
  position: absolute;
  bottom: -50px;
  left: 0;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  color: white;
  text-align: center;
  padding: 1rem 0;
  opacity: 0;
  transition: all 0.5s ease;
}

.wrapper:hover .artist-info {
  bottom: 0;
  opacity: 1;
}

.artist-name {
  margin: 0;
  color: #37ba83;
}

.full-name {
  text-transform: uppercase;
  font-weight: 700;
  margin: 0;
}
```
{% endcode %}

* Importeer de CSS classes in je `src/components/artist.js`.

{% code title="src/components/artist.js" %}
```jsx
import React from "react"
import { Link } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import {
  wrapper,
  image,
  artistInfo,
  artistName,
  fullName,
} from "./artist.module.css"

// Artist Component
```
{% endcode %}

* Voeg de CSS classes toe aan je componenten zoals hieronder weergegeven:

{% code title="src/components/artist.js" %}
```jsx
// Imports

export const Artist = ({ artist, slug }) => {
  const profile = getImage(artist.artistMeta.profilePicture.localFile)
  return (
    <Link
      className={wrapper}
      to={slug}
    >
      <GatsbyImage
        className={image}
        image={profile}
        alt={artist.artistMeta.profilePicture.altText}
      />
      <div className={artistInfo}>
        {artist.artistMeta.artistName && (
          <p className={artistName}>{artist.artistMeta.artistName}</p>
        )}
        <p className={fullName}>
          {artist.artistMeta.firstName} {artist.artistMeta.lastName}
        </p>
      </div>
    </Link>
  )
}

export default Artist
```
{% endcode %}

### Taak: Style je featured artists sectie  ✨

Vooraleer je begint met het stylen van je featured artists sectie moet je twee SVG-bestanden downloaden en toevoegen aan je `src/images` map.

{% file src="../../.gitbook/assets/blob-1.svg" %}
Green Blob 1
{% endfile %}

{% file src="../../.gitbook/assets/blob-2.svg" %}
Green Blob 2
{% endfile %}

Deze twee blobs zal je gebruiken in je CSS voor de groene achtergrond te creëren in je featured artists sectie.

* Navigeer terug naar je `src/page.module.css` en voeg volgende CSS classes toe:

{% code title="src/page.module.css" %}
```css
// Home Page header CSS

.subtitle {
  font-size: 4rem;
  line-height: 3rem;
  letter-spacing: -0.2rem;
  text-transform: uppercase;
  margin: 0;
  margin-bottom: 30px;
}

.section {
  position: relative;
  margin-top: 180px;
  text-align: center;
}

.section::before,
.section::after {
  position: absolute;
  display: inline-flex;
  content: "";
  background-size: 700px 700px;
  height: 700px;
  width: 700px;
  z-index: -1;
}

.section::before {
  top: 40%;
  left: -40%;
  background-image: url("./images/blob-1.svg");
}

.section::after {
  top: 0;
  right: -40%;
  background-image: url("./images/blob-2.svg");
}

.artists {
  display: flex;
  justify-content: space-between;
  margin-top: 90px;
  flex-wrap: wrap;
}

```
{% endcode %}

* Importeer de CSS classes in je `src/pages/index.js`.

{% code title="src/pages/index.js" %}
```jsx
import * as React from "react"
import Layout from "../components/layout"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Artist from "../components/artist"
import {
  header,
  headerInfo,
  headerPicture,
  headerTitle,
  CTA,
  section,
  subtitle,
  artists,
} from "../page.module.css"
```
{% endcode %}

* Voeg de CSS classes toe aan je componenten zoals hieronder weergegeven:

{% code title="src/pages/index.js" %}
```jsx
// Index Page

<Layout>

  // Home Page Header JSX
  
  <div className={section}>
    <h2 className={subtitle}>{homePage.featuredArtists.title}</h2>
    <p>{homePage.featuredArtists.description}</p>
    <div className={artists}>
      {homePage.featuredArtists.artists.map(artist => (
           <Artist
              slug={`artists/${artist.slug}`}
              key={artist.id}
              artist={artist}
            />
      ))}
    </div>
  </div>
</Layout>

// Page Query
```
{% endcode %}

* Navigeer naar [localhost:8000](http://localhost:8000) in je browser.

![Featured artists sectie](<../../.gitbook/assets/image (145).png>)

Voila, je featured artists sectie is af! 🥳 In het volgende deel zal je het laatste deel van je home page bouwen namelijk de `Footer`. **Dit zal net zoals je **`Artist`** component een Building block component zijn aangezien het op elke pagina zal worden herbruikt**!
