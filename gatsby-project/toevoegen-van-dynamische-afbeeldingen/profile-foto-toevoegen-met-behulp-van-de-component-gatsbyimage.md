---
description: >-
  In dit deel van de zelfstudie zal je een profiel foto toevoegen aan je artist
  template bestand.
---

# Profile foto toevoegen met behulp van de component GatsbyImage

## Taak: Profile foto toevoegen met behulp van de component GatsbyImage

Zodra je je GraphQL-query hebt ingesteld, kan je deze toevoegen aan je artist page template, `{wpArtist.slug}.js`.

Vervang je bestaande page query door de query die je in GraphiQL hebt gebouwd en die de `profilePicture` met `localFile` and `childImageSharp` bevat.

{% code title="src/pages/{wpArtist.slug}.js" %}
```jsx
import * as React from "react"
import { graphql } from "gatsby"
import Layout from "../../components/layout"

const ArtistPage = ({
  data: {
    wpArtist: { artistMeta: artist },
  },
}) => {
  return (
    <Layout pageTitle="Artist Template">
      <div>
        <h3>{artist.artistName}</h3>
        <h1>
          {artist.firstName} {artist.lastName}
        </h1>
        <div dangerouslySetInnerHTML={{ __html: artist.description }} />
        <p>Email: {artist.email}</p>
        <p>Phone: {artist.phone}</p>
        <p>Height: {artist.height}</p>
        <p>Shirt Size: {artist.shirtSize}</p>
        <p>Shoe Size: {artist.shoeSize}</p>
        <p>Origin: {artist.origin}</p>
      </div>
    </Layout>
  )
}

export const query = graphql`
  query MyQuery($id: String) {
    wpArtist(id: { eq: $id }) {
      artistMeta {
        firstName
        lastName
        email
        description
        artistName
        height
        origin
        phoneNumber
        shirtSize
        shoeSize
        profilePicture {
          localFile {
            childImageSharp {
              gatsbyImageData(placeholder: BLURRED)
            }
          }
          altText
        }
      }
    }
  }
`

export default ArtistPage
```
{% endcode %}

Importeer de `GatsbyImage`-component en de `getImage`-helperfunctie uit de `gatsby-plugin-image`-package.

{% code title="src/pages/{wpArtist.slug}.js" %}
```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import { GatsbyImage, getImage } from 'gatsby-plugin-image' 
import Layout from '../../components/layout'

// ...
```
{% endcode %}

Gebruik de `getImage`-helperfunctie om het `gatsbyImageData`-object op te halen uit het `profileImage.localFile`-veld.

{% code title="src/pages/{wpArtist.slug}.js" %}
```jsx
// imports

const ArtistPage = (
  data: {
    wpArtist: { artistMeta: artist },
  }
}) => {
  const image = getImage(artist.profilePicture.localFile)

  return (
    // ...
  )
}

// ...
```
{% endcode %}

{% hint style="info" %}
**Opmerking** 📣: `getImage` is een hulpfunctie die een `File`-node of een `ImageSharp`-node opneemt en het `gatsbyImageData`-object voor die node retourneert. Je kan het gebruiken om je code een beetje properder en leesbaar te houden.

Zonder de `getImage`-helperfunctie zou je `artist.profilePicture.localFile.childImageSharp.gatsbyImageData` moeten typen \(wat langer is, maar je dezelfde gegevens teruggeeft\).
{% endhint %}

Gebruik de component `GatsbyImage` van `gatsby-plugin-image` om de `profilePicture` gegevens weer te geven. Je moet aan `GatsbyImage` twee props doorgeven:

* **image**: het `gatsbyImageData`-object voor van je artiest zijn/haar profile foto.
* **alt**: de alternatieve tekst voor je afbeelding, uit het veld `altText` onder profilePicture.

{% code title="src/pages/{wpArtist.slug}.js" %}
```jsx
import * as React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../../components/layout"

const ArtistPage = ({
  data: {
    wpArtist: { artistMeta: artist },
  },
}) => {
  const image = getImage(artist.profilePicture.localFile)

  return (
    <Layout pageTitle="Artist Template">
      <div>
        <GatsbyImage image={image} alt={artist.profilePicture.altText} />
        <h3>{artist.artistName}</h3>
        <h1>
          {artist.firstName} {artist.lastName}
        </h1>
        <div dangerouslySetInnerHTML={{ __html: artist.description }} />
        <p>Email: {artist.email}</p>
        <p>Phone: {artist.phone}</p>
        <p>Height: {artist.height}</p>
        <p>Shirt Size: {artist.shirtSize}</p>
        <p>Shoe Size: {artist.shoeSize}</p>
        <p>Origin: {artist.origin}</p>
      </div>
    </Layout>
  )
}

export const query = graphql`
  query MyQuery($id: String) {
    wpArtist(id: { eq: $id }) {
      artistMeta {
        firstName
        lastName
        email
        description
        artistName
        height
        origin
        phoneNumber
        shirtSize
        shoeSize
        profilePicture {
          localFile {
            childImageSharp {
              gatsbyImageData(placeholder: BLURRED)
            }
          }
          altText
        }
      }
    }
  }
`

export default ArtistPage
```
{% endcode %}

Wanneer je nu elk van je artist pagina's bezoekt, zou je de bijbehorende profile foto boven de naam van je artist moeten zien!

![Kevin Bismark - /artists/kevin-bismark](../../.gitbook/assets/image%20%28124%29.png)

![Anne Woznak - /artists/anne-woznak](../../.gitbook/assets/image%20%28155%29.png)

