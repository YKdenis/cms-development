---
description: >-
  Een build webhook is een unieke URL die, wanneer aangeroepen, een build
  initialiseren.
---

# GatsbyJS - Build Webhook

## WordPress build webhook voor Gatsby

In het vorige hoofdstuk heb je een link gelegd tussen je Github repo en Netlify account. Bij elke commit naar je Github repo zal er een nieuwe build worden geïnitialiseerd. Je website zal met andere woorden altijd up to date zijn met de laatste code wijzigingen in je front-end.

Wat nu met wijzigingen op je WordPress applicatie? hoe kan je er voor zorgen dat de aanpassingen, die jij of je klant uitvoeren, automatisch worden gereflecteerd op je website?

Hiervoor kan je een build webhook gebruiken. Build webhooks zijn unieke URLs die, wanneer aangeroepen, een nieuwe build initialiseren. Met een build webhook kan je er dus voor zorgen dat bij elke aanpassing in je WP applicatie er gepingd wordt naar Netlify die op zijn beurt een nieuwe build start.

### Netlify Build Webhook aanmaken

Begin met het aanmaken van een build webhook voor je artist-agency website op Netlify. Navigeer naar je artist agency site overview op Netlify en klik op **site settings**.

![](<../../.gitbook/assets/image (48).png>)

klik vervolgens op **build & deploy** in de aside aan de linkerkant van je scherm.

![](<../../.gitbook/assets/image (30).png>)

Scroll naar beneden tot aan build hooks en druk op de knop **add build hook**. Geef de hook een naam, kies de correcte branch en klik op **Save**.

![](<../../.gitbook/assets/image (15).png>)

Je build webhook is aangemaakt. In de volgende stap zal je deze toepassen in je WordPress applicatie en er voor zorgen dat het wordt aangeroepen bij elke aanpassing die jij of de klant maakt.

### WPGatsby Build Webhook gebruiken

Ten slotte moet je de build hook toevoegen aan je WP applicatie. Dit kan je doen door gebruik te maken van de GatsbyJS plugin die je eerder hebt geïnstalleerd. Navigeer naar GatsbyJS onder je Settings in je WordPress admin paneel.

{% hint style="warning" %}
**Let op** :eyes::  Je gatsby front-end project is nu gekoppeld met je gehoste WordPress applicatie. Let er op dat je de build webhook toevoegt aan je gehoste WP applicatie en niet aan die in Local by Flywheel!
{% endhint %}

![](<../../.gitbook/assets/image (2).png>)

Het eerste veld op de GatsbyJS settings pagina is voor het instellen van een build webhook. Kopieer hier de build hook URL vanuit Netlify en klik vervolgens helemaal vanonder aan de pagina op **Save**.

![](<../../.gitbook/assets/image (6).png>)

Proficiat je build webhook is correct ingesteld! :tada:

### Conclusie

Pas de data van een van je artiesten aan. Normaliter, na een aantal minuten, zal er een build worden geïnitialiseerd op Netlify.

![](<../../.gitbook/assets/image (65).png>)

Zowel je Github repo als je WP applicatie zijn nu automatisch gekoppeld aan je Netlify hosting. Aanpassingen op beide platformen worden automatisch gereflecteerd op je gehoste website te Netlify!
