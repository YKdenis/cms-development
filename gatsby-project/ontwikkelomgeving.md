---
description: >-
  Het doel van deze les is om je te begeleiden bij het opzetten en implementeren
  van je eerste Gatsby-site met behulp van een starterstemplate.
---

# Opzetten van de ontwikkelomgeving  🏗

## de onderliggende structuur van een Gatsby-site

Voordat je begint met het bouwen van je eerste Gatsby-site, moet je vertrouwd raken met enkele web-technologieën en ervoor zorgen dat je alle vereiste software-tools hebt geïnstalleerd.

{% hint style="info" %}
Gatsby heeft hiervoor zelf een goede tutorial ter beschikking die je kan volgen via onderstaande link.
{% endhint %}

{% embed url="https://www.gatsbyjs.com/docs/tutorial/part-0/" %}

### De Command Line Interface

De command line is **een op tekst gebaseerde interface die wordt gebruikt om opdrachten op je computer uit te voeren**. Je zult het ook vaak als **de terminal** zien. In deze cursus gebruiken we beide termen door elkaar. 

Voor Gatsby zal je basis commando's zoals `cd`, `ls`, en `npm i`, ... moeten gebruiken. In vorige of samenlopende vakken heb je hoogstwaarschijnlijk al eens in de terminal gewerkt. Indien dit niet het geval is, of je wilt de basis er van nog eens opfrissen bekijk dan onderstaande links.

De instructies voor het gebruik van de command line verschillen enigszins, afhankelijk van het besturingssysteem dat je computer gebruikt:

* [Command line instructies voor Mac](https://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/)
* [Command line instructies voor Windows](https://www.lifewire.com/how-to-open-command-prompt-2618089)
* [Command line instructies voor Linux](https://www.howtogeek.com/140679/beginner-geek-how-to-start-using-the-linux-terminal/).

### NodeJS

**Node.js is een omgeving die JavaScript-code buiten een webbrowser kan uitvoeren.** Gatsby is gebouwd met Node.js. Om met Gatsby aan de slag te gaan, moet je een recente versie van Node op je computer hebben geïnstalleerd. npm wordt gebundeld met Node.js, dus als je geen npm hebt, is de kans groot dat je ook geen Node.js hebt!

Indien Node nog niet geïnstalleerd is op je computer kan je de laatste versie van Node via de onderstaande link downloaden. Volg vervolgens de instructies om het te installeren.

{% embed url="https://nodejs.org/en/" caption="Node installatie link" %}

Eenmaal als je het hebt geïnstalleerd navigeer je naar je terminal en type je **npm -v of node -v**. De installatie is gelukt indien je de versie van npm of Node terugkrijgt!

{% tabs %}
{% tab title="npm" %}
```bash
npm -v
```
{% endtab %}

{% tab title="node" %}
```
node -v
```
{% endtab %}
{% endtabs %}

![](../.gitbook/assets/image%20%2841%29.png)

#### Wat is NPM?

**npm is een JavaScript package manager.** Als je Node.js hebt gedownload en geïnstalleerd, is npm er automatisch bij geïnstalleerd!

{% hint style="info" %}
Een package is een code geschreven door andere developers die je kan hergebruiken in je eigen projecten. 

Bekijk ["Wat is npm?"](https://docs.npmjs.com/about-npm/index.html) voor meer informatie omtrent npm.
{% endhint %}

### Git

Git is een **gratis en open source gedistribueerd versiebeheersysteem** dat is ontworpen voor verschillende versies van je code op te slagen. Het helpt teamleden  om tegelijkertijd aan dezelfde codebase te werken.

Voor je Artist Agency project zal je een "starter"-site gebruiken. Dit is een **template project** waarop jij kan verder bouwen  

Wanneer je een Gatsby "starter" -site installeert, gebruikt Gatsby Git achter de schermen om de vereiste bestanden voor je starter te downloaden en te installeren. M.a.w. je moet Git hebben geïnstalleerd om je eerste Gatsby-site op te zetten.

De stappen om Git te downloaden en te installeren, zijn afhankelijk van je besturingssysteem. Volg de gids voor je systeem: 

* Installeer Git op [macOS](https://www.atlassian.com/git/tutorials/install-git#mac-os-x)
* Installeer Git op [Windows](https://www.atlassian.com/git/tutorials/install-git#windows)

Git is correct geïnstalleerd als je de versie terug krijgt bij het typen van git --version in je terminal.

```bash
git --version
```

![](../.gitbook/assets/image%20%2885%29.png)

### Gatsby CLI

De Gatsby-Command Line Interface \(CLI\) is een hulpmiddel waarmee je snel een Gatsby aangedreven site kan maken. De CLI is een gepubliceerd npm-pakket, wat betekent dat je het met npm kunt installeren.

Installeer de Gatsby CLI globaal door de onderstaande opdracht uit te voeren.

```bash
npm install -g gatsby-cli
```

Controleer of je de juiste versie hebt geïnstalleerd door de onderstaande opdracht uit te voeren. Je zou op v3 of nieuwer moeten zijn.

```bash
gatsby --version
```

Nu dat je de Gatsby CLI hebt geïnstalleerd kan je de **gatsby** command tools gebruiken in je terminal voor het aanmaken van je eerste gatsby aangedreven website!

