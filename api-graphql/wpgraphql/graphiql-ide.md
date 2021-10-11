---
description: >-
  Met de GraphiQL IDE kan jet het GraphQL schema, opgezet door de WPgraphQL
  plugin, gemakkelijk verkennen.
---

# De GraphiQL IDE - Breakdown

## GraphQL Endpoint

Het schrijven en uittesten van queries is super gemakkelijk aan de hand van de GraphiQL. Samen zullen we de GraphQL IDE gebruiken om de basis kennis van GraphQL te overlopen en een gevoel voor het schrijven van GraphQL-syntax te ontwikkelen.

Vooraleer je kan beginnen met het uittesten van queries moet je GraphQL endpoint correct zijn ingesteld. Navigeer naar [https://yourdomain.com/graphql](https://yourdomain.com/graphql).

{% hint style="info" %}
Verander "**yourdomain.com**" met de de domeinnaam van je lokale WP installatie.
{% endhint %}

![](<../../.gitbook/assets/image (81).png>)

Als je navigeert naar je graphQL endpoint krijg je bovenstaande error te zien. Je krijgt een error omdat je geen query hebt meegegeven tijdens het aanroepen van het GraphQL endpoint. **Als je deze error te zien krijgt dan is je GraphQL installatie correct ingesteld** en kan je beginnen met het schrijven en uittesten van queries in de GraphiQL IDE.

Indien je een andere error te zien krijgt, bekijk dan zeker eens of je bij je custom post type en custom taxonomy de velden `graphql_plural_name` en `graphql_single_name` hebt voorzien!

## GraphiQL interface

Als je navigeert naar de GraphiQL IDE in je WP dashboard krijg je het onderstaande scherm te zien.

![](<../../.gitbook/assets/image (99).png>)

De grafische user interface van Graphiql bestaat uit **5 belangrijke componenten**:

1. De Explorer;
2. Het query document;
3. Het return veld;
4. De query variables;
5. De docs;

### Query Operations

Als we gegevens van onze API willen opvragen, gebruiken we een query. Als voorbeeld zullen we alle pagina's van onze WP installatie opvragen met hun `title` en `uri`.

![](<../../.gitbook/assets/image (149).png>)

Het middelste veld is het **query document**, hier schrijf je de query uit. Als je vervolgens bovenaan op de "**play**" knop drukt zal er in de rechter kolom de return waarde worden weergegeven. De rechter kolom is het **return veld.**

![](<../../.gitbook/assets/image (8).png>)

Wanneer je een query verzendt, krijg je een **JSON-response** waarvan de structuur gebaseerd is op de geneste structuur van je query. Als je bijvoorbeeld een query voor pages verzendt en de `uri` en `title` opvraagt, zal je een JSON-response ontvangen met daarin een array genaamd `edges` dat objecten bevat met een key waarde `node` waarin een `title` en `uri` zitten, zoals hier boven wordt aangetoond.

{% hint style="info" %}
Wat edges en nodes zijn wordt verduidelijkt in [het hoofdstuk over de **Application Data Graph**](../graphql/application-data-graph.md). Het belangrijkste dat je hiervan moet onthouden is dat **de JSON-response de query structuur volgt**.
{% endhint %}

### Query Document

Een "**Query**" **\*\*wordt de **Operation Name\*\* genoemd. Dit beschrijft welk type query of bewerking er naar de GraphQL-service wordt verzonden.

{% hint style="info" %}
Bekijk de GraphQL documentatie, [Queries and Mutations](https://graphql.org/learn/queries/).
{% endhint %}

Je kan meerdere query's aan een **query document** toevoegen. Je kan bijvoorbeeld twee query operations in een query document plaatsen:

![](<../../.gitbook/assets/image (21).png>)

Als je meer dan één query in een query document hebt, moet je de query een operation name geven. **Denk aan een operation name als een function name**. In dit geval "`OtherQuery`" en "`MyQuery`".

Als je op de afspeelknop klikt, verschijnt er een vervolgkeuzelijst waarin je wordt gevraagd een van deze twee bewerkingen te selecteren.

![](<../../.gitbook/assets/image (16).png>)

Als je voor al deze gegevens één verzoek wilt verzenden, kan je ze allemaal in dezelfde query plaatsen:

![](<../../.gitbook/assets/image (22).png>)

### GraphiQL Explorer

Je kan de Explorer raadplegen in de kolom helemaal links. In de Explorer staan alle queries vermeld die WPGraphQL out of the box voor ons voorziet.

Je kan op de dropdownmenu's doorklikken en je zal zien dat er automatisch een query gegenereerd wordt in het query document. **Je kan gemakkelijk het GraphQL schema dat WPGraphQL voor ons heeft opgezet verkennen.** Per niveau dat je dieper gaat in de Explorer zal er een geneste query gegenereerd worden. De query hieronder is volledig opgesteld doormiddel van de Explorer:

![](<../../.gitbook/assets/image (141).png>)

### Query Variables

In de GraphiQL IDE kan je **query variabelen** meegeven om je queries generiek te maken. Variabelen moeten gedefinieerd worden van boven bij de operatie naam a.d.h.v. van **een dollar-teken**. Je definieert wat voor soort type je variabele is. In het voorbeeld hieronder is dat "`ID`" wat voor identifier staat. Het **uitroepteken(!)** laat weten aan GraphQL dat we strikt een integer verwachten een geen ander type zoals bv. een string.

Onderstaande query zal een artist ophalen a.d.h.v. een slug. Een slug is het laatste deel van een URL.

![](<../../.gitbook/assets/image (1).png>)

Bij de **operation name "**`MyQuery`**"** geef je een variabele mee genaamd `$slug` _\*\*_en laat je graphQL weten dat het een `ID` verwacht. Vervolgens gebruik je de slug in de artist query als `id` argument (`id: $slug`). Het argument `idType` zetten we op `SLUG`, zo weet GraphQL dat we een artist willen opvragen m.b.v. een slug.

![](<../../.gitbook/assets/image (54).png>)

Ten slotte kan je in het veld **Query Variables** een JSON-geformatteerd object meegeven waarin je de variabele "`slug`" definieert.

![](<../../.gitbook/assets/image (59).png>)

Als je de query nu uitvoert zal je dit als response krijgen:

![](<../../.gitbook/assets/image (116).png>)

Indien we de query willen hergebruiken en een andere artist willen opvragen dan kan dat gemakkelijk door de "`slug`" in ons JSON-object aan te passen naar een andere waarde. We hebben een **generieke/herbruikbare** **query** gedefinieerd!

### Docs

in de rechter bovenhoek kan je de Documentatie van je schema raadplegen.

![](<../../.gitbook/assets/image (28).png>)

Dit is interessant als je meer wilt weten over de verschillende argumenten en types in je schema en hoe deze aan elkaar gelinkt zijn.

![](<../../.gitbook/assets/image (57).png>)

## Resources

{% embed url="https://www.wpgraphql.com/docs/quick-start/" %}
