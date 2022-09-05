---
description: >-
  In dit deel zal je leren hoe je de Data Layer van Gatsby gebruikt om data met
  behulp van GraphQL op te halen.
---

# Query Data met GraphQL

## Introductie 

Tot nu toe heb je tekst geschreven en afbeeldingen rechtstreeks in je React-componenten toegevoegd. Dat is een uitstekende manier om veel websites te bouwen! Maar vaak is het gemakkelijker om gegevens ergens anders aan te maken en te onderhouden - zoals een map met Markdown-bestanden of een contentmanagementsysteem (CMS) - en deze vervolgens naar behoefte in je componenten op te nemen. Op die manier kan je je inhoud bijwerken zonder de code voor je site te beïnvloeden.

Handig is dat Gatsby een krachtige feature heeft, de **Data Layer** genaamd, die je kan gebruiken om van overal gegevens naar je site door te sluizen. Wil je blogposts in WordPress, je winkelproducten in Shopify en je gebruikersgegevens in Airtable bewaren? Geen probleem! Met de **Data Layer** van Gatsby kan je data uit meerdere bronnen combineren, waardoor je voor elk type data het beste platform kunt kiezen.

{% hint style="info" %}
De **Data Layer** van Gatsby wordt aangedreven door een technologie genaamd GraphQL. **GraphQL is een querytaal met een speciale syntax waarmee je kan vragen om de gegevens die je in een component nodig hebt.**

In deze zelfstudie leer je alles over GraphQL dat je moet weten om je eerste Gatsby-site te bouwen. Geïnteresseerd om meer te leren? [How To GraphQL](https://www.howtographql.com) is een gratis tutorial die je de basis leert.
{% endhint %}

In dit deel leer je hoe je gegevens aan de Data Layer van Gatsby kan toevoegen en hoe je die gegevens in je React-componenten kan opnemen.

#### Aan het einde van dit deel ben je in staat om:

* **GraphiQL **te gebruiken om de gegevens in de Data Layer te verkennen en je eigen GraphQL-query's te bouwen. 
* Een `useStaticQuery`-hook te gebruiken om gegevens naar een "building block" -component te trekken. 
* De `gatsby-source-filesystem` plugin gebruiken om gegevens vanuit het bestandssysteem van je computer naar je site te halen. 
* Een Page Query te maken om gegevens in een page component op te halen.
