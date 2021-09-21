---
description: "Gefeliciteerd, je hebt het einde van het deel Programmatisch pagina's maken behaald! \U0001F973Neem even de tijd om terug te denken aan wat je tot nu toe hebt geleerd."
---

# Conclusie

## Daag jezelf uit om de volgende vragen uit het hoofd te beantwoorden:

* Waarvoor wordt de **File System Route API** gebruikt? 
* Wat is de syntax voor het maken van een nieuwe **collection route**? 
* Wat is een **query variabele**? 
* Wanneer zou je een **query variabele** kunnen gebruiken?

{% hint style="info" %}
#### Deploy it! 🚀

Implementeer voordat je verder gaat je wijzigingen op je GitHub Repo, zodat je je voortgang niet kwijtspeelt!

Voer eerst de volgende opdrachten uit in een terminal om je wijzigingen naar je GitHub-repository te pushen. \(Zorg ervoor dat je zich in de directory op het hoogste niveau van je Gatsby-site bevindt!\)
{% endhint %}

```text
git add .
git commit -m "Programmatisch pagina's aanmaken finished"
git push origin main
```

### Belangrijkste leerpunten

* Met de **File System Route API van Gatsby** kan je **dynamisch nieuwe pagina's maken van Data Layer nodes** door je bestanden een speciale syntax te geven. \(bv. `{wpArtist.slug}.js`\)
  * **File System Routes** werken alleen op bestanden in de `src/pages` directory \(of subdirectories\). 
  * Om een nieuwe collection route te maken, geef je je bestand de naam `{nodeType.field}.js`, waarbij **nodeType** het type node is waarvan je pagina's wilt maken en **field** het gegevensveld van de node is dat je wilt gebruiken in de URL voor die pagina. 
  * **Met query variabelen kan je verschillende gegevenswaarden doorgeven aan dezelfde GraphQL-query**. Ze kunnen worden gecombineerd met veldargumenten om alleen gegevens over een specifiek node terug te krijgen.
  * **Query variabelen kunnen alleen worden gebruikt in page queries**.

