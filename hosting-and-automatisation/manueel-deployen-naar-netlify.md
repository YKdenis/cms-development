---
description: >-
  Leer hoe je een static site met Gatsby build via de terminal en manueel online
  zet op Netlify.
---

# Manueel deployen naar Netlify

## Probleemstelling en oplossing

Jammer genoeg laat de webhosting van AP het ons niet toe om Continuous Deployment te gebruiken voor onze frontend. Dit heeft te maken met de permissies die zijn ingesteld op de webhosting servers van AP. De servers zijn alleen te bereiken via het intern netwerk, intranet, van AP. M.a.w. de servers van Netlify kunnen niet communiceren met de server van AP.

Als oplossing zal je de build lokaal op je computer uitvoeren en de geëxporteerde statische files manueel op Netlify deployen.

### Lokaal builden van je Gatsby website

Open je artist agentschap in Visual Studio Code en navigeer naar je `gatsby-config` file. Zorg er voor dat de waarde van je `url` field gelijk is aan de `/graphql` link van Local WP installatie.

![](<../.gitbook/assets/image (72).png>)

Vooralleer je begint met het builden van je website let er op dat je Local website aan het runnen is.

Open je terminal en navigeer via het `cd` commando naar de root map van je Gatsby project. Voer voor de zekerheid nog eens het commando `gatsby clean` uit en vervolgens het commando `gatsby build`.

{% hint style="info" %}
Met `gatsby build` zal je de react applicatie omzetten tot statische files. Telkens wanneer je aanpassingen uitvoert in je code zal je de commando **gatsby build** opnieuw moeten uitvoeren vooraleer de verandering worden weergegeven in je statische files.
{% endhint %}

![](<../.gitbook/assets/image (148).png>)

Als alles goed verlopen is zou je nu een folder `public` moeten zien staan onder je `node_modules` folder in je root folder.

![](<../.gitbook/assets/image (8).png>)

{% hint style="info" %}
Met `gatsby serve` kan je testen of je build wel degelijk is gelukt. Voer het commando uit en surf naar [https://localhost:9000](https://localhost:9000). Check of dat je website werkt naar behoren. Test alle links, bekijk of de styling klopt, errors in de console, etc.
{% endhint %}

Je build is gelukt en je website is geëxporteerd naar statische files. In de volgende stap zal je de folder `public` manueel uploaden naar Netlify.

### Manueel deployen naar Netlify

Maak een account aan op de website van Netlify of log in met een bestaand account. Je kan aanmelden via **je e-mailadres van AP** of je **Github account**!

{% embed url="https://www.netlify.com" %}
Netlify website
{% endembed %}

Eenmaal ingelogd navigeer je naar **Sites** in de navigatiebalk van boven.&#x20;

![](<../.gitbook/assets/image (27).png>)

Onderaan de pagina is er een upload zone. Sleep je `public` folder, dat je hebt aangemaakt in de vorige stap, naar de upload zone om je website online te zetten.

![Upload zone Netlify - Sites](<../.gitbook/assets/image (35).png>)

Na een paar seconden zal je site online staan. Je zal een willekeurig gegenereerde link krijgen waarmee je naar je website kan navigeren.

![](<../.gitbook/assets/image (96).png>)

Proficiat je website staat online! :tada: Wat je nog kan doen is de willekeurig gegenereerde URL aanpassen naar de naam van je agentschap. Dat kan je doen door op de knop "**Domain Settings**" te klikken en vervolgens bij **Custom Domains,** bij de link van je website, op "**Options -> Edit site name**" te klikken.

![](<../.gitbook/assets/image (44).png>)

![](../.gitbook/assets/image.png)

![](<../.gitbook/assets/image (7).png>)
