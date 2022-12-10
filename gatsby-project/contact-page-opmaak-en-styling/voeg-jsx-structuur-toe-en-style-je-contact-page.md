---
description: >-
  Geef de contact page informatie data weer op je website en style deze volgens
  het ontwerp!
---

# Voeg de JSX structuur toe en style je contact page

## Taak: Voeg toe en pas de JSX structuur aan voor je Contact Page

Voeg de onderstaande JSX toe aan de return waarde van je page component. Vergeet niet je imports toe te voegen voor `GatsbyImage` en `getImage`!

{% code title="src/pages/contact.js" %}
```jsx
// imports

const ContactPage = ({
  data: {
    wpPage: { contactUsFields },
  },
}) => {
  const image = getImage(contactUsFields.picture.localFile)

  return (
    <Layout>
      <section>
        <article>
          <h2>{contactUsFields.title}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: contactUsFields.description,
            }}
          />
          <div>
            <a href={`mailto:${contactUsFields.email}`}>
              {contactUsFields.email}
            </a>
            <a href={`tel:${contactUsFields.phoneNumber}`}>
              {contactUsFields.phoneNumber}
            </a>
            <p>{`${contactUsFields.address}, ${contactUsFields.zipCode} ${contactUsFields.city}`}</p>
            <div>
              Follow us:
              <a target="__blank" href={contactUsFields.instagram}>
                {" "}
              </a>
              <a target="__blank" href={contactUsFields.facebook}>
                {" "}
              </a>
            </div>
          </div>
        </article>
        <GatsbyImage image={image} alt={contactUsFields.picture.altText} />
      </section>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

## Taak: Voeg CSS toe aan je Contact page JSX  ✨

Verschillende CSS classes uit je `page.module.css` kan je hergebruiken.

* Navigeer naar je CSS bestand voor je page in je `src`-directory `page.module.css`.
* Voeg volgende CSS classes vanonder in je file toe.

{% code title="src/page.module.css" %}
```css
/* Contact Page CSS */

.company-info {
  margin-top: 60px;
}

.company-info p,
.link {
  display: block;
  margin-bottom: 1rem;
}

.link {
  color: #37ba83;
}

.socials {
  display: flex;
  align-items: center;
  margin-top: 0.5rem;
}

.instagram,
.facebook {
  background-size: 30px 30px;
  height: 30px;
  width: 30px;
  margin-left: 1rem;
  transition: transform 0.3 ease;
}

.instagram:hover,
.facebook:hover {
  transform: scale(1.1);
}

.instagram {
  background-image: url("./images/instagram.svg");
}

.facebook {
  background-image: url("./images/facebook.svg");
}
```
{% endcode %}

* Importeer de CSS classes in je `src/pages/artists/index.js`.

{% code title="src/pages/contact.js" %}
```jsx
import React from "react"
import { graphql } from "gatsby"
import { GatsbyImage, getImage } from "gatsby-plugin-image"
import Layout from "../components/layout"
import {
  header,
  headerInfo,
  headerPicture,
  subtitle,
  companyInfo,
  socials,
  facebook,
  instagram,
  link
} from "../page.module.css"

// Contact Page Component
```
{% endcode %}

* Voeg de CSS classes toe aan je page component zoals hieronder weergegeven:

{% code title="src/pages/contact.js" %}
```jsx
// Imports

const ContactPage = ({
  data: {
    wpPage: { contactUsFields },
  },
}) => {
  const image = getImage(contactUsFields.picture.localFile)

  return (
    <Layout>
      <section className={header}>
        <article className={headerInfo}>
          <h2 className={subtitle}>{contactUsFields.title}</h2>
          <div
            dangerouslySetInnerHTML={{
              __html: contactUsFields.description,
            }}
          />
          <div className={companyInfo}>
            <a className={link} href={`mailto:${contactUsFields.email}`}>
              {contactUsFields.email}
            </a>
            <a className={link} href={`tel:${contactUsFields.phoneNumber}`}>
              {contactUsFields.phoneNumber}
            </a>
            <p>{`${contactUsFields.address}, ${contactUsFields.zipCode} ${contactUsFields.city}`}</p>
            <div className={socials}>
              Follow us:
              <a
                className={instagram}
                target="__blank"
                href={contactUsFields.instagram}
              >
                {" "}
              </a>
              <a
                className={facebook}
                target="__blank"
                href={contactUsFields.facebook}
              >
                {" "}
              </a>
            </div>
          </div>
        </article>
        <GatsbyImage
          className={headerPicture}
          image={image}
          alt={contactUsFields.picture.altText}
        />
      </section>
    </Layout>
  )
}

// Page Query
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

Proficiat! 🏆Je hebt het einde bereikt van dit hoofdstuk! Je contact page is volledig gestyled. **M.a.w. je volledige website is af en klaar om gedeployed te worden!**

In het volgende hoofdstuk zal je leren hoe je met Netlify je website kan deployen en hoe je **Continuous Deployment** toevoegt via GitHub!
