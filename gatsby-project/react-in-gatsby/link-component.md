---
description: >-
  Nu je een paar page components hebt gebouwd, is het tijd om naar het andere
  type React-componenten op een Gatsby-site te kijken: "building block"
  -componenten.
---

# Wat is een Link Component?

### Herhaling Building-block componenten

{% hint style="info" %}
**Opmerking**: de term **Building-block component** is geen officiële technische term. Het is gewoon de beste naam die Gatsby kon bedenken om dit soort componenten te beschrijven.
{% endhint %}

**Building-block componenten zijn kleinere componenten die slechts een deel van de gebruikersinterface van een pagina vertegenwoordigen** (in plaats van een hele pagina). Denk terug aan het voorbeeld van de winkelwebsite uit de "React in Gatbsy" sectie. De componenten `Navbar`, `Sidebar`, `ProductGrid` en `ProductCard` zijn voorbeelden van Building-block componenten. Je kan verschillende kleinere Building-block componenten combineren tot een grotere page component.

![](<../../.gitbook/assets/image (95).png>)

Een van de krachtige dingen van Building-block componenten is dat je **dezelfde component op meerdere plaatsen op je site kunt hergebruiken**. Dit is vooral handig voor delen van je gebruikersinterface die een vergelijkbare structuur delen, maar verschillende waarden weergeven.

Elk van de `ProductCard`-componenten in het bovenstaande productraster toont bijvoorbeeld een foto van het product, de productnaam, een korte beschrijving, de prijs en een link naar de productpagina.

De exacte waarden veranderen voor elk product, maar de algemene structuur blijft hetzelfde. Door de `ProductCard`-component dynamisch te maken, kan je dezelfde code hergebruiken voor alle producten in het raster!

### Herhaling Props

{% hint style="info" %}
React heeft een ingebouwde functie om je te helpen je componenten dynamisch te maken: **properties (of kortweg props)**.

De onderstaande codefragmenten laten **een voorbeeld** (je hoeft dit zelf niet uit te voeren) zien van hoe je een prop in een component kan doorgeven wanneer deze wordt weergegeven en hoe je de waarde van die prop binnen dat component kan gebruiken:

* Wanneer je je component definieert, moet deze een enkel argument bevatten: een object met de naam `props`. Het object "**props"** heeft alle eigenschappen die je aan je component hebt doorgegeven toen je deze renderde.
{% endhint %}

{% code title="src/components/greeting.js" %}
```jsx
// Defineren van de <Greeting> component
const Greeting = (props) => {
  return (
    <p>Hi {props.name}!</p>
  )
}
```
{% endcode %}

{% hint style="info" %}
Syntax-tip: in JSX kan je elke JavaScript-expressie insluiten door deze om te wikkelen met {}. Dat is hoe je toegang krijgt tot de waardes die in het **props-object** leven.

* Bij het renderen van het onderdeel `Greeting` geef je de naam prop door met een specifieke waarde, zoals "**Megan**". Je kan elke keer dat je de component `Greeting` rendert, een andere waarde gebruiken.
{% endhint %}

{% code title="src/pages/say-hello.js" %}
```jsx
// Renderen van de <Greeting> component

const SayHello = () => {
  return (
    <div>
      <Greeting name="Megan" />
      <Greeting name="Obinna" />
      <Greeting name="Generosa" />
    </div>
  )
}
```
{% endcode %}

{% hint style="info" %}
Je kan je **props** een naam geven die je maar wilt. Als je bijvoorbeeld `iceCreamFlavor="mint chip"` hebt doorgegeven bij het renderen van een component, zou die prop beschikbaar zijn voor gebruik in je component op `props.iceCreamFlavor.`
{% endhint %}

## Gatsby Link Component&#x20;

Tot nu toe heeft je artist agency twee afzonderlijke pagina's (**Home en About**), maar de enige manier om van de ene pagina naar de andere te gaan, is door de URL handmatig bij te werken. Het zou leuk zijn om links toe te voegen om het schakelen tussen pagina's op je site gemakkelijker te maken.

De component `Link` is een voorbeeld van een vooraf gebouwde component die je in je site kunt gebruiken. Met andere woorden, de component `Link` wordt gedefinieerd en onderhouden door een ander package (in dit geval het **Gatsby-package**). Dat betekent dat je het kunt importeren en gebruiken in je eigen componenten zonder al te veel te weten over hoe het onder de motorkap werkt.

Met de component `Link` kan je een koppeling toevoegen naar een andere pagina op je Gatsby-site. Het is vergelijkbaar met een HTML `<a>`-tag, maar met enkele extra prestatievoordelen. De component `Link` neemt een `prop` aan, die vergelijkbaar is met het `href-attribuut` van de `<a>`-tag. De waarde moet het URL-pad zijn naar de pagina op je site waarnaar je wilt linken.

{% hint style="info" %}
### Key Gatsby-concept 💡

Het component Gatsby `Link` biedt een prestatiefunctie die **preloading** wordt genoemd. Dit betekent dat de bronnen voor de gelinkte pagina worden opgevraagd wanneer de link in beeld komt of wanneer de muis erop zweeft. Op die manier kan de nieuwe pagina supersnel laden wanneer de gebruiker daadwerkelijk op de link klikt.

**Gebruik de `Link`-component om te linken tussen pagina's binnen je site. Gebruik de normale HTML `<a>`-tag voor externe links naar pagina's die niet door je Gatsby-site zijn gemaakt.**
{% endhint %}

Volg de onderstaande stappen om `Link`-componenten toe te voegen aan je Home- en About-pagina's.

Importeer op de Home page de component `Link` uit de Gatsby-package en voeg een link toe naar je pagina About.

{% code title="src/pages/index.js" %}
```jsx
import * as React from 'react'
import { Link } from 'gatsby'

const IndexPage = () => {
  return (
    <main>
      <title>Home Page</title>
      <h1>Welcome to Inghelbrecht Agency!</h1>
      <Link to="/about">About page</Link>
      <p>Lorem ipsum</p>
    </main>
  )
}

export default IndexPage
```
{% endcode %}

Importeer op de pagina About de component `Link` uit de Gatsby-package en voeg een link toe naar je Home page.

```jsx
import * as React from 'react'
import { Link } from 'gatsby'

const AboutPage = () => {
  return (
    <main>
      <title>About Us</title>
      <h1>About Us</h1>
      <Link to="/">Back to Home</Link>
      <p>Artist Agency was founded in 1977 by founder, John Doe. AA continues to be at the forefront of art by establishing the careers of our talents on a holistic level -- and setting trends within the industry. </p>
    </main>
  )
}

export default AboutPage
```

Klik in je webbrowser op elk van de links om te controleren of ze correct werken.

![](<../../.gitbook/assets/image (47) (1).png>)

![](<../../.gitbook/assets/image (83).png>)
