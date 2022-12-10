---
description: >-
  Voor onze agency website zullen we data moeten opvragen a.d.h.v. queries. We
  kunnen deze queries schrijven en uittesten in de GraphIQL IDE van WPGraphQL.
---

# Opdracht WPGraphQL

De queries die je hier zal schrijven zijn bedoelt als oefening om de syntaxis van GraphQL onder de knie te krijgen. Later, eenmaal als je met de front-end begint, zal je deze queries **NIET** kunnen **** toepassen in je front-end.

## Schrijf volgende queries:

{% hint style="info" %}
Bij het ophalen van foto's vraag je alleen naar het veld `sourceUrl`. Dit retourneert de absolute link naar je foto's in je WordPress installatie.&#x20;

Later zullen we met Gatsby foto's op een andere manier ophalen zodat ze automatisch dynamisch en responsief zijn!
{% endhint %}

{% hint style="warning" %}
Kopieer elke **query (niet de return waarde)** naar een aparte **.gql** file en bewaar dit lokaal op je computer.

Vb. voor de contactUsFields query maak je een file genaamd `contactUsFields.gql`
{% endhint %}

Voor deze opdracht mag je gebruik maken van de Query Composer in GraphIQL en de [GraphQL documentatie](https://graphql.org/learn/).

1. Maak een **page** query aan en haal de **contactUsFields** op. Gebruik hiervoor '**uri**' als `idType` en geef de '**contact-us**' als `id` mee. Haal op:
   * title;
   * description;
   * sourceUrl van picture;
   * address;
   * city;
   * zipcode;
   * email;
   * phoneNumber;
   * instagram;
   * twitter;
   * facebook;
2. Maak een **page** query aan en haal de **homeFields** op. Gebruik hiervoor '**uri**' als `idType` en geef de '**home**' als `id` mee. Haal op:
   * title;
   * description;
   * sourceUrl van picture;
   * de firstName en lastName van artists (**gebruik een inline fragment**);&#x20;
   * de title en url van CallToAction;
3. Haal de drie eerste artiesten op met behulp van de **artists** query. Gebruik de parameter **first**. Haal volgende informatie op:
   * firstName;
   * lastName;
   * artistName;
4. Haal de data van één artist op. Gebruik de **artist** query en haal de **artistMeta** data op. Gebruik hiervoor '**slug'** als `idType` en geef '**anna-woznak**' als `id` mee.
   * firstName;
   * lastName;
   * artistName;
   * email;
   * phoneNumber;
   * description
   * origin;
   * height;
   * shoeSize;
   * shirtSize;
   * sourceUrl van profilePicture;
   * name van roles (roles geeft een array terug);
5. Herwerk de query uit stap 2 zodat het een query variabele gebruikt voor de parameter `id`.

{% hint style="info" %}
Aan het einde van je resultaat in je return veld krijg je misschien een debug en/of tracing stack te zien. Je kan deze uitschakelen door naar de GraphQL Settings te navigeren en onderstaande velden uit te vinken. Vergeet niet je wijzigingen op te slaan!
{% endhint %}

![](<../../.gitbook/assets/image (34).png>)

<figure><img src="../../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Vergeet je opdracht niet in te dienen op Digitap. Deze opdracht staat op punten!

**Deadline: 23/10/22 om 23:59**
{% endhint %}
