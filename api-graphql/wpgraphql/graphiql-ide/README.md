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

![](<../../../.gitbook/assets/image (81) (1).png>)

Als je navigeert naar je graphQL endpoint krijg je bovenstaande error te zien. Je krijgt een error omdat je geen query hebt meegegeven tijdens het aanroepen van het GraphQL endpoint. **Als je deze error te zien krijgt dan is je GraphQL installatie correct ingesteld** en kan je beginnen met het schrijven en uittesten van queries in de GraphiQL IDE.

Indien je een andere error te zien krijgt, bekijk dan zeker eens of je bij je custom post type en custom taxonomy de velden `graphql_plural_name` en `graphql_single_name` hebt voorzien!

## GraphiQL interface

Als je navigeert naar de GraphiQL IDE in je WP dashboard krijg je het onderstaande scherm te zien.

<figure><img src="../../../.gitbook/assets/image (210).png" alt=""><figcaption></figcaption></figure>

De grafische user interface van Graphiql bestaat uit **5 belangrijke componenten**:

1. De Query Composer;
2. Het Query Document;
3. Het return veld;
4. De Query Variables;
5. De Docs;

### Query Operations

Als we gegevens van onze API willen opvragen, gebruiken we een query. Als voorbeeld zullen we alle pagina's van onze WP installatie opvragen met hun `title` en `uri`.

<figure><img src="../../../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

Het middelste veld is het **query document**, hier schrijf je de query uit. Als je vervolgens bovenaan op de "**play**" knop drukt zal er in de rechter kolom de return waarde worden weergegeven. De rechter kolom is het **return veld.**

<figure><img src="../../../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>

Wanneer je een query verzendt, krijg je een **JSON-response** waarvan de structuur gebaseerd is op de geneste structuur van je query. Als je bijvoorbeeld een query voor pages verzendt en de `uri` en `title` opvraagt, zal je een JSON-response ontvangen met daarin een array genaamd `edges` dat objecten bevat met een key waarde `node` waarin een `title` en `uri` zitten, zoals hier boven wordt aangetoond.

{% hint style="info" %}
Wat edges en nodes zijn wordt verduidelijkt in [het hoofdstuk over de **Application Data Graph**](../../graphql/application-data-graph.md). Het belangrijkste dat je hiervan moet onthouden is dat **de JSON-response de query structuur volgt**.
{% endhint %}

## Resources

{% embed url="https://www.wpgraphql.com/docs/quick-start/" %}
