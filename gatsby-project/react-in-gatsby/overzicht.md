---
description: >-
  Gefeliciteerd, je hebt het einde van het deel React in Gatsby gehaald! 🥳Neem
  even de tijd om terug te denken aan wat je tot nu toe hebt geleerd.
---

# Conclusie

## Daag jezelf uit om de volgende vragen uit het hoofd te beantwoorden:

* Wat is het verschil tussen een page component en een Building block component?
* Hoe voeg je een nieuwe pagina toe aan je Gatsby-site?
* Wat zijn de stappen voor het schrijven van een nieuwe React-component? 
* Wat zijn `props` en wanneer kun je ze gebruiken? 
* Wat is de `children` prop en waarom is het nuttig?

{% hint style="info" %}
### Commit it! 🚀

Implementeer voordat je verder gaat je wijzigingen op je GitHub-repo, zodat je je voortgang niet kwijtspeelt!

Voer eerst de volgende opdrachten uit in een terminal om je wijzigingen naar je GitHub-repository te pushen. (Zorg ervoor dat je je in de directory op het hoogste niveau van je Gatsby-site bevindt!)
{% endhint %}

```bash
git add .
git commit -m "Finished React in Gatsby"
git push origin main
```

## Belangrijkste leerpunten

* **React is een bibliotheek** die je helpt je ​​gebruikersinterface op te splitsen in kleinere stukjes die componenten worden genoemd. **Een component is een functie die een React-element retourneert**. React-elementen kunnen in **JSX** worden geschreven.
* **Page componenten** bevatten alle UI-elementen voor een specifieke pagina van je site. Gatsby maakt automatisch pagina's aan voor componenten die de standaard export zijn van bestanden in de `src/pages` directory. **De naam van het bestand wordt gebruikt als de route voor de pagina.** 
* B**uilding block componenten zijn kleinere herbruikbare onderdelen van je gebruikersinterface**. Ze kunnen worden geïmporteerd in page componenten of andere building block componenten. 
* Je kan kant-en-klare componenten (zoals `Link`) uit andere packages importeren, of je kan je eigen aangepaste componenten helemaal opnieuw schrijven (zoals `Layout`). 
* Je kan `props` gebruiken om de **weergave van een component te wijzigen**. Je kan je eigen `props` definiëren wanneer je een onderdeel bouwt. React heeft ook enkele ingebouwde props, zoals `children` en `className`. 
* Gatsby is niet eigenwijs over welke CSS benadering je wilt gebruiken, maar het **werkt standaard met CSS-modules**.
