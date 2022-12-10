---
description: >-
  Maak een collection route voor je artiesten aanmet behulp van de File Sytem
  Routes API.
---

# Artist Page Template aanmaken

## Taak: Pagina template voor artiesten maken

Nu je weet welk node-type en veld je moet gebruiken, kan je ze aan een sluiten met behulp van de naamgevingsconventie voor [File System Routes](https://www.gatsbyjs.com/docs/reference/routing/file-system-route-api/). Om nieuwe pagina's te maken van het `slug`-veld van je `wpArtist`-node, moet je een nieuw bestand maken op `src/pages/{wpArtist.slug}.js`.

{% hint style="info" %}
**Opmerking** 📣: Gatsby zal voor elke `wpArtist`-node in de GraphQL Data Layer een nieuwe pagina aanmaken. De slug zal worden gebruikt als route. M.a.w. als je slug "**kevin-bismark**" is dan zal je voor die artiest naar de route `/kevin-bismark` kunnen navigeren. De pagina die wordt weergegeven is de template page `src/pages/{wpArtist.slug}.js` waarin dynamisch de data van Kevin Bismark wordt ingevuld!
{% endhint %}

Maak een nieuw bestand in je `src/pages`-map met de naam `{wpArtist.slug}.js`. **Dit wordt het bestand voor je Artist Page Template**.

Maak een simpele page component in je nieuwe `{wpArtist.slug}.js`-bestand. Voeg voorlopig het `Layout` component toe, en hardcode de `pageTitle` en de inhoud van je component. (Je zult die later dynamisch maken.)

{% code title="src/pages/{wpArtist.slug}.js" %}
```jsx
import * as React from 'react'
import Layout from '../components/layout'

const ArtistPage = () => {
  return (
    <Layout pageTitle="Artiesten Template">
      <p>De content van je artiesten zal hier worden weergegeven.</p>
    </Layout>
  )
}

export default ArtistPage
```
{% endcode %}

Ga in een webbrowser naar [localhost:8000/kevin-bismark](http://localhost:8000/kevin-bismark) (verander `/kevin-bismark` met de naam van jouw artiest) en je zou je hard-coded inhoud moeten zien.

{% hint style="info" %}
Je kan je URL bijwerken met de slugs van je andere artiesten om te controleren of er ook identieke pagina's voor zijn gemaakt.
{% endhint %}

![Artist Template Page](<../../.gitbook/assets/image (88).png>)

{% hint style="info" %}
**Pro tip** 🧙‍♂️**:** Weet je niet zeker welke pagina's zijn gemaakt? Bekijk de **404-pagina** als je `gatsby develop` uitvoert. (Je kan er komen door te navigeren naar een URL van een pagina die niet bestaat.) **Onder aan de pagina staan de routes voor alle pagina's die Gatsby voor je site heeft gemaakt.**

(Als je wijzigingen aanbrengt in je routes, moet je de lokale ontwikkelingsserver stoppen en opnieuw starten om de lijst met pagina's op de **404-pagina** bij te werken.)
{% endhint %}

![](<../../.gitbook/assets/image (145).png>)
