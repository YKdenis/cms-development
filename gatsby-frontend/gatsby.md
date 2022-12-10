---
description: >-
  Gatsby is een gratis en open source framework gebaseerd op React dat
  ontwikkelaars helpt om supersnelle websites en apps te bouwen.
---

# Wat is Gatsby?

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2FNNj6wBFBE5VsKvHDtnGx%2Ffile.png?alt=media)

## Wat is Gatsby?

Gatsby stelt ontwikkelaars in staat om snelle, veilige en krachtige websites te bouwen met behulp van een op **React gebaseerd framework** en een innovatieve gegevenslaag die het integreren van verschillende inhoud, API's en services in één webervaring ongelooflijk eenvoudig maakt.

{% embed url="https://www.gatsbyjs.com/why-gatsby/" %}

{% embed url="https://www.youtube.com/watch?v=GuvAMcsoreI&ab_channel=ZacGordon" %}

Gatsby brengt de voordelen van statische website en dynamische websites samen. We kunnen als ontwikkelaar lokaal een dynamische site bouwen dat vervolgens door Gatsby wordt omgezet in statische HTML pagina's en uiteindelijk [gerehydradeert](https://www.gatsbyjs.com/docs/react-hydration/) wordt naar een React applicatie. Onze hostingprovider zal alleen een map met HTML, CSS en Javascript bestanden moeten hosten en deze beschikbaar stellen aan de eindgebruiker.

Lees zeker eens [Gatsby Core Philosophy](https://www.gatsbyjs.com/docs/gatsby-core-philosophy/) voor een beter inzicht van de filosofie achter Gatsby.

### GraphQL in Gatsby

Een van de geweldige voordelen van Gatsby is dat het de GraphQL-querytaal gebruikt om gegevens op te halen van eender welke API.

GraphQL is beschikbaar in Gatsby zonder een speciale installatie: een schema wordt automatisch opgezet en aangemaakt wanneer je de `gatsby develop` of `gatsby build` command uitvoert. Wanneer de site compileert, kan de graphiQL IDE worden geraadpleegd op: `http:/localhost:8000/___graphql`. Als je naar deze link navigeert krijg je, net zoals in onze Headless WordPress, een GraphiQL IDE te zien.

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2FBWyLkdbybyBKpNWVftbu%2Ffile.png?alt=media)

Gegevens moeten worden verzameld - of toegevoegd aan het GraphQL-schema - om te worden opgevraagd en naar pagina's te worden getrokken met GraphQL. Gatsby gebruikt source plugins om gegevens op te halen.

{% hint style="info" %}
Hoe je een Gatsby applicatie opzet en plugins toegevoegd zal tijdens het labo stap per stap worden uitgelegd.

Termen zoals `gatsby develop` en `gatsby build` zullen ook tijdens het labo verder worden besproken. Maak je geen zorgen als je het nog niet helemaal begrijpt!
{% endhint %}

{% hint style="info" %}
**Opmerking:** GraphQL is niet vereist: je kan Gatsby nog steeds gebruiken zonder GraphQL! Je kan bv. ook een REST API consumeren.&#x20;
{% endhint %}

### Gatsby gebruikt React

Gatsby gebruikt React en CSS, waarmee je hopelijk bekend bent. React wordt gebruikt voor alle templates en CSS voor de styling.

De componentarchitectuur van React vereenvoudigt het bouwen van grote websites door **modulariteit**, **herbruikbaarheid** en **duidelijke abstracties** aan te moedigen. React heeft een groot ecosysteem van open source-componenten, tutorials en tooling die naadloos kunnen worden gebruikt voor het bouwen van sites met Gatsby.

{% hint style="info" %}
Gatsby is gebouwd om zich bijna precies te gedragen als een normale React-applicatie.
{% endhint %}

Gatsby zal ook react-router abstraheren en in de achtergrond toepassen zodat we het gemakkelijk kunnen gebruiken in onze applicatie voor het navigeren tussen pagina’s.

#### Kort samengevat:

1. **GraphQL** haalt onze gegevens binnen;
2. .Met behulp van **React** schrijven we onze componenten in **JSX** (HTML en Javascript);
3. Het stylen van de website gebeurt met **CSS**;
4. Ten slotte compileert **Gatsby** al onze code (**React, GraphQL en CSS**) naar **statische files**;

### Gatsby heeft een rijk plugin-ecosysteem

Het is vermeldenswaardig dat Gatsby is gebouwd met een **plugin-architectuur** in gedachte en dit is een geweldig systeem.

#### Wat is een plugin?

Gatsby-plugins zijn Node.js-packages die Gatsby-API's implementeren en die gewoonlijk worden geïnstalleerd via een register zoals npm. Er zijn veel soorten plugins, waaronder data sourcing, SEO, responsieve afbeeldingen, offline ondersteuning, ondersteuning voor Sass, TypeScript, sitemaps en RSS, Google Analytics en meer.

Omdat wat we aanbieden een statische site is, kan de manier waarop we omgaan met JavaScript en andere dynamische functionaliteit van React en GraphQL een beetje ingewikkeld worden. Het is dus heel fijn dat we deze complexe code in plugins kunnen overbrengen en we kunnen vertrouwen op een enorm ecosysteem van andere plugin-auteurs om een deel van het zware werk voor ons te doen. **I.p.v. het wiel heruit te vinden kunnen we plugins gebruiken van andere programmeurs om veel voorkomende functionaliteit out-of-the-box te voorzien.**

{% hint style="info" %}
Deze plug-in-architectuur is een groot deel van Gatsby en wat het zo populair en krachtig maakt!

Je kan Gatsby plugins vergelijken met het installeren van externe libraries in React.
{% endhint %}

### Waarom Gatsby?

In één simpele zin gebruik je Gatsby vanwege zijn **snelheid, beveiliging en verbeterde ontwikkelaarservaring**.

#### Snelheid

Een van de grootste voordelen die je met Gatsby kunt behalen is ongetwijfeld de snelheid. Je genereert een statische site en zal veel sneller zijn dan veel van de alternatieven zoals bv. een gecachte WordPress website. Deze zal nooit zo snel en performant zijn als een statische website. De gecachte WP site moet nog steeds pingen naar de server voor te zien of er aanpassingen zijn doorgevoerd op de website. **Een Gatsby website zal nooit een request sturen naar een server. Alle data van de server wordt tijdens het build proces in de html geïnjecteerd!**

#### Beveiliging

Een statische site is inherent veel veiliger dan een dynamische site. Er is geen connectie met een databank. **De gehele website bestaat uit vooropgemaakte statische files.**

**Aangezien er geen live databank is, kan deze niet gelekt of gehackt worden**. Er zijn geen gebruikersgegevens die worden opgeslagen op de server waar de Gatsby-site gehost staat. In het geval dat iemand toegang krijgt tot de hosting server, hebben ze nog steeds alleen toegang tot HTML, CSS en Javascript-bestanden en kunnen ze veel minder schade aanrichten dan wanneer ze toegang zouden krijgen tot bijvoorbeeld een WordPress-site die gelinkt is aan een databank.

Met Gatsby behalen we dus een enorme beveiligingswinst!

#### Ontwikkelaarservaring

Ten slotte is de derde grote winst met Gatsby een verbeterde ontwikkelaarservaring. Het kan erg uitputtend en vervelend zijn voor ontwikkelaars om met verouderde stacks (technologieën) te werken.

Een van de leuke dingen van het werken met Gatsby is dat je **een moderne ontwikkelomgeving** hebt. De tooling is eenvoudig en robuust. De talen zijn modern en proper. Over het algemeen is het een geweldige omgeving om in te werken.

Bovendien is er **geweldige documentatie** en dat is erg handig wanneer je met een nieuwe technologie werkt. Je kan de Gatsby documentatie [hier](https://www.gatsbyjs.com/docs/) raadplegen.

### Een kort overzicht van Gatsby

Dus, dat gezegd hebbende, laten we hier even snel alles bekijken wat we hebben geleerd:

* Gatsby is een static site-generator;
* Onder de motorkap gebruikt het GraphQL en React;
* De belangrijkste voordelen zijn **snelheid**, **beveiliging** en **ontwikkelaarservaring**;
* Gatsby heeft een stabiele en groeiende gemeenschap van ontwikkelaars en plugin-auteurs;
