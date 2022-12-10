---
description: >-
  Vooraleer je een page query in je contact page toevoegt, moet je de query
  samenstellen in GraphiQL.
---

# Opbouwen van de Contact query

## Taak: Maak een query aan in GraphiQL voor je Contact page

In je Contact page heb je nog geen query gedefinieerd voor de data van WP op te vragen. Open je GraphiQL in je browser en gebruik de Explorer om je query vorm te geven.

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Probeer eerst zelf de query op te bouwen met behulp van de **Explorer** in je GraphiQL IDE vooraleer je de code hieronder bekijkt.
{% endhint %}

**Je query ziet er uit als volgt:**

```graphql
{
  wpPage(slug: {eq: "contact-us"}) {
    contactUsFields {
      description
      title
      picture {
        id
        altText
        localFile {
          childImageSharp {
            gatsbyImageData
          }
        }
      }
      address
      city
      email
      phoneNumber
      zipCode
      facebook
      instagram
    }
  }
}
```

Voor je `wpPage` query heb je een **query parameter** nodig. Je mag deze hardcoded op `wpPage(slug: {eq: "contact-us"})` zetten.

{% hint style="info" %}
**Let op** 👀**:** Het kan zijn dat je het `childImageSharp`-veld niet ziet staan in de **Explorer** van je GraphiQLIDE en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de **Query Editor**.
{% endhint %}

Werk vervolgens de structuur van je contact pagina component bij zodat het een page query accepteert en doorgeeft aan de `props` (**haal het data object uit je `props`**).

```jsx
import React from "react"
import { graphql } from "gatsby"
import Layout from "../components/layout"

const ContactPage = ({ data }) => {
  return <Layout>Contact Page</Layout>
}

export default ContactPage

export const query = graphql``
```

Kopieer de query onderaan in je `ContactPage` component. Vergeet niet je imports vanboven te definiëren.

```jsx
import React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../components/layout"

const ContactPage = ({ data }) => {
  console.log(data)
  return <Layout>Contact Page</Layout>
}

export default ContactPage

export const query = graphql`
  query {
   wpPage(slug: {eq: "contact-us"}) {
    contactUsFields {
      description
      title
      picture {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData
          }
        }
      }
      address
      city
      email
      phoneNumber
      zipCode
      facebook
      instagram
    }
  }
 }
`
```

`console.log` je `data` object dat je uit je props hebt gedestructereerd en kijk na of alles correct wordt opgehaald in je developer tools!

![](<../../.gitbook/assets/image (34) (1).png>)
