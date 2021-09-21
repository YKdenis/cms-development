---
description: >-
  Opzetten van een Gatsby-applicatie op basis van een starter, het opstarten van
  een hot-reloading lokale ontwikkelserver en meer!
---

# Aanmaken van je eerste Gatsby website

## Maak een nieuwe Gatsby site

Nu je je computer hebt ingesteld met alle tools die je nodig hebt, is het tijd om aan de slag te gaan!

In de loop van deze zelfstudie bouw en implementeer je je eerste Gatsby-site. Je site zal in connectie staan met je headless WP en via GraphQL de data opvragen en weergeven! Hier is een ****[**volledig voorbeeld**](https://artist-agency-2021.netlify.app/) van de site die je gaat bouwen.

{% embed url="https://artist-agency-2021.netlify.app/" %}

In dit deel van de zelfstudie doorloop je het proces om de sjabloon voor je artiesten website te maken en deze online te zetten.

### Gatsby new

Navigeer in je terminal naar de map waarin je de nieuwe website wenst aan te maken a.d.h.v. het commando `cd`. Typ vervolgens onderstaande commando in je terminal. Je mag de naam artist-agency veranderen naar 'achternaam-agency' bv. "**janssens-agency**".

```bash
gatsby new artist-agency https://github.com/gatsbyjs/gatsby-starter-default.git 
```

Met `gatsby new` creëer je een nieuwe gatsby website. Het laatste argument in de commando zal een link leggen met een voorgemaakt Gatsby sjabloon. Je kan navigeren naar [https://github.com/gatsbyjs/gatsby-starter-default.git](https://github.com/gatsbyjs/gatsby-starter-default.git) en het sjabloon bekijken.

Open je VScode, of je IDE naar keuze, en navigeer naar je Gatsby project. Je zal zien dat de mappen structuur de exacte structuur van het gatsby-default-starter sjabloon volgt.

![](../../.gitbook/assets/image%20%28103%29.png)

