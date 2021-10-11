---
description: >-
  Geef de home page header data weer op je website en style deze volgens het
  ontwerp!
---

# Structureer en style de Home page header JSX

![Header sectie van je home page](<../../.gitbook/assets/image (2).png>)

## Taak: Voeg de JSX structuur toe voor je Home Page Header

Momenteel wordt je page title nog toegevoegd in je `Layout` component. Je zal niet dezelfde JSX (**HTML + Javascript**) structuur hebben voor je page titel op je home page als op je artists page. Met andere woorden je kan je page title beter in de page component zelf definiëren en niet in de `Layout` component.

### Pas je `Layout` component aan en verwijder de `pageTitle` prop:

{% code title="src/components/layout.js" %}
```jsx
import * as React from "react"
import { Link, useStaticQuery, graphql } from "gatsby"
import {
  container,
  nav,
  navLinks,
  navLinkItem,
  navLinkText,
  siteTitle,
} from "./layout.module.css"

const Layout = ({ children }) => {
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
      <title>{data.site.siteMetadata.title}</title>
      <nav className={nav}>
        <header className={siteTitle}>{data.site.siteMetadata.title}</header>
        <ul className={navLinks}>
          <li></li>
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
      <main>{children}</main>
    </div>
  )
}

export default Layout
```
{% endcode %}

Importeer de `GatsbyImage` component en de `getImage` hulpfunctie. Voeg de onderstaande JSX toe aan de return waarde van je page component:

{% code title="src/pages/index.js" %}
```jsx
// imports

import { GatsbyImage, getImage } from "gatsby-plugin-image"

const IndexPage = ({
  data: {
    wpPage: { homePage },
  },
}) => {
  const image = getImage(homePage.headerHome.picture.localFile)

  return (
    <Layout>
      <div>
        <div>
          <h1>{homePage.headerHome.title}</h1>
          <div
            dangerouslySetInnerHTML={{
              __html: homePage.headerHome.description,
            }}
          />
          <a target="__blank" href={homePage.callToAction.link}>
            {homePage.callToAction.description}
          </a>
        </div>
        <div>
          <GatsbyImage
            image={image}
            alt={homePage.headerHome.picture.altText}
          />
        </div>
      </div>
    </Layout>
  )

// Page Query
```
{% endcode %}

{% hint style="info" %}
**Let op** 👀**:** De `callToAction.link` linkt naar een externe pagina. Voor **externe links** gebruik je het `<a>`-element en voor **interne links**, links naar andere pagina's op de website, gebruik je het `Link`-component van Gatsby.
{% endhint %}

## Taak: Sprinkle wat CSS op je JSX  ✨

![](<../../.gitbook/assets/image (13).png>)

Je home page header werkt zoals het hoort maar ziet er momenteel niet uit! Tijd om wat styling toe te voegen met behulp van **CSS modules**.

**Opfrisser nodig?** Bekijk onderstaande link:

{% content-ref url="../react-in-gatsby/style-components-css-modules.md" %}
[style-components-css-modules.md](../react-in-gatsby/style-components-css-modules.md)
{% endcontent-ref %}

* Maak een nieuwe CSS file aan in je `src` map genaamd `page.module.css`.
* Voeg onderstaande CSS classes toe aan je `page.module.css` file.

{% code title="src/page.module.css" %}
```css
.header {
  display: flex;
  justify-content: space-between;
  margin-top: 60px;
}

.header-info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 50%;
  max-width: 500px;
  margin-right: 30px;s
}
.header-picture {
  border-radius: 50%;
  width: 40vw;
  height: 40vw;
  max-width: 500px;
  max-height: 500px;
}

.header-title {
  font-size: 6rem;
  line-height: 5rem;
  letter-spacing: -0.2rem;
  text-transform: uppercase;
  margin: 0;
  margin-bottom: 30px;
}

.CTA {
  display: block;
  background-color: #37ba83;
  color: white;
  border: 1px solid #000;
  border-radius: 4px;
  padding: 10px 20px;
  margin-right: auto;
  margin-top: 20px;
  text-decoration: none;
  transition: all 0.2s ease;
}

.CTA:hover {
  color: #37ba83;
  background-color: #000;
  border: 1px solid #37ba83;
}
```
{% endcode %}

* Importeer de CSS classes in je `src/pages/index.js`.

{% code title="src/pages/index.js" %}
```jsx
import * as React from "react"
import Layout from "../components/layout"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import {
  header,
  headerInfo,
  headerPicture,
  headerTitle,
  CTA,
} from "../page.module.css"

// IndexPage

// Page Query
```
{% endcode %}

* Voeg de classes toe aan je JSX code zoals het hieronder wordt weergegeven:

{% code title="src/pages/index.js" %}
```jsx
// Imports

const IndexPage = ({
  data: {
    wpPage: { homePage },
  },
}) => {
  const image = getImage(homePage.headerHome.picture.localFile)

  return (
    <Layout>
      <div className={header}>
        <div className={headerInfo}>
          <h1 className={headerTitle}>{homePage.headerHome.title}</h1>
          <div
            dangerouslySetInnerHTML={{
              __html: homePage.headerHome.description,
            }}
          />
          <a className={CTA} target="__blank" href={homePage.callToAction.link}>
            {homePage.callToAction.description}
          </a>
        </div>
        <div>
          <GatsbyImage
            image={image}
            className={headerPicture}
            alt={homePage.headerHome.picture.altText}
          />
        </div>
      </div>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

* Start je ontwikkelingsserver met `gatsby develop` en navigeer naar [localhost:8000](http://localhost:8000) in je browser.

![](<../../.gitbook/assets/image (2) (1).png>)

Super, je header sectie is af! 🥳 In het volgende deel zal je verder bouwen aan je home page en de Featured Artists sectie opmaken en stylen!
