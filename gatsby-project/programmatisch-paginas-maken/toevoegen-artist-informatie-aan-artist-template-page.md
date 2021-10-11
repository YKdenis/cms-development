---
description: >-
  Leer hoe je een query variable gebruikt in je Page template om alle data van
  een artiest op te vragen.
---

# Toevoegen artist informatie aan Artist Template Page

## Render artist informatie in de Artist Page Template

Nu je alle pagina's voor je artiesten hebt ingesteld, is het tijd om de daadwerkelijke artist inhoud binnen te halen. **Je hebt geleerd dat je gegevens in je componenten kan trekken met behulp van GraphQL-query's**. Maar hoe kan je Gatsby vertellen welke `wpArtist`-node uit de Data Layer op elke pagina moet worden opgehaald? Om dat te doen, moet je meer te weten komen over een ander **belangrijk GraphQL-concept: query variabelen**.

{% hint style="info" %}
### **Belangrijk GraphQL-concept** ⛓**: query variabelen**

In GraphQL zijn query variabelen een manier om extra gegevens mee te sturen met je request. Met query variabelen kan je dynamische query's schrijven die verschillende gegevens retourneren op basis van de waarden die je doorgeeft.

Laten we een voorbeeld bekijken in GraphiQL. In **Query Data met GraphQL** heb je geleerd over het doorgeven van argumenten aan velden om de data die je terugkrijgt in de response te wijzigen. Je kan bijvoorbeeld de onderstaande query gebruiken om gegevens op te vragen voor de `wpArtist`-node dat een `slug`-veld heeft dat gelijk is aan **"kevin-bismark":**
{% endhint %}

```graphql
query MyQuery {
  wpArtist(slug: {eq: "kevin-bismark"}) {
    artistMeta {
      firstName
      lastName
      email
    }
  }
}
```

{% hint style="info" %}
... wat het volgende antwoord zou opleveren:
{% endhint %}

```graphql
{
  "data": {
    "wpArtist": {
      "artistMeta": {
        "firstName": "Kevin",
        "lastName": "Bismark",
        "email": "kevin@artistagency.com"
      }
    }
  },
  "extensions": {}
}
```

{% hint style="info" %}
In dit geval is je `slug`-waarde hard gecodeerd in je GraphQL-query. Maar wat gebeurt er als je een andere waarde op een andere pagina wilt weergeven? Dat is waar **query variabelen** binnenkomen.

GraphiQL heeft een inklapbare sectie **"Query variabelen"** onder aan het venster **Query-editor**. Als je erop klikt, verschijnt een nieuw tekstgebied, waar je key-value pairs kan toevoegen voor data die je in je zoekopdracht wilt doorgeven. Deze key-value pairs moeten in **JSON** worden geschreven. Als je bijvoorbeeld het onderstaande object aan de sectie Query variabelen toevoegt, krijgt je verzoek een query variabele met de naam `slug` met een waarde van een andere artiest:
{% endhint %}

```graphql
{
    "slug": "kevin-bismark"
}
```

{% hint style="info" %}
### Ga als volgt te werk om de query variabele in je query te gebruiken:

* Definieer je query variabele. Het moet de naam van je variabele bevatten \(met een `$` ervoor\) en het GraphQL-gegevenstype. 
* Gebruik de query variabele in je query. \(Je moet een $ toevoegen voor de naam van de variabele.\) 

Hier zie je bijvoorbeeld hoe je de vorige query zou moeten bijwerken om een query variabele te gebruiken in plaats van een argument:
{% endhint %}

```graphql
query MyQuery($slug: String) {
  wpArtist(slug: {eq: $slug}) {
    artistMeta {
      firstName
      lastName
      email
    }
  }
}
```

{% hint style="info" %}
Het uitvoeren van deze nieuwe query zou hetzelfde antwoord moeten opleveren als de vorige zonder query variabele. Maar nu kan je de waarde van je `slug`-variabele omwisselen met een andere waarde, zoals **"anne-woznak"**, en je response stuurt de juiste node terug.

Het onderstaande diagram laat zien hoe de query, query variabelen en respons allemaal in elkaar passen in de GraphiQL-interface:
{% endhint %}

![GraphiQL Interface met een query variabele](../../.gitbook/assets/image%20%2872%29.png)

{% hint style="info" %}
**Opmerking** 📣**:** In Gatsby kunnen query variabelen alleen binnen page query's worden gebruikt. \(**Je kunt ze niet gebruiken met de useStaticQuery hook**.\)
{% endhint %}

Wanneer je Gatsby's File System Route API gebruikt, voegt het automatisch enkele `props` toe aan de page template component voor elke pagina:

* De `id` voor de Data Layer node wordt gebruikt om de pagina te maken. 
* Het veld dat je hebt gebruikt om het dynamische deel van de route te maken. \(In jou geval het `slug`-veld.\) 

**Onder de motorkap stelt Gatsby beide waarden beschikbaar om te gebruiken als query variabelen in je page query's.**

{% hint style="info" %}
### Query variabele in je page query, hoe werkt dat juist?

Voeg een `console.log` toe om de `props` voor je Artist page component in `src/pages/blog/{wpArtist.slug}.js` af te drukken.
{% endhint %}

{% code title="src/pages/artists/{wpArtist.slug}.js" %}
```jsx
import * as React from 'react'
import Layout from '../../components/layout'

const ArtistPage = (props) => {
  console.log(props)
  return (
    <Layout pageTitle="Artiesten Template">
      <p>De content van je artiesten zal hier worden weergegeven.</p>
    </Layout>
  )
}

export default ArtistPage
```
{% endcode %}

{% hint style="info" %}
Ga in een webbrowser naar [localhost:8000/artists/kevin-bismark](http://localhost:8000/artists/kevin-bismark) en open de developer tools. Op het console-tabblad zou je een object moeten zien dat lijkt op het onderstaande:
{% endhint %}

```javascript
Object {
  // ...
  pageContext: Object { 
    id: "cG9zdDoxMjM="
    slug: "kevin-bismark"
  }
  // ...
}
```

{% hint style="info" %}
De keys in het `pageContext`-object worden toegevoegd wanneer je een pagina maakt met behulp van de File System Route API. **Dit zijn ook de keys die je kan gebruiken als query variabelen in je page query voor de page template voor artiesten.**
{% endhint %}

### 1\) Begin met het gebruik van GraphiQL om een page query te maken voor je Artist page template.

* Aangezien elke pagina slechts data nodig heeft voor een enkele `wpArtist`-node, gebruik je het veld `wpArtist`. 
* De snelste manier om nodes op te zoeken is door het `id`-veld te gebruiken, dus gebruik de `id`-query variabele in plaats van `slug`.

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
    }
  }
}
```

### 2\) Voeg je page query toe aan de page template voor artiesten.

* Vergeet niet de `graphql` tag te importeren! 
* Je moet ook de query name, **MyQuery**, verwijderen of vervangen door een unieke naam.

{% code title="src/pages/artists/{wpArtist.slug}.js" %}
```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import Layout from '../../components/layout'

const ArtistPage = (props) => {
  return (
    <Layout pageTitle="Artiesten Template">
      <p>De content van je artiesten zal hier worden weergegeven.</p>
    </Layout>
  )
}

export const query = graphql`
  query ($id: String) {
    wpArtist(slug: {eq: $id}) {
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
      }
    }
  }
`

export default ArtistPage
```
{% endcode %}

### 3\) Gebruik de data-prop om je artist informatie weer te geven in je page template component.

* Je hebt al geleerd dat Gatsby de resultaten van je page query doorgeeft aan je page component als een `data`-prop. 
* Je kan je Artist component bijwerken om de `data`-prop te gebruiken en de inhoud van je artist weer te geven.

```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import Layout from '../../components/layout'

const ArtistPage = ({data: {wpArtist: {artistMeta: artist}}}) => {
  return (
    <Layout pageTitle="Artiesten Template">
    <div>
      <h3>{artist.artistName}</h3>
      <h1>{artist.firstName} {artist.lastName}</h1>
      <div dangerouslySetInnerHTML={{__html: artist.description}} />
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
  query ($id: String) {
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
      }
    }
  }
`

export default ArtistPage
```

{% hint style="info" %}
**In de functie definitie wordt er destructering toegepast**. De parameter `props` wordt gedestructured tot 3 niveaus diep. Op die manier kan je gemakkelijk artist aanspreken en de data voor je artist weergeven in je component.

Volg [deze link](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring) voor meer informatie omtrent **destructering in Javascript**.
{% endhint %}

### 4\) Ga in je webbrowser naar een van je artist pagina's \(zoals [`localhost:8000/blog/kevin-bismark`](http://localhost:8000/blog/kevin-bismark)\). Je zou de inhoud van je artist op hun eigen pagina moeten zien!

* Probeer de routes voor je andere artiesten te controleren om er zeker van te zijn dat al je pagina's de inhoud van de artiesten correct weergeven.

![](../../.gitbook/assets/image%20%2844%29.png)

