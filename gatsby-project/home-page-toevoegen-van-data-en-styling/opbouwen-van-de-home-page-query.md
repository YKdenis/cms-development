---
description: Bouw je home page query op met behulp van je GraphiQL IDE.
---

# Opbouwen van de Home Page Query

### Taak: Maak een page query aan in GraphiQL voor je home page data op te vragen

Je kan je home page data opvragen door `wpPage` open te klikken in je GraphiQL explorer en vervolgens het `homePage`-veld aan te vinken.

**We zijn alleen geïnteresseerd in het ophalen van de home page en moeten dus een query argument gebruiken.** Je mag het `slug`-argument \(paars veld\) in de Explorer aanvinken. Je mag het `slug`-argument hardcoderen met de waarde **"home"**

Vraag vervolgens alle data op die je hebt gedefinieerd in je WP applicatie voor je home page. 

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Probeer eerst zelf de query op te bouwen met behulp van de **Explorer** in je GraphiQL IDE vooraleer je de code hieronder bekijkt.
{% endhint %}

**Je query ziet er uit als volgt:**

```graphql
query {
wpPage(slug: {eq: "home"}) {
    homePage {
      headerHome {
        description
        title
        picture {
          altText
          localFile {
            childImageSharp {
              gatsbyImageData(placeholder: BLURRED, width: 500, height: 500)
            }
          }
        }
      }
      callToAction {
        description
        link
      }
      featuredArtists {
        artists {
          ... on WpArtist {
            id
            artistMeta {
              artistName
              firstName
              lastName
              profilePicture {
                altText
                localFile {
                  childImageSharp {
                    gatsbyImageData(placeholder: BLURRED, transformOptions: {grayscale: true})
                  }
                }
              }
            }
            slug
          }
        }
        description
        title
      }
    }
  }
}
```

{% hint style="info" %}
**Opmerking 📣:** Aan het `gatsbyImageData`-object kan je parameters meegeven. 

Met de `transformerOptions` kan je de afbeeldingen tijdens build time aanpassen. `{grayscale: true}` zorgt er voor dat je afbeeldingen als zwart/wit worden ingeladen.

Met `width` en `height` kan je de image opvragen in een specifieke grote.

**Meer informatie** 📚**:** [Image opties in Gatsby.](https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-plugin-image#image-options)
{% endhint %}

{% hint style="info" %}
**Let op** 👀**:** Het kan zijn dat je het `childImageSharp`-veld niet ziet staan in de **Explorer** van je GraphiQLIDE en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de **Query Editor**.
{% endhint %}

{% hint style="info" %}
**GraphQL Core-concept** 💡: in je GraphQL query heb je **featuredArtists &gt; artists** en dan een stukje nieuwe syntax: `... on wpArtist`. Deze syntax wordt gebruikt voor het toevoegen van een GraphQL fragment. 

#### Wat is een Fragment?

**Kort uitgelegd is het een stuk voorgeschreven GraphQL code dat men kan hergebruiken in verschillende queries.** Voornamelijk om dubbele code te vermijden. Als je hier meer over wilt weten bekijk dan de [Gatsby documentatie over fragments](https://www.gatsbyjs.com/docs/reference/graphql-data-layer/using-graphql-fragments/)!
{% endhint %}

### Taak: voeg de query toe aan je home page component

Kopieer je query uit GraphiQL en navigeer naar je `src/pages/index.js` in VS code.

* Maak een nieuwe variabele buiten je component aan genaamd `query` en exporteer deze. **Dit is je page query**.
* Plak de GraphiQL query als waarde van je query variabele. **Vergeet niet je graphql-tag toe te voegen!**
* Voeg aan je component je `props` toe en deconstrueer je `data`-object.
* Voeg een `console.log(data)` toe aan je component en check of alle data correct wordt opgevraagd in de developer tools in je browser.

{% code title="src/pages/index.js" %}
```jsx
import * as React from "react"
import Layout from "../components/layout"
import { graphql } from "gatsby"
import { StaticImage } from "gatsby-plugin-image"

const IndexPage = ({ data }) => {
  console.log(data)
  return (
    <main>
      <Layout pageTitle="Welcome to Inghelbrecht Agency!">
        <p>Lorem ipsum</p>
        <StaticImage
          alt="Een Gatsby astronaut"
          src="../images/gatsby-astronaut.png"
        />
      </Layout>
    </main>
  )
}

export const query = graphql`
query {
  wpPage(slug: {eq: "home"}) {
      homePage {
        headerHome {
          description
          title
          picture {
            altText
            localFile {
              childImageSharp {
                gatsbyImageData(placeholder: BLURRED, width: 500, height: 500)
              }
            }
          }
        }
        callToAction {
          description
          link
        }
        featuredArtists {
          artists {
            ... on WpArtist {
              id
              artistMeta {
                artistName
                firstName
                lastName
                profilePicture {
                  altText
                  localFile {
                    childImageSharp {
                      gatsbyImageData(placeholder: BLURRED, transformOptions: {grayscale: true})
                    }
                  }
                }
              }
              slug
            }
          }
          description
          title
        }
      }
    }
  }
`

export default IndexPage

```
{% endcode %}

