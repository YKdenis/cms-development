---
description: >-
  Geef de about page informatie data weer op je website en style deze volgens
  het ontwerp!
---

# Herschrijf de JSX van je about page en voeg styling toe

## Taak: Voeg toe en pas de JSX structuur aan voor je About Page

Importeer de `GatsbyImage` component en de `getImage` hulpfunctie. Voeg de onderstaande JSX toe aan de return waarde van je page component:

{% code title="src/pages/about.js" %}
```jsx
// imports
const AboutPage = ({
  data: {
    wpPage: {
      aboutUsFields,
    },
  },
}) => {
  const goalPicture = getImage(aboutUsFields.goalPicture.localFile)
  const missionPicture = getImage(aboutUsFields.missionPicture.localFile)

  return (
    <Layout pageTitle="About Us">
      <section>
        <article>
          <h2>{aboutUsFields.goalTitle}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: aboutUsFields.goalDescription,
            }}
          />
        </article>
        <GatsbyImage image={goalPicture} alt={aboutUsFields.goalPicture.altText} />
      </section>
      <section>
        <GatsbyImage
          image={missionPicture}
          alt={aboutUsFields.missionPicture.altText}
        />
        <article>
          <h2>{aboutUsFields.missionTitle}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: aboutUsFields.missionDescription,
            }}
          />
        </article>
      </section>
    </Layout>
  )
}

export default AboutPage

// Page Query
```
{% endcode %}

## Taak: Voeg CSS toe aan je About page JSX  ✨

Verschillende CSS classes uit je `page.module.css` kan je hergebruiken.

* Navigeer naar je CSS bestand voor je page in je `src`-directory `page.module.css`.
* Voeg volgende CSS classes vanonder in je file toe.

{% code title="src/page.module.css" %}
```css
/* Page CSS */

.mission-section {
  display: flex;
  justify-content: space-between;
  margin-top: 120px;
}

.mission-info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 50%;
  max-width: 500px;
  margin-left: 30px;
}
```
{% endcode %}

* Importeer de CSS classes in je `src/pages/artists/index.js`.

{% code title="src/pages/about.js" %}
```jsx
import * as React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../components/layout"
import {
  header,
  headerInfo,
  headerPicture,
  subtitle,
  missionSection,
  missionInfo,
} from "../page.module.css"

// About Page Component
```
{% endcode %}

* Voeg de CSS classes toe aan je page component zoals hieronder weergegeven:

{% code title="src/pages/about.js" %}
```jsx
// Imports

const AboutPage = ({
  data: {
    wpPage: { aboutUsFields },
  },
}) => {
  const goalPicture = getImage(aboutUsFields.goalPicture.localFile)
  const missionPicture = getImage(aboutUsFields.missionPicture.localFile)

  return (
    <Layout pageTitle="About Us">
      <section className={header}>
        <article className={headerInfo}>
          <h2 className={subtitle}>{aboutUsFields.goalTitle}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: aboutUsFields.goalDescription,
            }}
          />
        </article>
        <GatsbyImage
          className={headerPicture}
          image={goalPicture}
          alt={aboutUsFields.goalPicture.altText}
        />
      </section>
      <section className={missionSection}>
        <GatsbyImage
          className={headerPicture}
          image={missionPicture}
          alt={aboutUsFields.missionPicture.altText}
        />
        <article className={missionInfo}>
          <h2 className={subtitle}>{aboutUsFields.missionTitle}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: aboutUsFields.missionDescription,
            }}
          />
        </article>
      </section>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

Proficiat! 🏆Je hebt het einde bereikt van dit hoofdstuk! Je about page is volledig gestyled. In het volgende hoofdstuk zal je de laatste pagina stylen, namelijk de contact pagina. ✨
