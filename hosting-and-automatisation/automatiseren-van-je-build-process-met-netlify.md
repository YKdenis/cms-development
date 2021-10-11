---
description: >-
  Automatiseer je build proces van je website voor een optimale
  developerservaring!
---

# Automatiseren van je Build Process met Netlify

Laten we beginnen met te identificeren wat Netlify is en wat ze bieden. Netlify is een webhostinginfrastructuur en automatiseringstechnologiebedrijf gevestigd in San Francisco.

In feite werd [JAMstack](https://jamstack.org) in eerste instantie tot leven gebracht door de mede-oprichter van Netlify, Mathias Biilmann. Netlify biedt webhosting en automatisering van de volgende generatie die zeer betaalbaar is. Ze bieden ook webhostinginfrastructuur voor JAMstack-websites.

Netlify vereenvoudigt het proces voor ontwikkelaars om een website te implementeren en te hosten. Het doet al het werk voor ons waar we niet te veel tijd of moeite aan willen besteden. Niet alleen dat, maar het biedt ook verschillende voordelen voor editors van CMS'en zoals WordPress!

{% hint style="info" %}
Jamstack is een architectuur die is ontworpen om je website sneller en veiliger te maken en daarbovenop gemakkelijker te schalen. Het bouwt voort op veel van de favoriete tools en workflows van ontwikkelaars die maximale productiviteit opleveren.

De kernprincipes van pre-rendering (bv. build process van Gatsby) en ontkoppeling zorgen ervoor dat sites en applicaties met meer vertrouwen en veerkracht kunnen worden opgeleverd dan ooit tevoren.

Ontdek meer van de voordelen van [Jamstack](https://jamstack.org/why-jamstack/).
{% endhint %}

### AP Webhosting WordPress applicatie

Vooralleer je kan beginnen met het automatiseren van je build process zal je ervoor moeten zorgen dat je WordPress applicatie ergens online staat. Netlify zal met behulp van je Github repository je website deployen. 

In je frontend gebruik je de `gatsby-source-wordpress` plugin in je `gatsby-config` file om connectie te leggen met je WordPress backend. Momenteel bezit het `url` veld een waarde dat overeenstemt met `https://achternaam-agency.netlify/graphql`. Deze url is alleen gekend in je lokale omgeving (op jou computer) m.a.w. **Netlify kan hier niet aan**. 

Indien je het toch zou proberen zal je snel merken dat het build proces van Netlify zal falen en het een error zal gooien omtrent het niet kunnen ophalen van de WordPress gegevens.

### Continuous Deployment

In stap twee, eenmaal als je WordPress applicatie online staat, zal je leren hoe je continuous deployment toepast en er voor zorgt dat bij elke commit naar je Github repo er een nieuwe build op Netlify word geïnitialiseerd. 

Op deze manier van werken zorg je er voor dat je website altijd overeenstemt met je codebase in je Github repo.

### Gatsby Build Webhook

Ten slotte moet je nog bij elke bewerking op je WordPress applicatie er voor zorgen dat Netlify een nieuwe build start. Dit kan je doen a.d.h.v. een build webhook. De build webhook zal, automatisch bij elke 'save' van een pagina of custom post type, de Netlify hosting pingen en een nieuwe build aanvragen. 
