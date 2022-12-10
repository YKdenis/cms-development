---
description: >-
  Gatsby heeft zijn eigen GraphQL Data Layer waar alle gegevens voor je site
  worden bewaard. Maar hoe werkt het onder de motorkap?
---

# De GraphQL Data Layer

### Herhaling: Wat is een Application Data Graph

De GraphQL Data Layer in Gatsby is een Application Data Graph.

{% content-ref url="../../api-graphql/graphql/application-data-graph.md" %}
[application-data-graph.md](../../api-graphql/graphql/application-data-graph.md)
{% endcontent-ref %}

## De Data Layer

Ten eerste worden je gegevens opgeslagen in een of meer bronnen. Die bron kan een map op het bestandssysteem van je computer zijn, een contentmanagementsysteem (CMS) zoals WordPress of een database.

Hoe krijg je data van de bron in de **Data Layer**? Door een bepaald type plugin aan je site toe te voegen, een **source plugin** genaamd. Elke **source plugin** is ontworpen om met een specifieke bron te communiceren. Wanneer je een site bouwt, haalt elke **source plugin** gegevens uit zijn specifieke bron en voegt deze toe aan de GraphQL Data Layer van je site.

### Hoe krijg je data terug uit de Data Layer?

Je kan GraphQL-query's in je componenten schrijven om de gegevens eruit te halen die je op je site wilt gebruiken. Wanneer je de commando `gatsby develop` uitvoert, zal Gatsby alle GraphQL-query's in je componenten vinden, uitvoeren en de resulterende gegevens in je component plaatsen.

![](<../../.gitbook/assets/image (42) (1).png>)
