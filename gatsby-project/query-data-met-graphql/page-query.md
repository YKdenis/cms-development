---
description: >-
  Het gebruik van GraphQL-query's in page componenten gebruikt een iets andere
  syntax dan query's in building block componenten. In page componenten gebruik
  je page query's.
---

# Wat is een Page Query?

## Query's in Page componenten

Tot nu toe heeft je site een paar statische landings pagina's: de home page en de about pagina. De volgende stap is om de data vanuit je Headless WordPress op te halen en weer te geven op je website!

We beginnen met het aanmaken van een nieuwe page component `Artists`. **Deze pagina zal een lijst weergeven met alle artiesten die je in WordPress hebt gedefineerd.**

Uiteindelijk zal je `Artists` page naar afzonderlijke pagina's linken voor elk van de artiesten in je Agency. Maar er is veel te leren om dat te bereiken, dus je zult in de komende paar delen van de zelfstudie naar dat doel toewerken.

### Taak: Maak een Artists pagina aan

Begin met het opzetten van het skelet voor je nieuwe `Artists` page component.

Maak een nieuw bestand: `src/pages/artists.js`. Definieer en exporteer een nieuwe page component voor je `Artists` page. Gebruik je bestaande `Layout` component om een basisstructuur toe te voegen.

{% code title="src/pages/artists.js" %}
```jsx
import * as React from 'react'
import Layout from '../components/layout'
const ArtistsPage = () => {
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      <p>A list of artists will be displayed here.</p>
    </Layout>
  )
}
export default ArtistsPage
```
{% endcode %}

Voeg een link naar je nieuwe `Artists` page toe aan de navigatiebalk in je Layout component:

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
          <li className={navLinkItem}>
            <Link className={navLinkText} to="/artists">
              Artists
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

Als je nu naar [localhost:8000/artists](http://localhost:8000/artists) gaat in je webbrowser, zou je je nieuwe `Artists` page moeten zien en zou er een link naar de `Artists` page in je navigatiebalk moeten zijn.

![Skelet Artists page](<../../.gitbook/assets/image (124).png>)

### Taak: Connect je Headless WordPress met behulp van een source plugin 

Nu je een Artists page hebt, is het tijd om je data vanuit Headless WP op te vragen en toe te voegen aan de **Data Layer **van Gatsby! **Om dat te doen, gebruik je een plugin genaamd **`gatsby-source-wordpress`.

Installeer de `gatsby-source-wordpress` plugin. Navigeer naar je terminal en type de volgende lijn code. 

{% hint style="info" %}
**Let er op dat je in de root map van je project zit!**
{% endhint %}

```jsx
npm install gatsby-source-wordpress
```

{% hint style="info" %}
Zie het [README-bestand](https://www.gatsbyjs.org/packages/gatsby-source-wordpress) van de `gatsby-source-wordpress` plugin voor meer informatie over de functies en features van de plugin.
{% endhint %}

Voeg de `gatsby-source-wordpress`** **plugin toe aan `gatsby-config.js` met behulp van de volgende code:

{% hint style="info" %}
Omdat `gatsby-source-wordpress` enkele aanvullende configuratie-opties vereist, gebruik je een `object` in plaats van een `string`. 

* Je geeft een **key** `resolve` mee waaraan je de naam van je plugin geeft: `gatsby-source-wordpress`
* Een object genaamd `options` waarin je extra configuratie kan meegeven. In het geval van `gatsby-source-wordpress` moet je een `url` key meegeven met **als waarde de url van je graphql endpoint in je Headless Wordpress.**
{% endhint %}

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
    {
      resolve: "gatsby-source-wordpress",
      options: {
        /*
         * De volledige URL van je Headless WordPress site's GraphQL API.
         * Voorbeeld : "https://www.example-site.com/graphql"
         */
        url: "http://artist-agency-2021.local/graphql",
      },
    },
  ],
};
```

Het bovenstaande codevoorbeeld laat zien hoe je je Headless WP koppelt aan je Gatsby a.d.h.v. de graphql endpoint van je WP applicatie. Je kan de URL terug vinden als je navigeert naar je **WP dashboard -> graphQL -> Settings - GraphQL Endpoint**.

![http://artist-agency-2021.local/graphql](<../../.gitbook/assets/image (125).png>)

Met m.b.v. deze URL zal Gatsby je data vanuit Headless WP doorsluizen naar de Data Layer en beschikbaar stellen in je gehele project. 

{% hint style="info" %}
**Opmerking **📣**: **Je Headless WordPress applicatie runt hoogstwaarschijnlijk lokaal op je computer. **Het is belangrijk dat je WP applicatie runt in Local by Flywheel**. Indien dit niet het geval is zal Gatsby het endpoint niet terugvinden en de data niet kunnen gebruiken in haar Data Layer.
{% endhint %}

#### WordPress plugin - WPGatsby plugin

Het laatste dat je nog zal moeten doen is de plugin **WPGatsby downloaden en installeren** op je WordPress Applicatie. Zonder deze plugin zal je Gatsby website geen connectie kunnen maken met je WP graphql endpoint!

![WPGatsby plugin in de WordPress plugin store](<../../.gitbook/assets/image (127).png>)

#### Query de WordPress data vanuit je Data Layer

Herstart je lokale ontwikkelingsserver om ervoor te zorgen dat de configuratie wijzigingen worden oppikt en je WordPress data wordt toegevoegd aan de Data Layer.

Je kan de query `AllWpArtist `gebruiken om gegevens over van meerdere artiesten tegelijk op te vragen. Probeer in GraphiQL de verschillende velden binnen `AllWpArtist` te verkennen om te zien welke soorten gegevens je terugkrijgt. Maak vervolgens een query met behulp van het veld `AllWpArtist` om de `firstName`, `lastName` en `artistName` van alle artiesten in je `Artist Page` te krijgen:

{% hint style="info" %}
**Opmerking **📣: Je query, voor het ophalen van je artists, heeft in Gatsby een geheel andere structuur dan in je GraphiQL op je WordPress Applicatie.

Als je meerdere artiesten wilt opvragen gebruik je `AllWpArtist` en indien je één artiest wilt opvragen gebruik je `wpArtist`. Met behulp van een selector (paars veld in GraphiQL) kan je specificeren welke artist je wilt opvragen.

Voor meer informatie bekijk de [GitHub pagina](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-source-wordpress/docs/tutorials/building-a-new-site-wordpress-and-gatsby.md) van `gatsby-source-wordpress`.
{% endhint %}

```graphql
query MyQuery {
  allWpArtist {
    edges {
      node {
      	id
        artistMeta {
          firstName
          lastName
          artistName
        }
      }
    }
  }
}
```

Voer de query uit in GraphiQL. Je reactie in het Result veld zou er ongeveer zo uit moeten zien als het onderstaande object:

```yaml
{
  "data": {
    "allWpArtist": {
      "edges": [
        {
          "node": {
            "artistMeta": {
              "firstName": "Kevin",
              "lastName": "Bismark",
              "artistName": "John Doe"
            },
            "id": "cG9zdDoxMjM="
          }
        },
        {
          "node": {
            "artistMeta": {
              "firstName": "Joel",
              "lastName": "Mott",
              "artistName": null
            },
            "id": "cG9zdDoxMTg="
          }
        },
        {
          "node": {
            "artistMeta": {
              "firstName": "Rayan",
              "lastName": "Miller",
              "artistName": null
            },
            "id": "cG9zdDoxMTI="
          }
        },
        {
          "node": {
            "artistMeta": {
              "firstName": "Anne",
              "lastName": "Woznak",
              "artistName": null
            },
            "id": "cG9zdDoxMDc="
          }
        }
      ]
    }
  },
  "extensions": {}
}
```

### Taak: gebruik een page query om de lijst met artiesten naar je Artist page te halen

Nu je een GraphQL-query hebt gemaakt die een lijst met je artiesten retourneert, is het tijd om die gegevens op je Artist page weer te geven!

Het gebruik van GraphQL-query's in Page component gebruikt een iets andere syntax dan query's in Building Block components. In Page component gebruik je page query's.

{% hint style="info" %}
#### Key Gatsby concept: gegevens in page componenten trekken met page query's 

Het proces voor het maken van een query in een page component ziet er iets anders uit dan `useStaticQuery`:

Importeer de `graphql`-tag uit de Gatsby-package. Exporteer een variabele die een string opslaat met de GraphQL-query die je wilt uitvoeren. **Wanneer je site wordt gebouwd, voert Gatsby je page query uit en geeft de resulterende gegevens door aan je page component als een **`prop`** die **`data`** wordt genoemd.** Je page query moet buiten je page component worden gedefinieerd. (Met `useStaticQuery` is je query gedefinieerd in je component.) Je kan de  `data` prop in je page component gebruiken om je page query gegevens op te halen en te gebruiken. Je kan de Javascript punt-operator (`.`) gebruiken om velden binnen de `data` prop te kiezen. 

**Hier is een klein voorbeeld om te laten zien hoe dit proces er in de praktijk uitziet:**
{% endhint %}

```jsx
import * as React from 'react'
// Stap 1: Importeer de graphql tag
import { graphql } from 'gatsby'
const HomePage = ({ data }) => {
  return (
    <p>
      { /* Stap 3: Gebruik de data in je component*/ }
      { data.site.siteMetadata.description }
    </p>
  )
}
// Stap 2: Exporteer een page query
export const query = graphql`
  query {
    site {
      siteMetadata {
        description
      }
    }
  }
`
export default HomePage
```

Volg de onderstaande stappen om een lijst met artiesten toe te voegen aan je Artist page.

#### 1) Importeer de `graphql`-tag uit de Gatsby-package.

{% code title="src/pages/artists.js" %}
```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import Layout from '../components/layout'

const ArtistsPage = () => {
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      <p>A list of artists will be displayed here.</p>
    </Layout>
  )
}
export default ArtistsPage
```
{% endcode %}

#### 2) Definieer en exporteer je page query. 

Kopieer de query die je in GraphiQL hebt gebouwd. Opmerking: de query die jee in GraphiQL bouwt, heeft standaard een query name, zoals `MyQuery`. Mogelijk zie je een fout als je meer dan één query met dezelfde naam hebt, dus **nadat je je query van GraphiQL naar je component hebt gekopieerd, verwijder je best de query name** (zoals in het onderstaande codevoorbeeld).

{% hint style="info" %}
**Opmerking 📣:** Als alternatief kan je elk van je queries een unieke naam geven.** Query names kunnen handig zijn voor het opsporen van fouten die in je console verschijnen wanneer Gatsby je query's uitvoert tijdens het bouwen.**
{% endhint %}

{% code title="src/pages/artists.js" %}
```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import Layout from '../components/layout'

const ArtistsPage = () => {
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      <p>A list of artists will be displayed here.</p>
    </Layout>
  )
}

export const query = graphql`
  query {
  allWpArtist {
    edges {
      node {
        id
        artistMeta {
          firstName
          lastName
          artistName
        }
      }
    }
  }
}

`

export default ArtistsPage
```
{% endcode %}

#### 3) Voeg de **`data`** prop toe aan de functie definitie. 

Vervang vervolgens het placeholder-element  door een lijst met artiesten. Gebruik de Javascript-array `.map()`-methode om de `edges`-array te doorlopen en de `firstName` en `lastName` voor elke artist weer te geven. 

{% hint style="info" %}
**Syntax tip**: in JavaScript hebben arrays een ingebouwde `.map()`-methode, die je kan gebruiken om over elementen in een array te itereren. Je kan vervolgens elk element manipuleren zonder de originele waarde van de array aan te tasten.

.`map()` neemt een functie op, die wordt uitgevoerd op elk element in de array. In het onderstaande codeblok gebruik je `.map()` om over elk van de `edges` in `data.allWpArtist.edges` te lopen. Voor elke iteratie wordt er een `Object` terug gegeven met een zelfbenoemde naam `item` die de geneste structuur volgt van je GraphQL-query: `item.node.artistMeta`. Je steekt `item.node.artistMeta` in een variabele genaamd `artist` die je vervolgens kan aanroepen om de `firstName` en `lastName` op te vragen in het React-element dat je retourneert voor elke artist.

Als je in React de methode `.map()` gebruikt om een lijst met elementen weer te geven, moet je elk element in de lijst een unieke `key` prop geven. Dit helpt React bij te houden welke waarden zijn gewijzigd en opnieuw moeten worden weergegeven. Voor meer informatie over het renderen van lijsten in React, bekijk de [React Docs: Lists and Keys](https://reactjs.org/docs/lists-and-keys.html).
{% endhint %}

```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import Layout from '../components/layout'

const ArtistsPage = ({data: {allWpArtist: {edges}}}) => {
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      {edges.map((item) => {
        const artist = item.node.artistMeta;
        return <p key={item.node.id}>{artist.firstName} {artist.lastName}</p>
      })}
    </Layout>
  )
}

export const query = graphql`
  query {
   allWpArtist {
    edges {
      node {
        id
        artistMeta {
          firstName
          lastName
          artistName
        }
      }
    }
  }
}

`

export default ArtistsPage
```

Als je nu naar je Artists page in een webbrowser kijkt, zou je een lijst moeten zien met de volledige namen van je artiesten:

![Artists page met lijst artiesten namen](<../../.gitbook/assets/image (128).png>)

Goed gedaan! 🎉 Je hebt de eerste stap van je nieuwe Artists page voltooid.

Maak je nog geen zorgen over de styling en de exacte data dat wordt weergegeven. Je zal dit later in een volgende tutorial onder de loep nemen!
