---
description: Een page component is eigen aan Gatsby, niet aan React!
---

# Wat is een Page Component?

## Een page component maken

Er zijn twee hoofdtypen componenten op een Gatsby-site. Het eerste type dat je gaat maken zijn page components. **Een page component bevat alle UI-elementen voor een specifieke pagina van je site**.

In deze sectie maakt je twee nieuwe page components: **één voor de home page en één voor de about pagina**.

### Taak: update de inhoud van de startpagina

Nu je een introductie tot React hebt gekregen, is het tijd om te proberen een aantal React-componenten te schrijven. Om te beginnen werk je de inhoud voor de home page bij.

{% hint style="info" %}
Als je dit nog niet hebt gedaan, open je Gatsby-site in Visual Studio Code en start je lokale ontwikkelingsserver op de command line:
{% endhint %}

1. Open je command line / terminal.&#x20;
2. Verander je map route naar de map voor je Gatsby-site (gebruik het commando `cd`).&#x20;
3. Run **gatsby develop**.&#x20;
4. Open [localhost:8000](http://localhost:8000) in je webbrowser.

Open je `src/pages/index.js`-file. Vervang de inhoud door het volgende.

{% hint style="info" %}
Merk op hoe de structuur van de component overeenkomt met de drie stappen voor het schrijven van React-componenten?
{% endhint %}

{% code title="src/pages/index.js" %}
```jsx
// Stap 1: Importeer React
import * as React from 'react'
// Stap 2: definieer je component
const IndexPage = () => {
  return (
    <main>
      <title>Home Page</title>
      <h1>Welcome to Inghelbrecht Agency!</h1>
      <p>Lorem ipsum</p>
    </main>
  )
}
// Stap 3: Exporteer je component
export default IndexPage
```
{% endcode %}

Ga naar **localhost:8000** in je webbrowser. (Mogelijk moet je even wachten terwijl je ontwikkelingsserver opnieuw wordt opgebouwd.) Zodra je pagina is bijgewerkt, zou deze er ongeveer zo uit moeten zien:

![home page Inghelbrecht Agency](<../../.gitbook/assets/image (156).png>)

{% hint style="info" %}
#### Key Gatsby-concept 💡

Gatsby maakt automatisch pagina's aan voor React-componenten die in de `src/pages`-directory leven.

Als een gebruiker de URL probeert te bezoeken voor een pagina die niet bestaat, gebruikt Gatsby de page component `src/pages/404.js` om in plaats daarvan een fout weer te geven. Ga je gang en probeer het eens! (Als je het op **localhost:8000** probeert, moet je op de knop "**Preview custom 404-pagina**" klikken.)
{% endhint %}

![](<../../.gitbook/assets/image (151).png>)

### Taak: Maak een nieuwe page component aan voor je about pagina

Nu je de bestaande home page hebt bijgewerkt, kan je proberen een geheel nieuwe pagina te maken. Maak een about pagina, zodat je bezoekers iets meer over je agency kunt vertellen.

Maak een nieuw bestand: `src/pages/about.js`. Gebruik de onderstaande code als startpunt voor je About pagina.

{% code title="/src/pages/about.js" %}
```jsx
// Stap 1: Importeer React
import * as React from 'react'

// Step 2: Definieer je component
const AboutPage = () => {
  return (
    <main>
      <title>About Us</title>
      <h1>About Us</h1>
      <p>Artist Agency was founded in 1977 by founder, John Doe. AA continues to be at the forefront of art by establishing the careers of our talents on a holistic level -- and setting trends within the industry. </p>
    </main>
  )
}

// Stap 3: Exporteer je component
export default AboutPage
```
{% endcode %}

Ga in een webbrowser naar **localhost:8000/about**. Wanneer je ontwikkelingsserver klaar is met het opnieuw opbouwen van je site, zou de pagina about er ongeveer zo uit moeten zien:

![About us page Inghelbrecht Agency](<../../.gitbook/assets/image (26) (1).png>)

{% hint style="info" %}
#### Key Gatsby-concept 💡

Pagina's die in de map `src/pages` zijn gemaakt, gebruiken de naam van het bestand als de route voor de pagina.

Als je bijvoorbeeld een bestand had met de naam `src/pages/garden-gnomes.js`, zou je die pagina kunnen openen op **localhost:8000/garden-gnomes**.
{% endhint %}

{% hint style="warning" %}
**Let op**: Je mag de file `page_2.js` in de pages folder verwijderen.
{% endhint %}
