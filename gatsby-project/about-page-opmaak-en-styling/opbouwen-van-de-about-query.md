---
description: >-
  In je about page heb je nog geen page query gedefinieerd. Begin met het
  definiëren van een query om al je data op te halen.
---

# Opbouwen van de About query

## Taak: Maak een query aan in GraphiQL voor je About page

In je About page heb je nog geen query gedefinieerd voor de data van WP op te vragen. Open je GraphiQL in je browser en gebruik de Explorer om je query vorm te geven.

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Probeer eerst zelf de query op te bouwen met behulp van de **Explorer** in je GraphiQL IDE vooraleer je de code hieronder bekijkt.
{% endhint %}

**Je query ziet er uit als volgt:**

```graphql
query {
  wpPage(slug: {eq: "about-us"}) {
    aboutUsFields {
      goalDescription
      goalTitle
      goalPicture {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
      missionTitle
      missionDescription
      missionPicture {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
    }
  }
}
```

Voor je `wpPage` query heb je een **query parameter** nodig. Je mag deze hardcoded op `wpPage(slug: {eq: "about-us"})` zetten.

{% hint style="info" %}
**Let op** 👀**:** Het kan zijn dat je het `childImageSharp`-veld niet ziet staan in de **Explorer** van je GraphiQLIDE en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de **Query Editor**.
{% endhint %}

Kopieer de query onderaan in je `AboutPage` component en haal het data object uit je `props`. Vergeet niet je `graphql` tag te importeren van de Gatsby library.

```jsx
import * as React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../components/layout"

const AboutPage = ({ data }) => {
  console.log(data)
  return (
    <Layout pageTitle="About Us">
      <p>
        Artist Agency was founded in 1977 by founder, John Doe. AA continues to
        be at the forefront of art by establishing the careers of our talents on
        a holistic level -- and setting trends within the industry.{" "}
      </p>
    </Layout>
  )
}

export default AboutPage

export const query = graphql`
  query {
  wpPage(slug: {eq: "about-us"}) {
    aboutUsFields {
      goalDescription
      goalTitle
      goalPicture {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
      missionTitle
      missionDescription
      missionPicture {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
    }
  }
}
`
```

`console.log` je data en kijk na of alles correct wordt opgehaald in je developer tools!

![Developer tools console.log](<../../.gitbook/assets/image (43).png>)
