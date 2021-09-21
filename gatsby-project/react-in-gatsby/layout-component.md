---
description: >-
  Je zal misschien merken dat er op elke pagina een aantal herhaalde delen van
  de gebruikersinterface zijn, zoals de sitetitel en het navigatiemenu.
---

# Wat is de Layout Component?

## Een herbruikbare Layout component maken

Je kan elementen zoals je `sitetitel` afzonderlijk naar elke pagina van je site kopiëren. Maar stel je voor dat je site tientallen \(of zelfs duizenden\) pagina's had. Als je de structuur van je `navigatiemenu` wilt wijzigen, moet je elk van die bestanden afzonderlijk bijwerken.

In plaats daarvan zou het beter zijn om **één gemeenschappelijke Layout component te maken** waarin alle gedeelde elementen worden gegroepeerd om ze op meerdere pagina's opnieuw te gebruiken. Op die manier kan je, wanneer je de layout moet bijwerken, de wijziging op één plaats aanbrengen en wordt deze automatisch toegepast op alle pagina's die dat onderdeel gebruiken.

In deze sectie maak je je eerste aangepaste Building block component: `Layout`. Om dat te doen, moet je een **speciale React-prop** gebruiken die `children` wordt genoemd.

{% hint style="info" %}
#### Key React Concept: Componenten met children

Naast de props die je aan je componenten kunt toevoegen, maakt React ook automatisch bepaalde props voor je componenten aan.

> Dit is een voorbeeld oefening, je hoeft het niet uit te voeren!

Een zo'n prop wordt `children` genoemd. Wanneer je een component rendert, wordt de onderliggende prop automatisch doorgegeven, ongeacht de inhoud die tussen de openings- en sluitingstags voor dat component komt. Dit is handig als je een component wilt maken die generieke inhoud omhult.

* De component `Link,`die je in het laatste gedeelte hebt gebruikt, gebruikte ook de prop voor `children`. Je hebt het gebruikt om de tekst door te geven die moet worden gehyperlinkt.
{% endhint %}

```jsx
<Link to="/">
  deze tekst wordt doorgegeven aan de Link component zijn children prop!
</Link>
```

{% hint style="info" %}
Zie je `Layout` component als een fotolijst. Een lijst heeft zijn eigen vorm en stijl, maar je kunt de inhoud ervan wisselen met wat je maar wilt. Je zou dezelfde fotolijst rond een foto van een huis of een standbeeld kunnen gebruiken. Je zou zelfs iets anders dan een foto kunnen plaatsen, zoals een schilderij of een borduursel.
{% endhint %}

![](../../.gitbook/assets/image%20%28140%29.png)

{% hint style="info" %}
Hier is een voorbeeld van hoe de code voor dit scenario eruit zou kunnen zien. Ten eerste, wanneer de `<Frame>` component  wordt weergegeven, wordt de inhoud tussen de openings- en sluitingstag doorgegeven:
{% endhint %}

{% code title="src/pages/gallery.js" %}
```jsx
import Frame from '../components/frame'

const GalleryPage = () => {
  return (
    <Frame>
      <p>Dit wordt doorgegeven als children</p>
    </Frame>
  )
}

export const GalleryPage
```
{% endcode %}

{% hint style="info" %}
In dit component wordt de prop voor `children` doorgegeven aan alle elementen die tussen de openings- en sluitingstag kwamen. Je kan de `children`-prop in je JSX renderen om de inhoud in te voegen.
{% endhint %}

{% code title="src/components/frame.js" %}
```jsx
import React from 'react'

const Frame = ({ children }) => {
  return (
    <div>
      <h1>Dit is de page title</h1>
      { children }
    </div>
  )
}

export default Frame
```
{% endcode %}

{% hint style="info" %}
In de browser zien de daadwerkelijke DOM-elementen er ongeveer zo uit:
{% endhint %}

```markup
<div>
  <h1>This is the page title</h1>
  <p>This will be passed in as children</p>
</div>
```

Volg de onderstaande stappen om een `Layout` component te maken en deze toe te voegen aan je Home- en About-pagina's.

Navigeer naar het bestand met de naam `src/components/layout.js`. Vervang de code met de code hieronder. **Deze component geeft een dynamische paginatitel en header weer** \(van de `paginatitel` prop\), **een lijst met navigatielinks en de inhoud die is doorgegeven met de** `children` **prop**. Om de toegankelijkheid te verbeteren, is er ook een `<main>`-element dat de paginaspecifieke elementen omhult \(de `<h1>`-header en de inhoud van `children`\).

{% code title="src/components/layout.js" %}
```jsx
import * as React from 'react'
import { Link } from 'gatsby'

const Layout = ({ pageTitle, children }) => {
  return (
    <div>
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
**Syntaxistip:** Het is je misschien opgevallen dat de `Layout` component een iets andere syntaxis gebruikt voor zijn props.

Nu in plaats van er zo uit te zien:
{% endhint %}

```jsx
const Layout = (props) => {
  ...
}
```

{% hint style="info" %}
ziet het er zo uit:
{% endhint %}

```jsx
const Layout = ({ pageTitle, children }) => {
  ...
}
```

{% hint style="info" %}
**Dit is een JavaScript-techniek die destructuring wordt genoemd**. Het is eigenlijk een shortcut voor het definiëren van variabelen op basis van de eigenschappen van een object. Het is hetzelfde als zeggen: "Neem het object dat aan deze functie wordt doorgegeven en pak de eigenschappen `pageTitle` en `children` uit in hun eigen variabelen."

Met andere woorden, het is een kortere manier om het volgende te doen
{% endhint %}

```jsx
const Layout = (props) => {
  const pageTitle = props.pageTitle
  const children = props.children
  ...
}
```

Werk je `IndexPage`-component bij om de `Layout` component te gebruiken in plaats van de hardcoded `Link`-component die je in de vorige sectie hebt toegevoegd.

{% code title="src/pages/index.js" %}
```jsx
import * as React from 'react'
import Layout from '../components/layout'

const IndexPage = () => {
  return (
    <main>
      <Layout pageTitle="Welcome to Inghelbrecht Agency!">
      <p>Lorem ipsum</p>
      </Layout>
    </main>
  )
}

export default IndexPage
```
{% endcode %}

Werk je `AboutPage`-component bij om ook de `Layout` component te gebruiken.

{% code title="src/pages/about.js" %}
```jsx
import * as React from 'react'
import Layout from '../components/layout'

const AboutPage = () => {
  return (
    <Layout pageTitle="About Us">
      <p>Artist Agency was founded in 1977 by founder, John Doe. AA continues to be at the forefront of art by establishing the careers of our talents on a holistic level -- and setting trends within the industry. </p>
    </Layout>
  )
}

export default AboutPage
```
{% endcode %}

Controleer je Home- en About-pagina's in een webbrowser om er zeker van te zijn dat je nieuwe `Layout` component werkt:

![Home page with Layout component](../../.gitbook/assets/image%20%28101%29.png)

![About page with Layout component](../../.gitbook/assets/image%20%2839%29.png)

