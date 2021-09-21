---
description: >-
  Leer hoe je GraphiQL gebruikt in Gatbsy om de Data Layer te verkennen en
  GraphQL-query's te schrijven
---

# GraphiQL in Gatbsy

Hoe weet je welke gegevens zich in de GraphQL Data Layer van je site bevinden? Wanneer je de lokale ontwikkelingsserver voor je site start, maakt Gatsby automatisch een speciaal eindpunt aan waarmee je een in-browser tool genaamd **GraphiQL** kan gebruiken. 

{% hint style="info" %}
Net zoals met de GraphiQL interface in je WordPress Applicatie kan je de gegevens van je site verkennen en GraphQL-query's maken.
{% endhint %}

#### Volg de onderstaande stappen om de GraphiQL-interface in Gatsby te openen:

* Start je lokale ontwikkelingsserver op door `gatsby develop` uit te voeren in je terminal.
* Ga in een webbrowser naar [http://localhost:8000/\_\_\_graphql](http://localhost:8000/___graphql). \(Dat zijn drie underscores in de URL.\)

![GraphiQL interface in Gatbsy](../../.gitbook/assets/image%20%2879%29.png)

{% hint style="info" %}
**De GraphiQL IDE in Gatsby werkt hetzelfde als de GraphiQL IDE in WordPress**. Bekijk onderstaande link om je kennis op te frissen.
{% endhint %}

{% page-ref page="../../api-graphql/wpgraphql/graphiql-ide.md" %}

**GraphiQL is een handig hulpmiddel voor het testen van je GraphQL-query's voordat je ze aan je code toevoegt**. Op die manier kan je ervoor zorgen dat je queries altijd  de correcte gegevens retourneren.

#### Probeer een paar query's te maken en uit te voeren door het volgende te doen:

Vink enkele van de blauwe velden in het Explorer-venster aan. Merk op hoe het aanvinken van het vakje voor een veld, het toevoegt aan de query in het **Query document**.

Klik op de knop bovenaan de pagina \(die eruitziet als een "afspeel"-knop\) om de zoekopdracht uit te voeren. Bekijk de gegevens die worden geretourneerd in het **Result veld**.

In het volgende gedeelte leer je meer over het gebruik van specifieke velden. Neem voor nu een tiental minuten de tijd om de verschillende velden te verkennen. Welke soorten data zijn al voor je beschikbaar in de Data Layer?

