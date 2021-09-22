---
description: >-
  Met alle benodigde tools op hun plaats, ben je klaar om de artist profile foto
  toe te voegen aan artist page template.
---

# GraphQL-query's maken die afbeeldingen uit WordPress ophalen

## Voeg de profile foto toe aan je page query in je artist page template.

Elk GraphQL `File`-object dat een afbeelding bevat, heeft een `childImageSharp`-veld dat je kan gebruiken om de afbeeldingsgegevens op te vragen. De exacte gegevensstructuur is afhankelijk van je gegevensbron, maar de syntax voor `gatsby-source-wordpress` is als volgt:

```graphql
query MyQuery($id: String) {
  wpArtist(id: {eq: $id}) {
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

We vragen ook de `altText` van onze profile foto op die we gedefinieerd hebben in WordPress.

{% hint style="info" %}
**Opmerking 📣:** Het kan zijn dat je `childImageSharp` niet zal zien staan in de Explorer van GraphiQL en dat je GraphiQL het zal onderstrepen met een rode lijn wanneer je het toevoegt in de Query Editor.

Dit wilt zeggen dat je `gatsby-transformer-sharp` niet correct is in gesteld.

Als het zich blijft voordoen, herstart je ontwikkelingsserver en gebruik de commando `gatsby clean`.
{% endhint %}

{% hint style="info" %}
`placeholder: BLURRED`: Dit genereert een versie met een zeer lage resolutie van de bronafbeelding en geeft deze weer als een onscherpe achtergrond.

Wanneer je foto nog niet helemaal is ingeladen wordt de onscherpe afbeelding getoond als placeholder. Hierdoor zal je site niet verspringen en behoudt het zijn layout. **Wanneer de afbeelding klaar is met laden wordt de onscherpe afbeelding vervangen door de hoge resolutie afbeelding.**
{% endhint %}

Je response ziet er als volgt uit:

```graphql
{
  "data": {
    "wpArtist": {
      "artistMeta": {
        "firstName": "Kevin",
        "lastName": "Bismark",
        "email": "kevin@artistagency.com",
        "description": "<p>Bismark was born in San Luis Obispo, California, and later moved to Arroyo Grande, California. His father, David Bismark, is an electrical engineer at Diablo Canyon Power Plant, and his mother, Starla Baskett, is an administrative assistant who also works at Diablo Canyon. Efron has a brother, Dylan, and had, as he has described, a \"normal childhood\" in a middle-class family. His surname originates from Hebrew. His paternal grandfather is Jewish, and Bismark has described himself as Jewish though he was raised agnostically and did not practice religion as a child.</p>\n",
        "artistName": "John Doe",
        "height": 183,
        "origin": "American",
        "phoneNumber": "0123456789",
        "shirtSize": "M",
        "shoeSize": 42.5,
        "profilePicture": {
          "localFile": {
            "childImageSharp": {
              "gatsbyImageData": {
                "layout": "constrained",
                "placeholder": {
                  "fallback": "data:image/jpeg;base64,/9j/2wBDABALDA4MChAODQ4SERATGCgaGBYWGDEjJR0oOjM9PDkzODdASFxOQERXRTc4UG1RV19iZ2hnPk1xeXBkeFxlZ2P/2wBDARESEhgVGC8aGi9jQjhCY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2NjY2P/wgARCAAUABQDASIAAhEBAxEB/8QAGAABAQEBAQAAAAAAAAAAAAAAAAQDAQL/xAAVAQEBAAAAAAAAAAAAAAAAAAAAAf/aAAwDAQACEAMQAAABpwtlKXsZ5kcC/wD/xAAdEAABBAIDAAAAAAAAAAAAAAABAAIDEgQQESEi/9oACAEBAAEFAnOqopLMR7GMOItDwLFf/8QAFBEBAAAAAAAAAAAAAAAAAAAAIP/aAAgBAwEBPwEf/8QAFBEBAAAAAAAAAAAAAAAAAAAAIP/aAAgBAgEBPwEf/8QAGhAAAgIDAAAAAAAAAAAAAAAAARAAMRFxgf/aAAgBAQAGPwKiZR2+vAX/xAAeEAACAQMFAAAAAAAAAAAAAAAAASERMVEQQXGRof/aAAgBAQABPyGkchKyQ5TePcUJKyjuBGiYC/pxH//aAAwDAQACAAMAAAAQ7Nh8/8QAFhEAAwAAAAAAAAAAAAAAAAAAABAR/9oACAEDAQE/ECP/xAAWEQEBAQAAAAAAAAAAAAAAAAARABD/2gAIAQIBAT8QZ3//xAAeEAEAAQQCAwAAAAAAAAAAAAABABEhMWFBkcHh8P/aAAgBAQABPxA6NAfKcEVMBbFzumOoOmYOTEOyFR+LQggJzm7ftNUf/9k="
                },
                "images": {
                  "fallback": {
                    "src": "/static/9a7fc845b17bb8877ac4abd348a50c64/30f07/kevin-bismark-profile.jpg",
                    "srcSet": "/static/9a7fc845b17bb8877ac4abd348a50c64/41624/kevin-bismark-profile.jpg 160w,\n/static/9a7fc845b17bb8877ac4abd348a50c64/1b894/kevin-bismark-profile.jpg 320w,\n/static/9a7fc845b17bb8877ac4abd348a50c64/30f07/kevin-bismark-profile.jpg 640w",
                    "sizes": "(min-width: 640px) 640px, 100vw"
                  },
                  "sources": [
                    {
                      "srcSet": "/static/9a7fc845b17bb8877ac4abd348a50c64/60b4d/kevin-bismark-profile.webp 160w,\n/static/9a7fc845b17bb8877ac4abd348a50c64/5e011/kevin-bismark-profile.webp 320w,\n/static/9a7fc845b17bb8877ac4abd348a50c64/90d07/kevin-bismark-profile.webp 640w",
                      "type": "image/webp",
                      "sizes": "(min-width: 640px) 640px, 100vw"
                    }
                  ]
                },
                "width": 640,
                "height": 640
              }
            }
          },
          "altText": "kevin-bismark-profile"
        }
      }
    }
  },
  "extensions": {}
}
```

Als je het `gatsbyImageData`-object in het veld `profilePicture.localFile.childImageSharp` nader bekijkt, zul je zien dat het een heleboel informatie bevat over de profile foto voor die artiest: **afmetingen, bestandspaden voor de afbeeldingen in verschillende formaten, fallback-afbeeldingen naar gebruiken als placeholder terwijl de afbeelding wordt geladen.** Al deze gegevens worden tijdens het bouwen door `gatsby-plugin-sharp` verwerkt. Het `gatsbyImageData`-object in je antwoord heeft dezelfde structuur die de `GatsbyImage`-component nodig heeft om een afbeelding weer te geven.

{% hint style="info" %}
**Opmerking** 📣: je hebt misschien gemerkt dat het `gatsbyImageData`-veld in GraphiQL verschillende argumenten accepteert, zoals `aspectRatio`, `formats` of `width`. Je kan deze argumenten gebruiken om extra gegevens door te geven over hoe je wilt dat `gatsby-image-sharp` je geoptimaliseerde afbeeldingen bouwt.

Deze opties zijn gelijk aan degene die je zou doorgeven aan de `StaticImage`-component als `props`.

Voor meer informatie, zie de [gatsby-plugin-image Documentatie](https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-plugin-image/#image-options).
{% endhint %}

