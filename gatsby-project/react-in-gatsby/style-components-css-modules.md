---
description: >-
  Nu je je paginastructuur hebt ingesteld, is het tijd om wat stijl toe te
  voegen en het mooi te maken!
---

# Style Components - CSS Modules

## Style Components met CSS-modules

Gatsby is niet strikt over welke CSS benadering je gebruikt. Je kan het systeem kiezen waarbij je je het beste voelt het voelt.

In deze zelfstudie zal je gebruik maken van **CSS-modules** om je componenten op te maken. Dit betekent dat stijlen binnen het bereik van componenten vallen, wat helpt om botsingen met **klassenaamgeving** tussen componenten te voorkomen. Gatsby is automatisch geconfigureerd om CSS-modules te verwerken - geen extra configuratie nodig!

{% hint style="info" %}
### Key Styling Concept: CSS-modules

Om stijlen te definiëren met behulp van CSS-modules, plaatst je je CSS in een bestand dat eindigt op de bestandsextensie .module.css. Dit vertelt Gatsby dat dit CSS-bestand moet worden verwerkt als een CSS-module in plaats van als gewone CSS.

Maak in je CSS-bestand afzonderlijke CSS-klassen voor elk element dat je wilt opmaken. Bijvoorbeeld:
{% endhint %}

{% code title="src/components/my-component.module.css" %}
```css
.title {
  color: blue;
  font-size: 3rem;
}
```
{% endcode %}

{% hint style="info" %}
Importeer vervolgens in je component .js-bestand elke klasse afzonderlijk en pas deze toe op het overeenkomstige React-element:
{% endhint %}

{% code title="src/components/my-component.js" %}
```jsx
import * as React from 'react'
import { title } from './my-component.module.css'
const MyComponent = () => {
  return (
    <h1 className={title}>
      Super Sweet Title Page
    </h1>
  )
}
export default MyComponent
```
{% endcode %}

{% hint style="info" %}
Als je de ontwikkelaarsconsole in je webbrowser opent en het `<h1>`-element inspecteert, zal je zien dat het een lange klassenaam heeft, zoals `my-component-module---title---2lRF7`. **Dat is de klassenaam die wordt gegenereerd door CSS-modules. Het is gegarandeerd uniek voor je hele site**, zelfs als je een ander onderdeel hebt dat ook een `title-`klasse in het `.module.css`-bestand heeft.

Dat is een van de redenen waarom **CSS-modules** een populaire CSS benadering is: ze laten je CSS schrijven die is afgestemd op je componenten, zodat je je geen zorgen hoeft te maken over botsingen tussen klasse namen van componenten.
{% endhint %}

Volg de onderstaande stappen om je `Layout` component op te maken met behulp van CSS-modules.

Maak een nieuw bestand: `src/components/layout.module.css`.

{% hint style="info" %}
Het `.module.css`-gedeelte aan het einde is belangrijk! Dat vertelt Gatsby dat deze stijlen CSS-modules gebruiken.
{% endhint %}

Begin met het toevoegen van een enkele `.container`-klasse:

{% code title="src/components/layout.module.css" %}
```css
.container {
  width: 90%;
  max-width: 1080px;
  margin: auto;
  font-family: sans-serif;
}
```
{% endcode %}

Importeer die klasse vervolgens in het .js-bestand van je `Layout`-component en gebruik de prop `className` om deze toe te wijzen aan het `<div>`-element op het hoogste niveau:

{% code title="src/components/layout.js" %}
```jsx
import * as React from 'react'
import { Link } from 'gatsby'
import { container } from './layout.module.css'

const Layout = ({ pageTitle, children }) => {
  return (
    <div className={container}>
      <title>{pageTitle}</title>
      <nav>
        <ul>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/about">About</Link></li>
        </ul>
      </nav>
      <main>
        <h1>{pageTitle}</h1>
        {children}
      </main>
    </div>
  )
}

export default Layout
```
{% endcode %}

{% hint style="info" %}
**Syntax tip**: Om klassen toe te passen op React-componenten, gebruik je de prop `className`. \(Dit is nog een voorbeeld van een ingebouwde prop die React automatisch weet te hanteren.\)

Dit kan verwarrend zijn als je gewend bent om het `class` attribuut op HTML-elementen te gebruiken. Doe je best om ze niet door elkaar te halen!
{% endhint %}

Wanneer je je lokale site in een webbrowser opent, zou je nu moeten zien dat het lettertype is gewijzigd en dat de inhoud meer op de pagina is gecentreerd.

![Home page Artist Agency](../../.gitbook/assets/image%20%28119%29.png)

Nu je hebt gezien hoe je een enkel element voor je component kunt opmaken, voeg je wat meer stijlen toe om vervolgens toe te passen op de andere elementen in je `Layout`-component. Je kan ook de `html` en `body` tag stylen in je css-bestand.

{% code title="src/components/layout.module.css" %}
```css
html {
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  font: 112.5%/1.45em sans-serif, georgia, serif;
  box-sizing: border-box;
  overflow-y: scroll;
  background-color: #000;
}
body {
  overflow: hidden;
  margin: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
  font-family: sans-serif, georgia, serif;
  font-weight: normal;
  word-wrap: break-word;
  font-kerning: normal;
  -moz-font-feature-settings: "kern", "liga", "clig", "calt";
  -ms-font-feature-settings: "kern", "liga", "clig", "calt";
  -webkit-font-feature-settings: "kern", "liga", "clig", "calt";
  font-feature-settings: "kern", "liga", "clig", "calt";
}

.container {
  width: 90%;
  max-width: 1080px;
  margin: auto;
  font-family: sans-serif;
}

.nav {
  display: flex;
}

.nav-links {
  display: flex;
  align-items: center;
  height: 90px;
  padding: 0;
  margin: 0;
  list-style: none;
}

.nav-link-item {
  padding-right: 2rem;
}

.nav-link-text {
  color: white;
  text-transform: uppercase;
  text-decoration: none;
  font-weight: 600;
  transition: color 0.2s ease;
}

.nav-link-text:hover {
  color: #37ba83;
}
```
{% endcode %}

Importeer de nieuwe klassen in je `Layout`-component en pas elke klasse toe op het overeenkomstige element.

{% code title="src/components/layout.js" %}
```jsx
import * as React from 'react'
import { Link } from 'gatsby'
import { container, nav, navLinks, navLinkItem, navLinkText } from './layout.module.css'

const Layout = ({ pageTitle, children }) => {
  return (
    <div className={container}>
      <title>{pageTitle}</title>
      <nav className={nav}>
        <ul className={navLinks}>
          <li className={navLinkItem}>
            <Link className={navLinkText} to="/">
              Home
            </Link>
          </li>
          <li className={navLinkItem}>
            <Link className={navLinkText} to="/about">
              About
            </Link>
          </li>
        </ul>
      </nav>
      <main>
        <h1>{pageTitle}</h1>
        {children}
      </main>
    </div>
  )
}

export default Layout
```
{% endcode %}

{% hint style="info" %}
**Syntax tip**: In CSS is de conventie om klassen een naam te geven met behulp van kebab-case \(zoals `.nav-links`\). Maar in JavaScript is de conventie om variabelen een naam te geven met behulp van camel case \(zoals `navLinks`\).

Gelukkig, als je CSS-modules met Gatsby gebruikt, kan je beide hebben! De klassennamen van je kebab-case in je `.modules.css`-bestanden worden automatisch geconverteerd naar camel-case-variabelen die je in je .`js`-bestanden kunt importeren.
{% endhint %}

Zodra je ontwikkelingsserver klaar is met het opnieuw opbouwen van je site, zou je je nieuwe stijlen moeten zien in je webbrowser:

![Home Page met nieuwe stijlen](../../.gitbook/assets/image%20%28139%29.png)

