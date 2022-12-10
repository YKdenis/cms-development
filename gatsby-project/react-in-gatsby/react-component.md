---
description: Herhaling van de React library
---

# Wat is een React Component?(Herhaling)

## Wat is een React-component?

Onder de motorkap is een React-component een functie die een React-element retourneert. **Een React-element is een object dat React gebruikt om DOM-elementen weer te geven**.

![](<../../.gitbook/assets/image (102).png>)

{% hint style="danger" %}
**ALLE** code voorbeelden in dit hoofdstuk voeg je niet toe aan je artist-agency project. Het dient puur als herhaling. :)
{% endhint %}

De eenvoudigste manier om React-elementen te schrijven is met JSX. **JSX is een JavaScript-syntax extensie** die de DOM-structuur voor je component beschrijft. Het lijkt een beetje op HTML in je JavaScript-bestanden:

```jsx
const hello = <h1>Hello world!</h1>
```

Dus een eenvoudige React-component kan er ongeveer zo uitzien:

```jsx
const Greeting = () => {
  return (
    <h1>Hello world!</h1>
  )
}
```

### Wat zijn props in React?&#x20;

We gebruiken `props` in React om gegevens van de ene component naar de andere (van een bovenliggende component naar een onderliggende component(en)) door te geven. Props is slechts een kortere manier om properties te zeggen, wat in het Nederlands eigenschappen betekent. Ze zijn handig wanneer je wilt dat de gegevensstroom in je app dynamisch is!

Laten we als voorbeeld een Nav.js-component aanmaken die er als volgt uitziet:

```jsx
function Nav() {
  return (
    <nav className="Nav">
      
    </nav>
  )
}

export default Nav
```

Vervolgens zullen we een component menuItem importeren in onze Nav-component:

```jsx
import menuItem from "./menuItem"

function Nav() {
  return (
    <nav className="Nav">
      
    </nav>
  )
}

export default Nav
```

Met `props` kan je de logica van een component dynamisch hergebruiken. Dit betekent dat de gegevens in de component niet statisch zijn. Dus voor elk ander component dat die logica gebruikt, kunnen de gegevens worden aangepast om aan de vereisten te voldoen.

Om `props` te gebruiken, moet je `props` doorgeven als argument in je functie component. Dit is vergelijkbaar met het doorgeven van argumenten aan je normale JavaScript-functies. Hier is een voorbeeld:

```jsx
function menuItem(props) {
  const text = props.text;
  const link = props.link;
    return (
        <a href={link}>{text}</a>
    );
}

export default menuItem
```

We zijn klaar met het gebruiken van onze `props`, dus de volgende stap is om het component menuItem te gebruiken in het Nav-component en de gegevens daaraan door te geven. Je geeft de gegevens (`link` en `text`) net zoals attributen door in HTML. Het ziet er zo uit:

```jsx
import menuItem from "./menuItem"

function Nav() {
  return (
    <nav className="Nav">
      <menuItem link="/home" text="Home"/>
    </nav>
  )
}

export default Nav
```

Je kan dynamisch gegevens maken voor elk component met behulp van de logica die is gedefinieerd is in het component menuItem. Je kan menuItem meerdere keren oproepen in het Nav-component en telkens andere waardes opgeven voor `link` en `text`:

```jsx
import menuItem from "./menuItem"

function Nav() {
  return (
    <nav className="Nav">
      <menuItem link="/home" text="Home"/>
      <menuItem link="/contact-us" text="Contact Us"/>
      <menuItem link="/about-us" text="About Us"/>
    </nav>
  )
}

export default Nav
```

{% hint style="info" %}
In het volgende hoofdstuk zullen we dieper ingaan op het gebruik van React in Gatsby.&#x20;
{% endhint %}
