---
description: >-
  Maak een herbruikbaar building block component aan voor de Footer en importeer
  het in je Layout component.
---

# Building block component: Footer

![Building block component: Footer](<../../.gitbook/assets/image (104).png>)

## Taak: Maak een nieuwe Building Block component aan genaamd Footer

Navigeer naar je `src/components` map en creëer een nieuw bestand met de naam `footer.js`.

* Definieer een component met de naam `Footer` en geef het de volgende JSX structuur:

{% code title="src/components/footer.js" %}
```jsx
import React from "react"

const Footer = ({ siteTitle, companyInfo }) => {
  return (
    <div>
      <div>
        <p>{siteTitle}</p>
        <p>Codobi</p>
        <p>All rights reserved.</p>
      </div>
      <div>
        <p>{`${companyInfo.address}, ${companyInfo.postcode} ${companyInfo.city}`}</p>
        <div className={socials}>
          Follow us:
          <a
            className={instagram}
            target="__blank"
            href={companyInfo.socials.instagram}
          />
          <a
            className={facebook}
            target="__blank"
            href={companyInfo.socials.facebook}
          />
        </div>
      </div>
    </div>
  )
}

export default Footer
```
{% endcode %}

{% hint style="info" %}
**Opmerking 📣:** Je footer verwacht twee `props` namelijk: `siteTitle` en `companyInfo`. De `siteTitle` is gekend in je `Layout` component maar `companyInfo` nog niet!

Je zal later de `companyInfo` binnenhalen vanuit GraphQL. De `companyInfo` is gekend in je WP contact page. Met behulp van de `useStaticQuery` zal je het op halen in je `Layout` component.
{% endhint %}

* Navigeer naar je GraphiQL interface in je browser en bouw de query op voor je `companyInfo` met behulp van je `contactPage` veld.

```graphql
wpPage(slug: { eq: "contact-us" }) {
        contactPage {
          companyInformation {
            address
            city
            postcode
            socials {
              facebook
              instagram
            }
          }
        }
      }
```

* Navigeer naar je `Layout` component en voeg je bovenstaande query toe aan de useStaticQuery hook.

{% code title="src/components/layout.js" %}
```jsx
// Imports

const Layout = ({ children }) => {
  const data = useStaticQuery(graphql`
    query {
      site {
        siteMetadata {
          title
        }
      }
      wpPage(slug: { eq: "contact-us" }) {
        contactPage {
          companyInformation {
            address
            city
            postcode
            socials {
              facebook
              instagram
            }
          }
        }
      }
    }
  `)

// return value
  )
}

export default Layout
```
{% endcode %}

* importeer je `Footer` en definieer het helemaal vanonder in je component.

{% code title="src/components/layout.js" %}
```jsx
  // Imports

  const Layout = ({ children }) => {

  // useStaticQuery hook

  return (
    <>
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
      <Footer
        siteTitle={data.site.siteMetadata.title}
        companyInfo={data.wpPage.contactPage.companyInformation}
      />
    </>
  )
}

export default Layout
```
{% endcode %}

## Taak: Style je Footer component ✨

In je Footer component zal je een link moeten leggen met Facebook en Instagram. Voor beide is er een icoontje voorzien dat je hieronder kan downloaden. Voeg het toe aan de map `src/images`.

{% file src="../../.gitbook/assets/facebook.svg" %}
Facebook Icoon
{% endfile %}

{% file src="../../.gitbook/assets/instagram.svg" %}
Instagram Icoon
{% endfile %}

![](<../../.gitbook/assets/image (154).png>)

Je Footer is een building block component m.a.w. je kan er een module CSS file voor aanmaken. Navigeer naar je map `src/components` en maak een nieuwe file aan genaamd `footer.module.css`.

* Voeg volgende CSS classes toe aan je `footer.module.css`.

{% code title="src/components/footer.module.css" %}
```css
p {
  margin: 0;
}

.wrapper {
  display: flex;
  justify-content: center;
  margin-top: 120px;
  padding: 2rem 0;
  color: #e0e0e0;
}

.wrapper > div:first-child {
  text-align: right;
  margin-right: 1rem;
}

.wrapper > div:last-child {
  margin-left: 1rem;
}

.title {
  position: relative;
  display: flex;
  align-items: center;
  flex-shrink: 0;
  font-size: 1rem;
  text-transform: uppercase;
  font-weight: 600;
  color: white;
  margin-right: auto;
}

.title::after {
  content: ".";
  position: absolute;
  right: -5px;
  bottom: 3px;
  font-size: 1.8rem;
  font-family: serif;
  color: #37ba83;
  margin-right: auto;
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
  background-image: url("../images/instagram.svg");
}

.facebook {
  background-image: url("../images/facebook.svg");
}
```
{% endcode %}

* Importeer je CSS classes in je `Footer` component bestand.

{% code title="src/components/footer.js" %}
```jsx
import React from "react"
import {
  wrapper,
  title,
  socials,
  instagram,
  facebook,
} from "./footer.module.css"

// Footer Component
```
{% endcode %}

* Voeg de classes toe aan je `Footer` JSX.

{% code title="src/components/footer.js" %}
```jsx
// Imports

const Footer = ({ siteTitle, companyInfo }) => {
  return (
    <div className={wrapper}>
      <div>
        <p className={title}>{siteTitle}</p>
        <p>Codobi</p>
        <p>All rights reserved.</p>
      </div>
      <div>
        <p>{`${companyInfo.address}, ${companyInfo.postcode} ${companyInfo.city}`}</p>
        <div className={socials}>
          Follow us:
          <a
            className={instagram}
            target="__blank"
            href={companyInfo.socials.instagram}
          />
          <a
            className={facebook}
            target="__blank"
            href={companyInfo.socials.facebook}
          />
        </div>
      </div>
    </div>
  )
}

export default Footer
```
{% endcode %}

* Open je browser en navigeer naar je [localhost:8000](http://localhost:8000).

![Footer eindresultaat](<../../.gitbook/assets/image (40).png>)

Proficiat! 🏆Je hebt het einde bereikt van dit hoofstuk! Je home page is volledig gestyled. In het volgende hoofdstuk gaan we de artists page herstructuren en stylen! ✨
