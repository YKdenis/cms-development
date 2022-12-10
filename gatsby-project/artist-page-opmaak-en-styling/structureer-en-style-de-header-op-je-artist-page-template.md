---
description: >-
  Geef de artist informatie data weer op je website en style deze volgens het
  ontwerp!
---

# Structureer en style de header van je Artist page template

![Eindresultaat Artist Page Template header](<../../.gitbook/assets/image (71).png>)

## Taak: Voeg de JSX structuur toe voor je header op je Artist template page

Voeg de onderstaande JSX toe aan de return waarde van je page component:

<pre class="language-jsx" data-title="src/pages/artists/{wpArtist.slug}.js"><code class="lang-jsx">// imports

<strong>const ArtistPage = ({
</strong>  data: {
    wpArtist: {
      artistMeta: artist,
      roles: { nodes: roles },
    },
  },
}) => {
  const image = getImage(artist.profilePicture.localFile)

  return (
    &#x3C;Layout pageTitle="Artist Template">
      &#x3C;section>
        &#x3C;article>
          {artist.artistName &#x26;&#x26; &#x3C;h3>{artist.artistName}&#x3C;/h3>}
          &#x3C;div>
            {roles.map((role, i) => (
              &#x3C;span key={i}>
                {role.name} {i + 1 &#x3C; roles.length &#x26;&#x26; "- "}
              &#x3C;/span>
            ))}
          &#x3C;/div>
          &#x3C;h1>
            {artist.firstName} {artist.lastName}
          &#x3C;/h1>
          &#x3C;div dangerouslySetInnerHTML={{ __html: artist.description }} />
          &#x3C;p>&#x3C;span>Email:&#x3C;/span> {artist.email}&#x3C;/p>
          &#x3C;p>&#x3C;span>Phone:&#x3C;/span> {artist.phoneNumber}&#x3C;/p>
          &#x3C;p>&#x3C;span>Height:&#x3C;/span> {artist.height}&#x3C;/p>
          &#x3C;p>&#x3C;span>Shirt Size:&#x3C;/span> {artist.shirtSize}&#x3C;/p>
          &#x3C;p>&#x3C;span>Shoe Size:&#x3C;/span> {artist.shoeSize}&#x3C;/p>
          &#x3C;p>&#x3C;span>Origin:&#x3C;/span> {artist.origin}&#x3C;/p>
        &#x3C;/article>
        &#x3C;GatsbyImage image={image} alt={artist.profilePicture.altText} />
      &#x3C;/section>
    &#x3C;/Layout>
  )
}

// Page Query
</code></pre>

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Als je een object of array deconstrueert kan je aan de hand van een '`:`' operator de variabele dat je er uithaalt een andere naam geven.

In de code hierboven heb je dit toegepast op het `nodes` object en heb je het de naam `roles` gegeven!
{% endhint %}

```jsx
// imports
const ArtistPage = ({
  data: {
    wpArtist: {
      artistMeta: artist,
      roles: { nodes: roles },
    },
  },
}) => // Artistpage component
```

{% hint style="info" %}
Pro tip: Aangezien je `artistName` niet required is, kan het zijn dat deze `null` teruggeeft voor een artiest. Je kan hieronder een logical AND (**&&**) gebruiken zoals je hierboven hebt gedaan!

Als `artistName` leeg is dan wordt er niets weergegeven. Als `artistName` is ingevuld dan wordt het `<h3>`-element met de `artistName` weergegeven.

Meer info: [Logical AND operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template\_literals).
{% endhint %}

```jsx
{artist.artistName && <h3>{artist.artistName}</h3>}
```

## Taak: Sprinkle wat CSS op je Artist page template header  ✨

* Navigeer naar je page.module.css en voeg onderstaande CSS classes toe onderaan je file.

{% code title="src/page.module.css" %}
```css
/* Artist page CSS */

.artist-name {
  font-size: 2rem;
  text-transform: uppercase;
  color: #37ba83;
  margin: 0;
}

.artist-roles {
  font-size: 1.3rem;
  text-transform: uppercase;
  margin: 0.5rem 0 1rem 0;
}

.full-name {
  font-size: 3rem;
  text-transform: uppercase;
  margin: 1rem 0 1.5rem 0;
}

.artist-description {
  margin-bottom: 2rem;
}

.artist-info {
  font-weight: 700;
  text-transform: uppercase;
  color: #37ba83;
}
```
{% endcode %}

* Importeer je `page.module.css` in je artist page template file. Je kan verschillende CSS classes hergebruiken dat je in je home page hebt toegepast: `header`, `headerInfo` en `headerPicture`.

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
      <section className={header}>
        <article className={headerInfo}>
          {artist.artistName && (
            <h3 className={artistName}>{artist.artistName}</h3>
          )}
          <div className={artistRoles}>
            {roles.map((role, i) => (
              <span>
                {role.name} {i + 1 < roles.length && "- "}
              </span>
            ))}
          </div>
          <h1 className={fullName}>
            {artist.firstName} {artist.lastName}
          </h1>
          <div
            className={artistDescription}
            dangerouslySetInnerHTML={{ __html: artist.description }}
          />
          <p>
            <span className={artistInfo}>Email:</span> {artist.email}
          </p>
          <p>
            <span className={artistInfo}>Phone:</span> {artist.phoneNumber}
          </p>
          <p>
            <span className={artistInfo}>Height:</span> {artist.height}
          </p>
          <p>
            <span className={artistInfo}>Shirt Size:</span> {artist.shirtSize}
          </p>
          <p>
            <span className={artistInfo}>Shoe Size:</span> {artist.shoeSize}
          </p>
          <p>
            <span className={artistInfo}>Origin:</span> {artist.origin}
          </p>
        </article>
        <GatsbyImage
          className={headerPicture}
          image={image}
          alt={artist.profilePicture.altText}
        />
      </section>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

![Eindresultaat](<../../.gitbook/assets/image (71) (1).png>)

In het volgende onderdeel zal je een nieuwe sectie aanmaken en daaraan de pictures toevoegen!
