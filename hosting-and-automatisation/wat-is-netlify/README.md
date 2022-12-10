---
description: >-
  Netlify is een hosting platform dat speciaal is ontworpen voor het hosten van
  statische websites
---

# Wat is Netlify?

<figure><img src="../../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

## Wat is Netlify?

**Netlify host je statische websites en zorgt op een effectievere manier voor betere beveiliging, prestaties, snelheid en schaalbaarheid.**

Netlify is een van de meest vernieuwende webontwikkelingsplatforms. Het helpt programmeurs hun productiviteit op de best mogelijke manier te vermenigvuldigen. Het platform voorziet een gemakkelijke manier om statische files te hosten en daarboven op deze te testen en uit te breiden met dynamische functionaliteiten zoals het afhandelen van formulieren.&#x20;

De website-industrie verandert zowel continu als snel van een monolithische naar ontkoppelde structuur. Netlify is echter ontwikkeld om op dit moment in te spelen. Het biedt ongelooflijke **webautomatiseringstechnologie** en **webhostinginfrastructuur**. Netlify biedt oplossingen van de volgende generatie in beide aspecten.

{% hint style="info" %}
Netlify is een krachtig **serverless** platform met een intuïtieve, op git gebaseerde workflow.
{% endhint %}

### Hoe werkt Netlify en waarvoor wordt het gebruikt?&#x20;

Netlify werkt als volgt voor het hosten van statische files gegenereerd door een SSG:

1. Maakt verbinding met je **GitHub-repository** om je broncode op te halen;
2. Start het **bouwproces** van je gatsby/react applicatie;
3. Maakt **statische files** (HTML, CSS en Javascript) aan;
4. Host de statische files op een **CDN**;

{% content-ref url="wat-is-een-cdn.md" %}
[wat-is-een-cdn.md](wat-is-een-cdn.md)
{% endcontent-ref %}

In een notendop, Netlify creëert zijn eigen soort repository die zowel naar een Github-repository als zijn eigen microservices pusht. Vervolgens distribueert het je website over een CDN om het tenslotte aan bezoekers te leveren.

Netlify gebruikt een CDN om je content te distribueren, wat resulteert in het sneller laden van je website dan op traditionele hostingnetwerken. In plaats van de site telkens te laden wanneer de bezoeker naar een pagina surft, krijgt de bezoeker een vooraf geladen versie rechtstreeks van de dichtstbijzijnde geografische CDN-knooppunt, waardoor de laadtijden sterk worden verkort.

De HTML, CSS en JS van je website worden gedistribueerd over een groot aantal CDN-knooppunten. Wanneer een bezoeker toegang probeert te krijgen tot je website, kiest hij automatisch het knooppunt dat het dichtst bij je in de buurt is en levert vervolgens de statische bestanden aan.

### Waarom Netlify?

#### Prijs

Het is gratis. Netlify heeft een **gratis tier** die je toegang geeft tot de basis functionaliteit om een statische website te deployen. Een abonnement geeft je toegang tot meer add-ons en capaciteit indien je op grotere projecten werkt.

{% hint style="info" %}
Voor het hosten van je artist agency is de gratis tier van Netlify voldoende!
{% endhint %}

#### Continuous Deployment

Continuous Deployment werkt door je GitHub-repository te verbinden en de broncode van je website op te halen. Telkens wanneer er een wijziging is in je repository, detecteert Netlify deze wijziging en voert vervolgens het build process van je website opnieuw uit.

Deze manier van werken zorgt er voor dat je website altijd overeenstemt met je codebase. Je zal niet meer manueel bij elke bewerking je website opnieuw moeten uploaden!

#### Netlify als Content Delivery Network

Netlify voorziet een CDN systeem speciaal ontworpen voor statische websites te hosten.

Je moet geen server voorzien om je artist agency website te hosten. Je website bestaat uit alleen statische files m.a.w. je kan je gehele website op de CDN van Netlify zetten.

Dit is veel goedkoper dan een hosting service op te zetten en verbeterd de performance aangezien je website nu op verschillende knooppunten is gecachet!

{% hint style="info" %}
&#x20;De reden waarom Netlify een gratis tier kan voorzien is omdat statische files heel weinig plaats in beslag nemen en worden niet bij elke ping opnieuw opgebouwd zoals bij dynamische websites (**serverside rendering**).

Het kost voor Netlify **twee keer niets** om een statische website op hun Content Delivery Netwerk te hosten.
{% endhint %}
