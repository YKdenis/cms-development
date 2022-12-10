# Query Document

## Query Document

Een "**Query**" wordt de Operation Name genoemd. Dit beschrijft welk type query of bewerking er naar de GraphQL-service wordt verzonden.

{% hint style="info" %}
Bekijk de GraphQL documentatie, [Queries and Mutations](https://graphql.org/learn/queries/).
{% endhint %}

Je kan meerdere query's aan een **query document** toevoegen. Je kan bijvoorbeeld twee query operations in een query document plaatsen:

![](<../../../.gitbook/assets/image (21) (1).png>)

{% hint style="info" %}
In dit voorbeeld wordt '**artistBy**' gebruikt in de query. Dit is een oud voorbeeld en `artistBy` is deprecated!
{% endhint %}

Als je meer dan één query in een query document hebt, moet je de query een operation name geven. **Denk aan een operation name als een function name**. In dit geval "`OtherQuery`" en "`MyQuery`".

Als je op de afspeelknop klikt, verschijnt er een vervolgkeuzelijst waarin je wordt gevraagd een van deze twee bewerkingen te selecteren.

<figure><img src="../../../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>

Als je voor al deze gegevens één verzoek wilt verzenden, kan je ze allemaal in dezelfde query plaatsen:

<figure><img src="../../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

###
