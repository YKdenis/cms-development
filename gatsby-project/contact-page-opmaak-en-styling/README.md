---
description: >-
  Maak een nieuwe pagina aan in je pages map genaamd contact.js. Definieer een
  page component en geef het de juiste JSX en styling.
---

# Contact Page 📞: opmaak en styling

## Maak de Contact page aan

Navigeer in je IDE (VScode) naar de `src/pages` map en creëer een nieuwe file genaamd `contact.js`. Defineer een page component en importeer vervolgens de `GatsbyImage`, `getImage,` `graphql`-tag en je `Layout`-component.

![](<../../.gitbook/assets/image (33) (1).png>)

{% hint style="info" %}
Het kan zijn dat je nog een `page-2`.js dummy file in je project hebt zitten. Je mag deze verwijderen!

De `using-typescript.tsx` file mag je ook verwijderen. Voor dit project gebruik je geen Typescript m.a.w. deze file wordt nergens gebruikt.
{% endhint %}

```jsx
import React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../components/layout"

const ContactPage = () => {
  return <Layout>Contact Page</Layout>
}

export default ContactPage
```

### Navigatie Contact page

Je Contact page is beschikbaar maar staat nog niet in je navigatiebalk! Voeg een extra `<li>`-element toe aan je `<ul>` in je `<nav>`-element van je `Layout`-component.

{% code title="src/components/layout.js" %}
```jsx
// Layout component

<nav className={nav}>
  <header className={siteTitle}>{data.site.siteMetadata.title}</header>
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
    <li className={navLinkItem}>
      <Link className={navLinkText} to="/artists">
        Artists
      </Link>
    </li>
    <li className={navLinkItem}>
      <Link className={navLinkText} to="/contact">
        Contact
      </Link>
    </li>
  </ul>
</nav>

// Layout component
```
{% endcode %}

Gebruik het `Link`-component van Gatsby en zet je `to`-attribuut op '**/contact**'.

Dit vormt de basis van je Contact page. In het volgende deel zal je de contact page query schrijven!

## Eindresultaat:

In dit hoofdstuk zal je werken aan het hieronder weergegeven ontwerp. Zoals je kan zien wordt de Wordpress data, zowel tekst als foto's, ingeladen en in een esthetisch jasje gestoken.

![Contact page eindresultaat](<../../.gitbook/assets/localhost\_8000\_contact (1).png>)
