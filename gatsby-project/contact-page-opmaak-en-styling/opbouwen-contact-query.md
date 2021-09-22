---
description: >-
  Vooraleer je een page query in je contact page toevoegt, moet je de query
  samenstellen in GraphiQL.
---

# Opbouwen Contact query

## Taak: Maak een query aan in GraphiQL voor je Contact page

In je Contact page heb je nog geen query gedefinieerd voor de data van WP op te vragen. Open je GraphiQL in je browser en gebruik de Explorer om je query vorm te geven.

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Probeer eerst zelf de query op te bouwen met behulp van de **Explorer** in je GraphiQL IDE vooraleer je de code hieronder bekijkt.
{% endhint %}

**Je query ziet er uit als volgt:**

```graphql
query {
  wpPage(slug: {eq: "contact-us"}) {
    contactPage {
      headerContact {
        description
        title
        picture {
          localFile {
            childImageSharp {
              gatsbyImageData
            }
          }
        }
      }
      companyInformation {
        address
        city
        email
        phoneNumber
        postcode
        socials {
          facebook
          instagram
        }
      }
    }
  }
}
```

Voor je `wpPage` query heb je een **query parameter** nodig. Je mag deze hardcoded op `wpPage(slug: {eq: "contact-us"})` zetten.

{% hint style="info" %}
**Opmerking** 📣: Je hebt de slug '**contact-us**' gedefinieerd in je WP applicatie onder je Contact us page.

De slug van je Contact pagina op je Gatsby website is niet hetzelfde als de slug van je Contact us page op je WP applicatie!
{% endhint %}

{% hint style="info" %}
**Let op** 👀**:** Het kan zijn dat je het `childImageSharp`-veld niet ziet staan in de **Explorer** van je GraphiQLIDE en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de **Query Editor**.
{% endhint %}

Kopieer de query onderaan in je `ContactPage` component en haal het data object uit je `props`. Vergeet niet je je imports vanboven te definiëren.

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
    wpPage(slug: { eq: "contact-us" }) {
      contactPage {
        headerContact {
          description
          title
          picture {
            localFile {
              childImageSharp {
                gatsbyImageData
              }
            }
          }
        }
        companyInformation {
          address
          city
          email
          phoneNumber
          postcode
          socials {
            facebook
            instagram
          }
        }
      }
    }
  }
`
```

`console.log` je data en kijk na of alles correct wordt opgehaald in je developer tools!

![](../../.gitbook/assets/image%20%2834%29.png)

