---
description: Bouw je artists page query op met behulp van je GraphiQL IDE.
---

# Opbouwen van de Artists Page Query

## Taak: Maak een page query aan in GraphiQL voor je artists page data op te vragen

Je kan je artists page data opvragen door `wpPage` open te klikken in je GraphiQL explorer en vervolgens het `artistsPage`-veld aan te vinken.

Vink het `slug`-argument (paars veld) in de Explorer aan. Je mag het `slug`-argument hard coderen met de waarde **"artists"**.

![](<../../.gitbook/assets/image (78).png>)

Vraag vervolgens alle data op die je hebt gedefinieerd in je WP applicatie voor je artists page.

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Probeer eerst zelf de query op te bouwen met behulp van de **Explorer** in je GraphiQL IDE vooraleer je de code hieronder bekijkt.
{% endhint %}

**Je query ziet er uit als volgt:**

```graphql
wpPage(slug: {eq: "artists"}) {
    artistsPage {
      headerArtists {
        description
        title
        picture {
          localFile {
            childImageSharp {
              gatsbyImageData(quality: 100, placeholder: BLURRED, layout: FULL_WIDTH)
            }
          }
          altText
        }
      }
    }
  }
```

{% hint style="info" %}
**Let op** 👀**:** Het kan zijn dat je het `childImageSharp`-veld niet ziet staan in de **Explorer** van je GraphiQLIDE en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de **Query Editor**.
{% endhint %}

{% hint style="info" %}
De **layout parameter** in je `gatsbyImageData` bepaalt de afbeeldingsformaten die worden gegenereerd, evenals het gedrag van de afbeelding zelf in de browser.

Gebruik `FULL_WIDTH`voor afbeeldingen die altijd over de volledige breedte van het scherm worden weergegeven, zoals banners of hero images.

**Meer informatie omtrent de**[ **layout parameter** 📚](https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-plugin-image/#layout)
{% endhint %}

## Taak: Vraag al je artiesten op via een query

Op je artists page wil je natuurlijk alle artiesten weergeven en er voor zorgen dat bezoekers er op kunnen doorklikken. Momenteel heb je deze al via `allWpArtists` opgehaald. Laten we de query verder uitbreiden.

Navigeer naar je GraphiQL IDE en vink het `allWpArtists`-veld aan in je Explorer. Vraag vervolgens de `firstName`, `lastName`, `artistName`, `profilePicture`, `id` en de `slug` op.

```graphql
  allWpArtist {
    edges {
      node {
        artistMeta {
          artistName
          firstName
          lastName
          profilePicture {
            localFile {
              childImageSharp {
                gatsbyImageData(placeholder: BLURRED, transformOptions: {grayscale: true})
              }
            }
            altText
          }
        }
        slug
        id
      }
    }
  }
```

## Taak: voeg de queries toe aan je artists page component

Kopieer je queries uit GraphiQL en navigeer naar je `src/pages/artists/index.js` in VS code.

* Maak een nieuwe variabele buiten je component aan genaamd `query` en exporteer deze. **Dit is je page query**.
* Plak de GraphiQL query als waarde van je query variabele. **Vergeet niet je graphql-tag toe te voegen!**
* Voeg aan je component je `props` toe en deconstrueer je `data`-object.
* Voeg een `console.log(artistsPage, artistsInfo)` toe aan je component en check of alle data correct wordt opgevraagd in de developer tools in je browser.

{% code title="src/pages/artists/index.js" %}
```jsx
import * as React from "react"
import { Link, graphql } from "gatsby"
import Layout from "../../components/layout"

const ArtistsPage = ({
  data: {
    allWpArtist: { edges: artistsInfo },
    wpPage: { artistsPage },
  },
}) => {
  console.log(artistsPage, artistsInfo)
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      {artistsInfo.map(item => {
        const artist = item.node.artistMeta
        const slug = item.node.slug
        return (
          <Link key={item.node.id} to={`/artists/${slug}`}>
            <p>
              {artist.firstName} {artist.lastName}
            </p>
          </Link>
        )
      })}
    </Layout>
  )
}

export const query = graphql`
  query {
    wpPage(slug: { eq: "artists" }) {
      artistsPage {
        headerArtists {
          description
          title
          picture {
            localFile {
              childImageSharp {
                gatsbyImageData(quality: 100, placeholder: BLURRED, layout: FULL_WIDTH)
              }
            }
          }
        }
      }
    }
    allWpArtist {
      edges {
        node {
          artistMeta {
            artistName
            firstName
            lastName
            profilePicture {
              localFile {
                childImageSharp {
                  gatsbyImageData(
                    placeholder: BLURRED
                    transformOptions: { grayscale: true }
                  )
                }
              }
            }
          }
          slug
          id
        }
      }
    }
  }
`

export default ArtistsPage
```
{% endcode %}
