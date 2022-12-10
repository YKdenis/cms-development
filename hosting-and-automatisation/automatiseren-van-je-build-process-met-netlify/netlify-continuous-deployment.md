---
description: >-
  In deze les zal je een Netlify account aanmaken en je website online zetten
  met behulp van continuous deployment via Github.
---

# Netlify - Continuous Deployment

## Continuous Deployment met Netlify

Door continuous deployment toe te voegen aan je website zal er bij elke nieuwe commit van je lokale werkomgeving naar je Github repo een nieuwe build worden gestart op Netlify. M.a.w. Netlify zal luisteren naar aanpassingen in je Github repo en telkens als er een nieuwe aanpassing plaatsvindt, je website opnieuw binnenhalen en opbouwen.

Aldus er voor zorgen dat je website up to date is met de laatste broncode die in je Github repo leeft. Je hoeft niet meer bij elke aanpassing je website manueel te deployen, in plaats daarvan kan je pushen vanuit je terminal naar je repo en een automatisch build proces initialiseren!

Hieronder vind je meer uitleg over hoe je continuous deployment opzet voor Gatsby met Netlify. :muscle:

### Maak een Netlify Account aan

Navigeer naar [https://app.netlify.com/](https://app.netlify.com/) en login via Github of maak een nieuw account door op Email te klikken.

![](<../../.gitbook/assets/image (109).png>)

Bij het aanmaken van een Netlify account zullen er verschillende vragen worden gesteld omtrent de rede waarvoor je Netlify wilt gebruiken. Vul dit voor jezelf in.

In het volgende scherm krijg je een Quickstart Guide te zien. Doorloop en lees de drie stappen.

![](<../../.gitbook/assets/image (90).png>)

Eenmaal als je de drie stappen hebt doorlopen krijg je een overzicht te zien van je Netlify dashboard. Momenteel staat er nog niets op aangezien je nog geen website hebt toegevoegd!

![](<../../.gitbook/assets/image (86).png>)

In de navigatiebalk bovenaan klik je op Sites.&#x20;

![](<../../.gitbook/assets/image (4).png>)

Zoals eerder vermeld is je site dashboard nog leeg. Klik op de knop **New site from Git** om een nieuwe website te initialiseren.

![](<../../.gitbook/assets/image (84).png>)

### Verbind met een Git-provider

Netlify zal vragen met welke Git Provider je graag zou willen koppelen. Je hebt de keuze tussen Github, Gitlab en Bitbucket. Kies Github als Git-provider aangezien je broncode van je site op Github wordt gehost.

![](<../../.gitbook/assets/image (30).png>)

### Kies een repositiory

Github zal je vragen om in te loggen en vervolgens een lijst van al je repositories tonen. Kies de repo met de broncode van je artist-agency.

![](<../../.gitbook/assets/image (22).png>)

{% hint style="info" %}
Als je de artist agency repository niet in de lijst ziet staan dan zal je de configuratie van Netlify op je Github account moeten aanpassen. Onderaan je webpagina staat er een link, klik erop om je Netlify configuratie op Github aan te passen.&#x20;
{% endhint %}

![](<../../.gitbook/assets/image (43).png>)

{% hint style="info" %}
Scroll naar beneden op de configuratie pagina van Github tot aan Repository access. Geef Netlify access tot al je repositories of selecteer de repo van je artist agency zoals hieronder weergegeven.

Als je terug navigeert naar je de '**Create new site**' webpagina zou je de repository moeten zien staan!
{% endhint %}

![](<../../.gitbook/assets/image (9).png>)

### Site settings en deploy! :rocket:

Vooralleer je de artist agency website deployed wordt er gevraagd of je de default settings wilt aanpassen. Let er op dat je de correcte branch kiest (normaliter is dit **main** of **master**). Je mag de default settings laten staan en op **deploy site** klikken.

![](<../../.gitbook/assets/image (1).png>)

Je website zal worden gedeployed op een random domeinnaam gegenereerd door Netlify. Het duurt een vijftal minuten om je website te builden en beschikbaar te stellen via de Netlify domeinnaam.

![](<../../.gitbook/assets/image (182).png>)

![](<../../.gitbook/assets/image (16).png>)

Als alles goed is verlopen staat je website online. Proficiat! :tada:

{% hint style="warning" %}
Het kan zijn dat je build faalt. In dat geval is er waarschijnlijk iets mis met je gatsby project. Om lokaal je build te testen kan je gebruik maken van de commands [gatsby build](https://www.gatsbyjs.com/docs/reference/gatsby-cli/#build) en [gatsby serve](https://www.gatsbyjs.com/docs/reference/gatsby-cli/#build).
{% endhint %}

### Conclusie

Netlify zal luisteren naar nieuwe aanpassingen op je Github repo. Telkens als je een nieuwe commit pusht naar de artist agency repo zal er een nieuwe build worden geïnitialiseerd op Netlify. Als gevolg zal je website altijd up to date zijn met de laatste wijzigingen!

{% hint style="info" %}
**Let op** :eyes:**:** Alleen wijzigingen in je Gatsby project zullen een nieuwe build starten. Wijzigingen in je WP applicatie nog niet! Hiervoor moet je een build webhook gebruiken. Meer omtrent build webhooks in het volgende hoofdstuk. :thumbsup:
{% endhint %}
