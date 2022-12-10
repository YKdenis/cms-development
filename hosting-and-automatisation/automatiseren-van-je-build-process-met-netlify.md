---
description: >-
  Automatiseer je build proces van je website voor een optimale
  developerservaring!
---

# Automatiseren van je Build Process met Netlify

Laten we beginnen met te identificeren wat Netlify is en wat ze bieden. Netlify is een webhostinginfrastructuur en automatiseringstechnologiebedrijf.

Netlify vereenvoudigt het proces voor ontwikkelaars om een website te onderhouden en te hosten. Het doet heel veel routine werk voor ons waar we niet te veel tijd of moeite aan willen besteden. Niet alleen dat, maar het biedt ook verschillende voordelen voor editors van CMS'en zoals WordPress!

{% hint style="info" %}
**Jamstack** is een architectuur die is ontworpen om je website sneller en veiliger te maken en daarbovenop gemakkelijker te schalen. Het bouwt voort op veel van de favoriete tools en workflows van ontwikkelaars die maximale productiviteit opleveren.

De kernprincipes van pre-rendering (bv. build process van Gatsby) en ontkoppeling zorgen ervoor dat sites en applicaties met meer vertrouwen en veerkracht kunnen worden opgeleverd dan ooit tevoren.

Ontdek meer van de voordelen van [Jamstack](https://jamstack.org/why-jamstack/).
{% endhint %}

### 1) Webhosting WordPress applicatie

Vooraleer je kan beginnen met het automatiseren van je build process zal je ervoor moeten zorgen dat je WordPress applicatie ergens online staat. Netlify zal met behulp van je Github repository je website deployen **MAAR**:

In je frontend gebruik je de `gatsby-source-wordpress` plugin in je `gatsby-config` file om connectie te leggen met je WordPress backend. Momenteel bezit het `url` veld een waarde dat overeenstemt met `https://achternaam-agency.netlify/graphql`. Deze url is alleen gekend in je lokale omgeving (op jou computer) m.a.w. **Netlify kan hier niet aan**.&#x20;

Indien je het toch zou proberen zal je snel merken dat het build proces van Netlify zal falen en het een error zal gooien omtrent het niet kunnen ophalen van de WordPress gegevens.

Vandaar moet je WordPress applicatie ergens online staan zodat Netlify er mee kan communiceren.

{% hint style="warning" %}
**Let op:** de webhosting van AP is alleen intern toegankelijk m.a.w. Netlify kan niet communiceren met een WordPress applicatie gehost op de AP webhosting.

Indien je de volgende stappen wilt uitvoeren (**continuous deployment en webhooks**) moet je zelf een hosting voorzien voor je WordPress website.

Als je geen eigen webhosting kunt voorzien lees je over beide concepten en volg je het hoofdstuk '**Manueel deployen naar Netlify**'.

Je moet degelijk weten wat continuous deployment is en hoe webhooks werken!
{% endhint %}

### 2) Continuous Deployment

In stap twee, eenmaal als je WordPress applicatie online staat, zal je leren hoe je continuous deployment toepast en er voor zorgt dat bij elke commit naar je Github repo er een nieuwe build op Netlify word geïnitialiseerd.&#x20;

**Met deze manier van werken zorg je er voor dat je website altijd overeenstemt met je codebase in je Github repo.**

### 3) Gatsby Build Webhook

Wanneer je continuous deployment hebt toegepast op je website zal Netlify luisteren naar aanpassingen in je Github repo. Wat als er aanpassingen zijn in je WordPress applicatie? Bv. wanneer een admin een nieuwe artiest toevoegt.&#x20;

Netlify moet dus ook nog een nieuwe build starten bij het aanpassen van content op je WordPress applicatie. Dit kan je doen a.d.h.v. een build webhook. De build webhook zal, automatisch bij elke 'save' van een pagina of custom post type, de Netlify hosting pingen en een nieuwe build aanvragen.&#x20;
