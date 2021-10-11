---
description: >-
  Gefeliciteerd, je hebt het einde van het deel Query data met GraphQL behaald!
  🥳Neem even de tijd om terug te denken aan wat je tot nu toe hebt geleerd.
---

# Conclusie

## Daag jezelf uit om de volgende vragen uit het hoofd te beantwoorden:

* Hoe krijg je data in de Data Layer? 
* Hoe kan je zien welke gegevens zich in de Data Layer bevinden? 
* Hoe haal je data uit de Data Layer? 
* Wat zijn de verschillen tussen een page query en `useStaticQuery`? 
* Hoe zou je beslissen welke je wilt gebruiken?

{% hint style="info" %}
#### Deploy it! 🚀

Implementeer voordat je verder gaat je wijzigingen op je GitHub Repo, zodat je je voortgang niet kwijtspeelt!

Voer eerst de volgende opdrachten uit in een terminal om je wijzigingen naar je GitHub-repository te pushen. (Zorg ervoor dat je zich in de directory op het hoogste niveau van je Gatsby-site bevindt!)
{% endhint %}

```
git add .
git commit -m "Query data met GraphQL finished"
git push origin main
```

### Belangrijkste leerpunten

* `source` **plugins** halen gegevens van hun oorspronkelijke locatie naar de Gatsby GraphQL Data Layer.
* Je kan het **GraphiQL eindpunt** ([localhost:8000/\__\_graphql](http://localhost:8000/\__\_graphql)) gebruiken om de gegevens in de Data Layer te verkennen en GraphQL-query's te ontwerpen. 
* Je kan GraphQL-query's schrijven om gegevens uit de Data Layer en in je React-componenten te halen. 
  * Gebruik de `useStaticQuery`**-hook** om gegevens naar een "**Building Block**" -component op te halen. 
  * Gebruik een **page query** om gegevens in een **page component** op te halen.
