---
description: >-
  Nu je het algemene proces hebt gezien voor hoe gegevens worden verwerkt op je
  Gatsby-site, is het tijd om het zelf uit te proberen.
---

# Het schrijven van een Query op de Data Layer

## Query's in Building Block components

Haal de `sitetitle` in de `Layout` component binnen. Het proces voor het gebruik van GraphQL-query's in je componenten ziet er enigszins anders uit, **afhankelijk van of het een Page Component of een Building Block component is**.

In dit eerste gedeelte begin je met het ophalen van gegevens in een Building Block component. Om dat te doen, werk je je `Layout` component bij om de titel van je site op te halen en weer te geven.

### Taak: gebruik GraphiQL om de query op te bouwen

Kijk in je `gatsby-config.js`-bestand. Er staat al wat informatie over je site in het `siteMetadata`-object.

```yaml
module.exports = {
  siteMetadata: {
    title: "Inghelbrecht Agency",
    description: "Artist Agency was founded in 1977 by founder, John Doe. AA continues to be at the forefront of art by establishing the careers of our talents on a holistic level -- and setting trends within the industry.",
    author: "@gatsbyjs",
    siteUrl: "https://gatsbystarterdefaultsource.gatsbyjs.io/",
  },
  plugins: [
    "gatsby-plugin-image",
    "gatsby-plugin-sharp",
  ],
};
```

De `siteMetadata-`gegevens worden automatisch in de GraphQL Data Layer getrokken, dus je hebt geen `source`-plugin nodig.

Aangezien je geen `source`-plugin hoeft in te stellen, kan je rechtstreeks naar GraphiQL navigeren om je GraphQL-query  op te bouwen:

Ga in je webbrowser naar [localhost:8000/\__\_graphiql](http://localhost:8000/\__\_graphiql) om de GraphiQL-interface te zien. Open in je **Explorer** de keuzelijst voor het `site` veld. Open in het `site` veld de tweede keuzelijst voor het veld `siteMetadata` (de blauwe). Dit komt overeen met het `siteMetadata`-object in je `gatsby-config.js`-bestand. 

{% hint style="info" %}
#### Dubbel zien? 👀

Het is je misschien opgevallen dat er twee verschillende keuzelijsten zijn voor `siteMetadata` (en voor elk veld onder de site dropdown).

De eerste (**de paarse met een dubbele punt**, `siteMetadata:`) is eigenlijk een argument dat aan het `site` veld is gekoppeld. Je kan de paarse keuzelijsten gebruiken om te filteren welke gegevens uit de Data Layer in het antwoord worden geretourneerd. (Je zult hier later een voorbeeld van zien.)

De tweede (**de blauwe zonder dubbele punt, **`siteMetadata`) is wat je vaker zult gebruiken. Deze voegt het daadwerkelijke `siteMetadata`-veld toe aan je query, die GraphQL vertelt om dat veld in je response data op te nemen.

Probeer elk van de keuzelijsten in de **Explorer** aan te vinken en kijk hoe de query in het **Query-document** verandert. Welke verschillen merk je op?
{% endhint %}

Vink binnen `siteMetadata` het vakje naast het titel aan. De query in je **query-document** zou er als volgt uit moeten zien:

```graphql
query MyQuery {
  site {
    siteMetadata {
      title
    }
  }
}
```

Klik op de knop "**Execute** **Query**" (het driehoekje "**play**" boven aan de pagina) om de query uit te voeren. Het antwoord in het **Result veld** zou er ongeveer zo uit moeten zien als het onderstaande object. **Merk op hoe de structuur van het gegevensobject in het antwoord overeenkomt met de structuur van de velden in de query!**

```yaml
{
  "data": {
    "site": {
      "siteMetadata": {
        "title": "Inghelbrecht Agency"
      }
    }
  },
  "extensions": {}
}
```

Probeer de waarde van de title** **prop in je `gatsby-config.js`-bestand te wijzigen. Wanneer je het bestand opslaat, moet je site opnieuw worden opgebouwd (`gatbsy develop`) en wanneer het klaar is, kan je de query opnieuw uitvoeren in GraphiQL en je bijgewerkte gegevens bekijken.

### Taak: gebruik `useStaticQuery` om de sitetitle in de `Layout` component binnen te halen en weer te geven. 

Nu je een GraphQL-query hebt die de gegevens retourneert waarnaar je op zoek bent, hoe gebruikt je die query dan in je React-componenten?

Om gegevens naar een Building Block component te halen, gebruik je een vooraf gedefinieerde functie van Gatsby genaamd `useStaticQuery`.

{% hint style="info" %}
#### Key Gatsby-concept: gegevens in Building Block componenten trekken met `useStaticQuery` 

De Gatsby-package heeft een speciale vooraf gedefinieerde hook waarmee je GraphQL-query's aan je Building Block componenten kan toevoegen: `useStaticQuery`.

`useStaticQuery` neemt één parameter: een`  templated string  `van de GraphQL-query die je wilt uitvoeren. Het retourneert de gevraagde gegevens, die je in een variabele kunt opslaan en vervolgens in je hele component kunt gebruiken.

**Hier is een kort overzicht van het proces voor het toevoegen van `useStaticQuery` om gegevens naar je Building Block componenten te door te sluizen:**

Importeer de `useStaticQuery`-hook en de `graphql`-tag uit de gatsby-package. 

* De `graphql`-tag is iets dat letterlijk een [tagged template literal ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates)wordt genoemd. Kortom, de `graphql`-tag vertelt Gatsby dat de string die erop volgt een GraphQL-query is, zodat Gatsby deze kan ontleden en uitvoeren.
{% endhint %}

```javascript
import { useStaticQuery, graphql } from 'gatsby'
```

{% hint style="info" %}
Roep in je component `useStaticQuery` aan met behulp van de graphql template tag en je query van GraphiQL. Sla de resultaten op in een nieuwe variabele zodat je deze later in je component kan gebruiken.
{% endhint %}

```javascript
const data = useStaticQuery(graphql`
  // Copy-paste je query van GraphiQL hier, 
     en delete de query naam "MyQuery"
`)
```

{% hint style="info" %}
Gebruik de gegevens in je component door de puntoperator (`.`) te gebruiken om toegang te krijgen tot het juiste veld buiten het antwoord. 

#### Hier, een klein voorbeeld om te laten zien hoe dit proces er in de praktijk uitziet:
{% endhint %}

{% code title="src/components/header.js" %}
```jsx
import * as React from 'react'

// Stap 1: Importeer de useStaticQuery hook en graphql tag
import { useStaticQuery, graphql } from 'gatsby'

const Header = () => {
  /* Stap 2: gebruik de useStaticQuery hook en
    graphql tag om de data te query'en
    (De query wordt uitgevoerd tijdens build time) */
  const data = useStaticQuery(graphql`
    query {
      site {
        siteMetadata {
          title
        }
      }
    }
  `)

  return (
    <header>
      {/* Stap 3: Gebruik de data in je component */}
      <h1>{ data.site.siteMetadata.title }</h1>
    </header>
  )
}

export default Header
```
{% endcode %}

{% hint style="info" %}
**Opmerking **🙋‍♂️: Je kan `useStaticQuery` slechts één keer per bestand aanroepen. **Als je meerdere velden nodig hebt, kan je ze allemaal in één query toevoegen**.

Als je bijvoorbeeld gegevens nodig hebt uit zowel het `site` veld als het veld `siteBuildMetadata`, kan je de volgende query aanroepen om `StaticQuery` te gebruiken:
{% endhint %}

```javascript
const data = useStaticQuery(graphql`
  query {
    site {
      siteMetadata {
        title
      }
    }
    siteBuildMetadata {
      buildTime
    }
  }
`)
```

Volg de onderstaande stappen om `useStaticQuery` te gebruiken om de `sitetitle` uit de metagegevens van je site op te halen in je `Layout` component.

Importeer de `useStaticQuery`-functie en de `graphql`-tag uit de Gatsby package.

{% code title="src/components/layout.js" %}
```javascript
import * as React from 'react'
import { Link, useStaticQuery, graphql } from 'gatsby'
import { container, nav, navLinks, navLinkItem, navLinkText } from './layout.module.css'

const Layout = ({ pageTitle, children }) => {
  return (
    // ...
  )
}

export default Layout
```
{% endcode %}

Roep `useStaticQuery` aan en geef het de query door die je in GraphiQL hebt gemaakt. Zorg ervoor dat je de `graphql`-tag gebruikt, zodat Gatsby weet dat de string die je doorgeeft een GraphQL-query is. Sla de geretourneerde waarde van `useStaticQuery` op in een variabele. 

{% hint style="info" %}
**Opmerking** 🙋: de query die je in GraphiQL bouwt, heeft standaard een **query name**, zoals **MyQuery**. Mogelijk zie je een fout als je meer dan één query met dezelfde naam hebt, dus **nadat je je query van GraphiQL naar je component hebt gekopieerd, verwijder je de naam** (zoals in het onderstaande codevoorbeeld).
{% endhint %}



{% code title="src/components/layout.js" %}
```javascript
import * as React from 'react'
import { Link, useStaticQuery, graphql } from 'gatsby'
import { container, nav, navLinks, navLinkItem, navLinkText } from './layout.module.css'

const Layout = ({ pageTitle, children }) => {
 const data = useStaticQuery(graphql`
    query {
      site {
        siteMetadata {
          title
        }
      }
    }
  `)
  return (
    // ...
  )
}

export default Layout
```
{% endcode %}

{% hint style="info" %}
**Opmerking** 🙋: als je een regel toevoegt om de waarde van je `data` variabele naar de console af te drukken, zal je zien dat het antwoord een iets andere structuur heeft dan hoe het eruitzag in het **Result venster **van GraphiQL. In het bijzonder bevat je `data` variabele alleen het object dat overeenkomt met het `data` veld in het **Result venster**.

Dus als je GraphiQL **Result venster** dit liet zien:
{% endhint %}

```yaml
{
  "data": {
    "site": {
      "siteMetadata": {
        "title": "Inghelbrecht Agency"
      }
    }
  },
  "extensions": {}
}
```

dan heeft je `data` variabele de volgende structuur:

```yaml
{
  "site": {
    "siteMetadata": {
      "title": "Inghelbrecht Agency"
    }
  }
}
```

Nu je een variabele hebt met de resultaten van je query, kan je de `title` van je site in de **JSX** weergeven voor je `Layout` component. Om toegang te krijgen tot de `sitetitle`, gebruik je de JavaScript punt-operator (`.`) om de waarde van `data.site.siteMetadata.title` op te halen. **Voeg het toe zodat het zowel in het browsertabblad, als bovenaan je pagina-inhoud wordt weergegeven**.

{% code title="src/components/layout.js" %}
```jsx
import * as React from 'react'
import { Link, useStaticQuery, graphql } from 'gatsby'
import {
  container,
  heading,
  navLinks,
  navLinkItem,
  navLinkText
} from './layout.module.css'

const Layout = ({ pageTitle, children }) => {
  const data = useStaticQuery(graphql`
    query {
      site {
        siteMetadata {
          title
        }
      }
    }
  `)

  return (
    <div className={container}>
      <title>{pageTitle} | {data.site.siteMetadata.title}</title>
      <header>{data.site.siteMetadata.title}</header>
      <nav>
        <ul className={navLinks}>
          <li className={navLinkItem}>
            <Link to="/" className={navLinkText}>
              Home
            </Link>
          </li>
          <li className={navLinkItem}>
            <Link to="/about" className={navLinkText}>
              About
            </Link>
          </li>
        </ul>
      </nav>
      <main>
        <h1 className={heading}>{pageTitle}</h1>
        {children}
      </main>
    </div>
  )
}

export default Layout
```
{% endcode %}

![Site title op de home page in nav menu](<../../.gitbook/assets/image (122).png>)

Nu de `sitetitle` op de pagina verschijnt, is het tijd om wat stijl toe te voegen! Definieer enkele stijlen voor de `sitetitle` onder de bestaande stijlen in je `layout.module.css`-bestand. Vervang ook je `nav-link-item` klasse van `padding-left` naar `padding-right`.

{% code title="src/components/layout.module.css" %}
```css
.site-title {
  position: relative;
  display: flex;
  align-items: center;
  height: 90px;
  flex-shrink: 0;
  font-size: 1.2rem;
  text-transform: uppercase;
  font-weight: 600;
  margin-right: auto;
}

.site-title::after {
  content:'.';
  position: absolute;
  right: -5px;
  bottom: 35px;
  font-size: 2rem;
  font-family: serif;
  color: #37BA83;
  margin-right: auto;
}

.nav-link-item {
  padding-left: 2rem;
}
```
{% endcode %}

Importeer je nieuwe CSS in je `Layout` component en pas ze toe op de `<header>` met de `sitetitle` die je hebt toegevoegd.

{% code title="src/components/layout.js" %}
```jsx
import * as React from 'react'
import { Link, useStaticQuery, graphql } from 'gatsby'
import { 
  container, 
  nav, 
  navLinks, 
  navLinkItem, 
  navLinkText, 
  siteTitle 
} from './layout.module.css'

const Layout = ({ pageTitle, children }) => {
  const data = useStaticQuery(graphql`
    query {
      site {
        siteMetadata {
          title
        }
      }
    }
  `)

  return (
    <div className={container}>
      <title>{pageTitle} | {data.site.siteMetadata.title}</title>
      <nav className={nav}>
        <header className={siteTitle}>
          {data.site.siteMetadata.title}
        </header>
        <ul className={navLinks}>
        <li>
        </li>
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

Wanneer je browser opnieuw wordt geladen, zie je dat je de nieuwe CSS is toegepast op de titel van je site.

![Home page met CSS sitetitle](<../../.gitbook/assets/image (123).png>)

Gefeliciteerd, je hebt zojuist GraphQL gebruikt om gegevens naar je site te door te sluizen! Probeer de `sitetitle` in je `gatsby-config.js`-bestand te wijzigen en bekijk je ge-update site in de browser. 💻
