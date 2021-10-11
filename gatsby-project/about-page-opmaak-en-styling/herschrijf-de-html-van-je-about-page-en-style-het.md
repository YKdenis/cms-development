---
description: >-
  Geef de about page informatie data weer op je website en style deze volgens
  het ontwerp!
---

# Herschrijf de HTML van je about page en style het

## Taak: Voeg toe en pas de JSX structuur aan voor je About Page

Importeer de `GatsbyImage` component en de `getImage` hulpfunctie. Voeg de onderstaande JSX toe aan de return waarde van je page component:

{% code title="src/pages/about.js" %}
```jsx
// imports
import { GatsbyImage, getImage } from "gatsby-plugin-image"

const AboutPage = ({
  data: {
    wpPage: {
      aboutPage: { headerAboutUs, mission },
    },
  },
}) => {
  const imageHeader = getImage(headerAboutUs.picture.localFile)
  const imageMission = getImage(mission.bannerPicture.localFile)

  return (
    <Layout pageTitle="About Us">
      <div>
        <div>
          <h2>{headerAboutUs.title}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: headerAboutUs.description,
            }}
          />
        </div>
        <GatsbyImage image={imageHeader} alt={headerAboutUs.picture.altText} />
      </div>
      <div>
        <div>
          <GatsbyImage
            image={imageMission}
            alt={mission.bannerPicture.altText}
          />

          <h2>{mission.title}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: mission.description,
            }}
          />
        </div>
      </div>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

## Taak: Voeg CSS toe aan je About page JSX  ✨

Verschillende CSS classes uit je `page.module.css` kan je hergebruiken.

* Navigeer naar je CSS bestand voor je page in je `src`-directory `page.module.css`.
* Voeg volgende CSS classes vanonder in je file toe.

{% code title="src/page.module.css" %}
```css
// Page CSS

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
    wpPage: {
      aboutPage: { headerAboutUs, mission },
    },
  },
}) => {
  const imageHeader = getImage(headerAboutUs.picture.localFile)
  const imageMission = getImage(mission.bannerPicture.localFile)

  return (
    <Layout pageTitle="About Us">
      <div className={header}>
        <div className={headerInfo}>
          <h2 className={subtitle}>{headerAboutUs.title}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: headerAboutUs.description,
            }}
          />
        </div>
        <GatsbyImage
          className={headerPicture}
          image={imageHeader}
          alt={headerAboutUs.picture.altText}
        />
      </div>
      <div className={missionSection}>
        <GatsbyImage
          className={headerPicture}
          image={imageMission}
          alt={mission.bannerPicture.altText}
        />
        <div className={missionInfo}>
          <h2 className={subtitle}>{mission.title}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: mission.description,
            }}
          />
        </div>
      </div>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

Proficiat! 🏆Je hebt het einde bereikt van dit hoofdstuk! Je about page is volledig gestyled. In het volgende hoofdstuk zal je de laatste pagina stylen, namelijk de contact pagina. ✨

