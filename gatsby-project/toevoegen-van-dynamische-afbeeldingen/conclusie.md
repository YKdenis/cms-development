---
description: >-
  Gefeliciteerd, je hebt het einde van het deel Toevoegen van dynamische
  afbeeldingen behaald! 🥳Neem even de tijd om terug te denken aan wat je tot nu
  toe hebt geleerd.
---

# Conclusie

## Daag jezelf uit om de volgende vragen uit het hoofd te beantwoorden:

* Wanneer moet je de component `GatsbyImage` gebruiken in plaats van de component `StaticImage`?
* Hoe haal je een **dynamische foto** in de Graphiql van Gatsby?

{% hint style="info" %}
#### Deploy it! 🚀

Implementeer voordat je verder gaat je wijzigingen op je GitHub Repo, zodat je je voortgang niet kwijtspeelt!

Voer eerst de volgende opdrachten uit in een terminal om je wijzigingen naar je GitHub-repository te pushen. (Zorg ervoor dat je zich in de directory op het hoogste niveau van je Gatsby-site bevindt!)
{% endhint %}

```
git add .
git commit -m "Toevoegen van dynamische afbeeldingen finished"
git push origin main
```

### Belangrijkste leerpunten

* Gebruik de `StaticImage`-component als je component altijd dezelfde afbeelding weergeeft (van een relatief pad of een externe URL).&#x20;
  * Weergeven van een foto met behulp van **een relatief pad (lokale foto) of een url (externe foto)** doe je met het `StaticImage` component;
* Gebruik de `GatsbyImage`-component als de afbeeldingsbron verandert voor verschillende instanties van je component (**als deze wordt doorgegeven als een prop**).
  * Weergeven van een **dynamische** foto (**opgehaald uit een query**) doe je met het `GatsbyImage` component;
* Gebruik `childImageSharp` en `gatsbyImageData` voor het dynamisch ophalen van een foto met GraphQL in Gatsby.

### Extra resources 📚

{% embed url="https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-plugin-image#restrictions-on-using-staticimage" %}

### Wat nu? 🤔

Je hebt alles dat je nodig hebt om de agency website verder af te werken! De home page, about page en artist page data moet worden binnengehaald, weergegeven en worden gestyled. Vervolgens moet de artist template page gestyled worden en tenslotte moet je een page component aanmaken voor de Contact page en daarvoor de data ophalen, weergeven en stylen.

Je hebt alle tools en informatie gekregen om hiermee verder aan de slag te gaan:

* Je begrijpt het verschil tussen **Building block componenten** en **Page componenten**;
* Je weet hoe je **WordPress data** opvraagt vanuit de **Data Layer**;
* Je begrijpt hoe je **CSS modules** kan toepassen om je JSX te stylen;
* Je kan queries uittesten in **GraphiQL**;
* Je kan de `useStaticQuery` hook gebruiken in Building block componenten;
* Je kan **page queries** schrijven in je **Page componenten**;
* Je kan de **Link component** gebruiken van Gatsby om te navigeren tussen pagina's;
* Je kan de `StaticImage`- en `GatsbyImage`-component van `gatsby-plugin-image` gebruiken voor afbeeldingen weer te geven;
