# GraphQL Resources

## Hoe werkt een GraphQL API?

In de praktijk is een GraphQL API georganiseerd rond drie hoofdbouwstenen: 

1. Het schema;
2. De queries en mutaties;
3. de resolvers;

Heel simpel uitgelegd** omschrijft het schema de gehele structuur van de GraphQL API**. Welke gegevens je kan opvragen en hoe je ze kan opvragen.

Queries zijn **stukjes omschrijvende code waarmee je data kan opvragen**. In GraphQL volgen queries de structuur van het schema.

Mutaties daarentegen zijn **stukjes code waarmee je data kan wegschrijven, aanpassen of verwijderen**. Dit valt buiten de scope van de cursus en zal niet worden gevraagd op het examen.

Resolvers zijn functies die in de backend gaan bepalen hoe de data uit de databank wordt opgehaald. Wij gaan ons niet bezig houden met het schrijven van resolvers. Dit zal automatisch voor ons worden uitgevoerd door het gebruik van plugins. 

### Officiële documentatie

De officiële GraphQL documentatie is een goede plek om te beginnen met GraphQL. Je zal er de basis principes van GraphQL leren en de GraphQL-syntax onder de knie krijgen.

{% embed url="https://graphql.org/learn/" %}

Doorloop het **introductie** gedeelte en **Queries and Mutations**. 

#### Het is belangrijk dat je alle onderstaande concepten begrijpt vooraleer je begint aan WPGraphQL in het volgende hoofdstuk!

* Fields
* Arguments
* Aliases
* Fragments
* Operation Names
* Variables
* Directives
* ~~Mutations~~ (valt buiten de scope van de cursus)
* Inline fragments

#### Extra resources

{% embed url="https://www.wpgraphql.com/docs/intro-to-graphql/" %}
