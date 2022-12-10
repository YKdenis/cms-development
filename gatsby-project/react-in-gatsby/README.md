---
description: >-
  In het vorige deel van de zelfstudie begon je met je eerste Gatsby-site. Nu je
  alles hebt ingesteld, is het tijd om deze site je eigen te maken.
---

# De React library 🗂 in Gatsby

## Overzicht

Om de basispaginastructuur voor je artist agency op te bouwen, moet je weten wat **React-componenten** zijn en hoe Gatsby ze gebruikt.

#### Aan het einde van dit deel ben je in staat om:

1. nieuwe **page components** aan te maken en toe te voegen aan je site;
2. Importeren en gebruiken van een kant-en-klaar component uit een andere package;
3. Het maken van je eigen herbruikbare "**building block**" -component;
4. Gebruik van [React props](https://reactjs.org/docs/components-and-props.html) om de manier waarop een component wordt weergegeven te manipuleren;
5. Gebruik van de **children prop** om een **wrapper component** te maken;

### Wat is React?

React is de JavaScript-bibliotheek die Gatsby onder de motorkap gebruikt om gebruikersinterfaces (UI's) te maken. Met React kun je je gebruikersinterface opsplitsen in kleinere, herbruikbare stukjes die componenten (**components**) worden genoemd.

Stel je bijvoorbeeld de gebruikersinterface voor van een product van een online winkel:

![](<../../.gitbook/assets/image (134).png>)

Om deze pagina in React te bouwen, heb je mogelijk een **navigatie component** voor het navigatiemenu, een **zijbalk component** voor extra informatie die aan de zijkant van de hoofdinhoud wordt weergegeven, en een **productlijst component** om alle producten weer te geven voor uitverkoop.

Je kan ook componenten maken van andere componenten. Je kan bijvoorbeeld besluiten om het **productlijst component** op te splitsen in een lijst van meerdere **product componenten**, die elk de details over een enkel product weergeven. Dit patroon wordt **composition** genoemd, grotere componenten die zijn samengesteld uit kleinere componenten.
