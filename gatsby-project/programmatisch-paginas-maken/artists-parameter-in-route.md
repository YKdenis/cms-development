---
description: >-
  Groepeer je artist template onder een submap genaamd artists voor Search
  Engine Optimization en de algemene organisatie van je website.
---

# Toevoegen van /artists parameter in de route

## Taak: update route om een /artists-parameter op te nemen

Tot nu toe zijn al je pagina's gemaakt rechtstreeks op het hoofddomein van je site (localhost:8000). Maar het zou beter zijn (zowel voor Search Engine Optimization als voor de algemene organisatie van je website) als je al je artiesten onder een `/artists`-parameter zou groeperen. Op die manier zouden de URL's voor al je artiesten beginnen met `localhost:8000/artists/`.

Aangezien Gatsby routes bouwt op basis van de mappenstructuur in de `src/pages`-directory, kan je nieuwe route parameters aan een pagina toevoegen door subdirectories in `src/pages` aan te maken.

Maak een nieuwe map in je `src/pages`-map en noem het artists.

![](<../../.gitbook/assets/image (130).png>)

Verplaats het bestand `src/pages/{wpArtist.slug}.js` naar de nieuwe artists-submap.

Werk de import voor je `Layout` component bij om de nieuwe mapstructuur weer te geven:

{% code title="src/pages/artists/{wpArtists.slug}.js" %}
```jsx
import * as React from 'react'
import Layout from '../../components/layout'
// ...
```
{% endcode %}

Zodra je lokale ontwikkelingsserver je site opnieuw heeft opgebouwd, controleer je in een webbrowser of de routes naar je artiesten zijn bijgewerkt.

Je zou nu bijvoorbeeld een pagina moeten hebben op `localhost:8000/artists/kevin-bismark`, en proberen toegang te krijgen tot `localhost:8000/kevin-bismark` (zonder de artists paramater in je route). Deze route zou je naar de **404-pagina** moeten sturen.

{% hint style="info" %}
**Pro tip** 🧙‍♂️: **Gatsby slaat informatie over je site op in de cache** terwijl deze wordt gebouwd, om volgende builds sneller te maken. Maar soms, wanneer je wijzigingen aanbrengt op je site, moet je de cache leegmaken voordat je wijzigingen worden weergegeven.

Als je onverwacht gedrag ziet (zoals misschien dat je lokale ontwikkelingsserver je nieuwe wijzigingen niet oppikt), kan je `gatsby clean` commando uitvoeren in de terminal om de **cache te verwijderen** en opnieuw te beginnen met je volgende build.
{% endhint %}

Voor de organisatie zou het goed zijn om al je artiest gerelateerde pagina's bij elkaar te houden. Verplaats het bestand `src/pages/artists.js` ook naar je nieuwe map `src/pages/artists`.

* Hernoem het bestand van `artists.js` naar `index.js`. (Anders wordt je artiest pagina verplaatst naar `localhost:8000/artists/artists`).
* Je moet ook de import voor de `Layout` component bijwerken om de nieuwe mappenstructuur weer te geven:

{% code title="src/pages/artists/index.js" %}
```jsx
import * as React from 'react'
import { graphql } from 'gatsby'
import Layout from '../../components/layout'

// ...
```
{% endcode %}

* Mogelijk moet je je lokale ontwikkelingsserver stoppen en opnieuw opstarten om de wijzigingen weer te geven.

Controleer in een webbrowser of je Artists page nog steeds wordt weergegeven op l[ocalhost:8000/artists](http://localhost:8000/artists).

Goed werk! Je hebt nu Gatsby's File System Route API gebruikt om pagina's te maken van nodes in de Data Layer!
