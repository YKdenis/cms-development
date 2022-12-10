---
description: Bouw je artist template page query op met behulp van je GraphiQL IDE.
---

# Opbouwen van de Artist query

## Taak: Maak een query aan in GraphiQL voor je artist template page

In je template page heb je al een query gedefinieerd voor één specifieke artist op te vragen met behulp van `wpArtist`. Kopieer deze query terug in je GraphiQL IDE zodat je het verder kan aanpassen.

```graphql
query ($slug: String) {
    wpArtist(slug: { eq: $slug }) {
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
```

Voor je `wpArtist` query heb je een **query variabele** nodig. Definieer een `object` in het **Query Variables** venster rechtsonder in je GraphiQL IDE en geef het een key `id` met als waarde de id van een van je artiesten mee.

```graphql
{
  "slug": "anna-woznak"
}
```

Voor je artist moet je nog de `pictures` en de `roles` opvragen. Gebruik de GraphiQL Explorer en bouw je query verder op.

{% hint style="info" %}
**Pro tip 🧙‍♂️:** Probeer eerst zelf de query op te bouwen met behulp van de **Explorer** in je GraphiQL IDE vooraleer je de code hieronder bekijkt.
{% endhint %}

**Je query ziet er uit als volgt:**

```graphql
query ($slug: String) {
  wpArtist(slug: {eq: $slug}) {
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
      picture1 {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
      picture2 {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
      picture3 {
        altText
        localFile {
          childImageSharp {
            gatsbyImageData(placeholder: BLURRED)
          }
        }
      }
    }
    roles {
      nodes {
        name
      }
    }
  }
}

```

{% hint style="info" %}
**Let op** 👀**:** Het kan zijn dat je het `childImageSharp`-veld niet ziet staan in de **Explorer** van je GraphiQLIDE en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de **Query Editor**.
{% endhint %}
