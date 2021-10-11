---
description: >-
  In dit deel van de zelfstudie gebruik je de dynamische component GatsbyImage
  om afbeeldingen toe te voegen aan elk van je artiesten.
---

# Toevoegen van dynamische afbeeldingen

## Introductie

In het deel Gatsby Plugins heb je `gatsby-plugin-image` gebruikt om statische afbeeldingen aan je home page toe te voegen. Nu je wat meer met de Data Layer van Gatsby hebt gewerkt, is het tijd om `gatsby-plugin-image` opnieuw te bekijken. Deze keer leer je hoe je dynamische afbeeldingen aan je site kan toevoegen.

#### Aan het einde van dit deel van de zelfstudie ben je in staat om:

* De component `GatsbyImage` te gebruiken om dynamisch afbeeldingen te maken.

### Herhaling `StaticImage`

Wanneer je je site bouwt, laadt de `StaticImage`-component de afbeelding van je bestandssysteem of van de externe URL, en genereert het alle formaten en dimensies die je nodig hebt om een responsieve afbeelding te ondersteunen.

Omdat de afbeelding tijdens het bouwen wordt geladen, kan je de bestandsnaam niet als een `prop` doorgeven of deze op een andere manier buiten de component genereren. Het moet een statische tekenreeks zijn of een lokale variabele in het bereik van de component.

{% hint style="info" %}
Met andere woorden `StaticImage` kan niet worden gebruikt in een page query voor een page component aangezien deze buiten de component wordt gedefinieerd!

**Belangrijk:** Externe afbeeldingen worden tijdens het bouwen gedownload en vergroot of verkleind. Als de afbeelding op je WP applicatie wordt gewijzigd, wordt deze pas op je site bijgewerkt nadat je deze opnieuw hebt opgebouwd.
{% endhint %}

### Wat is het verschil tussen `GatsbyImage` en `StaticImage`?

In het deel Gatsby Plugins heb je geleerd hoe je de `StaticImage`-component van `gatsby-plugin-image` kunt gebruiken.

Maar hoe weet je of je de `StaticImage`-component of de `GatsbyImage`-component moet gebruiken? **De beslissing komt er uiteindelijk op neer of je afbeeldingsbron al dan niet hetzelfde zal zijn elke keer dat de component wordt weergegeven.**

* De `StaticImage`-component is bedoeld voor statische afbeeldingsbron, zoals een hardgecodeerd bestandsroute of externe URL. **Met andere woorden, de bron voor je afbeelding zal altijd hetzelfde zijn elke keer dat de component wordt weergegeven.**
* De component `GatsbyImage` is voor dynamische afbeeldingsbronnen, bijvoorbeeld als de afbeeldingsbron als een `prop` wordt doorgegeven. 

#### Hier is een snelle analogie om het verschil te illustreren:

* Het gebruik van de `StaticImage`-component is als het vragen om een ​​routebeschrijving met behulp van een fysiek adres, zoals "400 Main Street". Je komt altijd op dezelfde plek uit, hoeveel mensen je ook vraagt. 
* Het gebruik van de `GatsbyImage`-component is als vragen om een ​​algemenere weg. Als je iemand vraagt ​​om je naar de beste koffiebar in de stad te verwijzen, hangt het af van aan wie je het vraagt ​​en wat hun persoonlijke voorkeuren zijn.

![](<../../.gitbook/assets/image (144).png>)

In dit deel van de zelfstudie voeg je een profiel foto toe aan je Artist Template Page. Aangezien de afbeeldingsbron die je in de page template laadt, voor elke artiest verandert, gebruik je de `GatsbyImage`-component.
