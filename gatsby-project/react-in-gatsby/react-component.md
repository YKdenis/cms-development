---
description: Herhaling van de React library
---

# Wat is een React Component?(Herhaling)

### Wat is een React-component? 

Onder de motorkap is een React-component een functie die een React-element retourneert. **Een React-element is een object dat React gebruikt om DOM-elementen weer te geven**.

![](<../../.gitbook/assets/image (102).png>)

De eenvoudigste manier om React-elementen te schrijven is met JSX. **JSX is een JavaScript-syntaxisextensie** die de DOM-structuur voor je component beschrijft. Het lijkt een beetje op HTML in je JavaScript-bestanden:

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

In de volgende sectie zal je meer leren over het maken van React-componenten.
