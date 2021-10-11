---
description: Creëer dynamisch nieuwe routes met Gatsby's File System Route API
---

# Wat is de Gatsby's File System Route API?

Wanneer je je Gatsby-site bouwt, maakt Gatsby een nieuwe route voor elke page component in je `src/pages`-directory. Tot nu toe heb je maar **één pagina per bestand gemaakt**: het bestand `index.js` maakt de home page, het bestand `about.js` maakt de about page en het bestand `artists.js` maakt de pagina Artists aan.

Maar je kan ook **één page component gebruiken om meerdere pagina's te maken**. In plaats van alle inhoud hard te coderen, maak je een template om de basisstructuur van je pagina te schetsen, en vervolgens kan Gatsby dynamisch de specifieke gegevens voor elke pagina toevoegen tijdens het bouwen. Om dat te doen, gebruik je **Gatsby's File System Route API**, hiermee kan je **dynamisch routes maken door je paginabestanden een speciale syntax te geven**.

{% hint style="info" %}
## Key Gatsby-concept 💡: File System Route API

[Gatsby's File System Route API ](https://www.gatsbyjs.com/docs/reference/routing/file-system-route-api/)definieert **een speciale syntax** voor het benoemen van de bestanden in je `src/pages`-directory, waarmee je **dynamisch nieuwe pagina's voor je site kan maken op basis van een verzameling nodes in de GraphQL Data Layer**.

Stel je bijvoorbeeld voor dat je site een aantal product nodes in de Data Layer had. **Je kan de File System Route API gebruiken om één product pagina template bestand te maken.** Wanneer je je website bouwt zal Gatsby die pagina template combineren met de gegevens voor elke product node en een nieuwe pagina genereren voor elk product. En als je besluit dat je wijzigingen aan je product pagina moet aanbrengen, hoef je alleen het template component te bewerken en zal Gatsby al je product pagina's automatisch bijwerken de volgende keer dat de site opnieuw wordt opgebouwd.

## Een collection route maken:

Bepaal van welk type node je pagina's wilt maken. Kies welk veld op die node je wilt gebruiken in de route (de URL) voor je pagina's. Maak een nieuwe page component in je `src/pages`-directory met behulp van de volgende **naamgevingsconventie**: `{nodeType.field}.js`. **Vergeet niet de accolades** (`{}`) in je bestandsnaam op te nemen om het dynamische deel van de route aan te geven!

Als je bijvoorbeeld een aparte pagina voor elke product node wilt maken en je wilt de naam van het product in de URL gebruiken, dan maak je een nieuw bestand aan op `src/pages/{Product.name}.js`. Dan zou Gatsby die pagina's maken op routes zoals `/bottle` of `/sweatshirt` of `/notebook`.
{% endhint %}

In dit deel zal je **Gatsby's File System Route API** gebruiken om dynamisch nieuwe pagina's te maken voor elk van je artiesten.

Volgens de API moet je over twee dingen beslissen voordat je een **collection route** maakt:

* Welk type node je wilt gebruiken om pagina's van te maken. 
* Welk veld van die node je wilt gebruiken voor in de URL. 

Omdat je artiesten via WordPress zijn binnengehaald, gebruik je de `wpArtist`-node type om pagina's van te maken. Maar welk veld op de `wpArtist`-node kan je best gebruiken?

`gatsby-source-wordpress` voegt automatisch een `slug`-veld toe aan elke `wpArtist`-node. Deze slug zou normaal gezien de `firstName` en `lastName` moeten retourneren zoals hieronder weergegeven. Je kan de waarde van het `slug`-veld voor elk `wpArtist`-node in GraphiQL zien. Als je de volgende query uitvoert:

```graphql
query MyQuery {
  allWpArtist {
    edges {
      node {
        slug
      }
    }
  }
}
```

... je zou ongeveer volgend resultaat moeten krijgen:

```yaml
{
  "data": {
    "allWpArtist": {
      "edges": [
        {
          "node": {
            "slug": "kevin-bismark"
          }
        },
        {
          "node": {
            "slug": "joel-mott"
          }
        },
        {
          "node": {
            "slug": "rayan-miller"
          }
        },
        {
          "node": {
            "slug": "anne-woznak"
          }
        }
      ]
    }
  },
  "extensions": {}
}
```

Dat ziet eruit als een goed formaat voor een URL!

{% hint style="info" %}
**Opmerking** 📣: in dit geval is het slug-veld een goede keuze omdat het leesbaar is voor mensen, wat betekent dat de URL's voor je artiesten gemakkelijker te begrijpen zijn voor gebruikers. **Maar je kan elk veld in je routes gebruiken**, zelfs als het speciale tekens of witruimte bevat, omdat Gatsby elke route zal ["slugifyen"](https://www.gatsbyjs.com/docs/reference/routing/file-system-route-api/). `I ♥ Paris` wordt bijvoorbeeld omgezet in `i-love-paris`.
{% endhint %}
