---
description: >-
  WPGraphQL is een gratis, open-source WordPress-plug-in die je WordPress-site
  verandert in een GraphQL API-server.
---

# WP Plugin 🔌: WPGraphQL

## Installeren WPGraphQL

WPGraphQL is een WordPress-plug-in, om WPGraphQL met WordPress te gebruiken, moet deze eerst worden geïnstalleerd en geactiveerd.

Navigeer in je WordPress dashboard naar "**Plugins".** Vervolgens in het submenu daaronder klik je op "**Add New**". Zoek naar de plugin "**WPGraphQL**" en klik op de knop "**Install Now**". Eenmaal als de plugin is geïnstalleerd, zal er op de WPGraphQL tegel een knop "**Activate**" verschijnen. Klik deze aan om er voor te zorgen dat de plugin degelijk wordt gebruikt binnen je WordPress installatie!

![](<../../.gitbook/assets/image (15).png>)

### Installatie WPGraphQL met ACF

Vooraleer we kunnen beginnen met het schrijven en testen van onze GraphQL queries moeten we een plugin installeren dat de custom fields van ACF beschikbaar stelt in WPGraphQL. Met de plugin WPGraphQL voor advanced custom fields zorg je ervoor dat de ACF-velden automatisch worden weergegeven in je WPGraphQL-schema.

#### Github - Plug-in voor downloaden / klonen

WPGraphQL voor ACF is niet beschikbaar via de plugin store van WP zelf. Je moet deze via Github downloaden en manueel installeren.

{% embed url="https://github.com/wp-graphql/wp-graphql-acf" %}

Navigeer naar bovenstaande link, klik op de knop "**Code**" en vervolgens op download ZIP.

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2FrY8pGDoBHt4vWL6qxGBA%2Ffile.png?alt=media)

Om het risico op onbedoeld gedrag te minimaliseren, is het het beste dat je plugin-zipfile "**wp-graphql-acf.zip**" is en niet iets anders, zoals "wp-graphql-acf-master.zip" of "wp-graphql-acf-Develop.zip".

Je kan de plugin installeren via je WordPress dashboard. Navigeer naar plugins, klik op "**New Plugin**" en vervolgens op "**Upload Plugin**".

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2F3h12CNBNrwIsjwlpgjis%2Ffile.png?alt=media)

Upload de plugin, wacht even tot dat het installatie proces is afgerond en klik vervolgens op "**Activate Plugin"**.

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2F9y3ShvcjMyrUcucbQHHD%2Ffile.png?alt=media)

Eenmaal als de plugin is geactiveerd moeten we onze Field Group beschikbaar stellen in het **WPGraphQL Schema**. Navigeer naar **Custom Fields** in je WP dashboard en klik op een Field Group. Scroll vervolgens naar beneden, onder de settings tab zou je een nieuwe sectie genaamd **GraphQL** moeten zien.

![](<../../.gitbook/assets/image (48).png>)

**\*\*Schakel **"Show in GraphQL'"** in en geef een **beschrijvende naam** in camelcase notatie aan je Field Group**:\*\*

* Artist Fields: **artistMeta**
* Home Page Fields: **homePage**
* About Page Fields: **aboutPage**
* Contact Page Fields: **contactPage**
* Artists Page Fields: **artistsPage**

{% hint style="info" %}
Vergeet niet op update te klikken nadat je de GraphQL sectie hebt aangepast!
{% endhint %}

De overige twee velden "**Manually set GraphQL types for field group**" en "**GraphQL types to show the field group on**" mag je laten staan op de initiële waarden.
