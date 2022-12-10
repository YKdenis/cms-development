---
description: >-
  In deze zelfstudie zal je leren hoe je een Gatsby plugin toevoegt aan en
  gebruikt op je site.
---

# Installatieproces van een Gatsby Plugin

## Voeg een plug-in toe aan je site

Om een plugin aan je site toe te voegen, gebruik je het volgende proces:

* Installeer de plugin met **npm**.&#x20;
* Configureer de plugin in het `gatsby-config.js`-bestand van je site.&#x20;
* Gebruik de plugin op je site.

### Een gedetailleerd overzicht:

#### 1) Installeer de plugin met **npm**.&#x20;

Voer in je terminal de volgende opdracht uit . Hiermee wordt de plugin toegevoegd als een [dependency](https://nodejs.dev/learn/npm-dependencies-and-devdependencies) in je `package.json`- en `package-lock.json`-bestanden.

```bash
npm install plugin-name
```

(_verwissel de naam van de plugin voor de naam van de plugin die je wilt gebruiken_)

**Afhankelijk van de plugin die je gebruikt, zijn er mogelijk meer** [**dependencies**](https://nodejs.dev/learn/npm-dependencies-and-devdependencies) **die je moet installeren**. Controleer de `README` van de specifieke plugin in de plugin bibliotheek voor meer details.

#### 2) Configureer de plugin in je `gatsby-config.js`-bestand.

Je `gatsby-config.js`-bestand bevat informatie over je site, inclusief configuratie voor plugins. Je kan een plugin toevoegen aan de array `plugins`:

Dit is een voorbeeld. Je hoeft dit zelf niet uit te voeren!

{% code title="gatsby-config.js" %}
```yaml
module.exports = {
  siteMetadata: {
    title: "My First Gatsby Site",
  },
  plugins: ["plugin-name"],
};
```
{% endcode %}

**Sommige plugins vereisen extra configuratie-opties**. In dat geval voeg je een `object` toe aan de array met plugins (in plaats van een `string`), zoals hieronder wordt weergegeven.

Controleer de plugin `README` in de Gatsby Plugin Library voor meer details over hoe dat options-object eruit zou moeten zien.

{% code title="gatsby-config.js" %}
```yaml
module.exports = {
  siteMetadata: {
    title: "My First Gatsby Site",
  },
  plugins: [
    {
      resolve: "plugin-name",
      options: {
        // Check de plugin README-file voor welke options je hier kan meegeven
      }
    },
  ]
}
```
{% endcode %}

{% hint style="info" %}
**Opmerking** 📣: \_\_nadat je het `gatsby-config.js`-bestand hebt bijgewerkt, moet je opnieuw `gatsby develop` uitvoeren vooraleer je de wijzigingen in de browser zichtbaar zijn.
{% endhint %}

#### 3) Gebruik de plugin op je site.

Nu _je_ de plugin hebt ingesteld, kan je deze naar behoefte op je Gatsby-site gebruiken.

**De details van deze stap zullen verschillen op basis van wat de plugin doet.** Soms heeft de plugin een component of functie die je kan importeren en gebruiken in je site. Op andere momenten hoef je misschien helemaal niets extra's te doen. Controleer de `README` van de plugin voor meer details!

![](<../../.gitbook/assets/image (118).png>)

De volgende secties leiden je door het proces van het toevoegen van een plugin aan je site. Je gebruikt de plugin `gatsby-plugin-image` om performante afbeeldingen aan je site toe te voegen.

### Taak: gebruik `gatsby-plugin-image` om een ​​statische afbeelding aan je Home page toe te voegen

Je kan de `gatsby-plugin-image` plugin gebruiken om **responsieve afbeeldingen** aan je site toe te voegen met behoud van een snelle laadtijd. `gatsby-plugin-image` exporteert een component genaamd `StaticImage`, die je kan gebruiken om afbeeldingen te laden vanaf een externe URL of je lokale bestandssysteem (local filesystem).

Volg de onderstaande stappen om de `StaticImage`-component te gebruiken om een ​​afbeelding van een URL aan je Home page toe te voegen.

**Aangezien we een starter template hebben gebruikt is `gatsby-plugin-image` al geïnstalleerd en staat het in onze `package.json`-file. Je hoeft het niet toe te voegen via de terminal.**

<figure><img src="../../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure>

De `StaticImage`-component vereist een paar extra plugins om te werken. Deze extra plugins worden `peer-dependencies` genoemd. Je moet ze samen met het `gatsby-plugin-image` package installeren:

* `gatsby-plugin-sharp`: verwerkt de daadwerkelijke beeldverwerking die wordt gebruikt door `gatsby-plugin-image`.&#x20;
* `gatsby-source-filesystem`: Hiermee kan je gegevens ophalen uit het bestandssysteem van je computer. (Je leert later meer over deze plugin.)&#x20;

{% hint style="info" %}
Tip: Wanneer je een nieuwe plugin aan je site toevoegt, controleer dan de plugin `README` in de [Gatsby Plugin Library](https://www.gatsbyjs.com/plugins) om te zien of er speciale installatie-instructies zijn.
{% endhint %}

De `gatsby-plugin-sharp` en `gatsby-source-filesystem` plugins zijn al gedefineerd in je `gatsby-config.js`-bestand.

Navigeer naar je `gatsby-config.js`-bestand en verwijder alles dat er momenteel in beschreven staat. We zullen deze samen van scratch opnieuw invullen. Voeg de`gatsby-plugin-sharp` en `gatsby-plugin-image` plugins toe aan je `gatsby-config.js`.&#x20;

**Maak je nog geen zorgen over de `gatsby-source-filesystem`. We komen er later op terug.**

Voeg volgende code toe aan je lege `gatsby-config.js` file:

<pre class="language-yaml"><code class="lang-yaml"><strong>module.exports = {
</strong>  siteMetadata: {
    title: "Artist Agency",
    description: "Artist Agency was founded in 1977 by founder, John Doe. AA continues to be at the forefront of art by establishing the careers of our talents on a holistic level -- and setting trends within the industry.",
    author: "@gatsbyjs",
    siteUrl: "https://gatsbystarterdefaultsource.gatsbyjs.io/",
  },
  plugins: [
    "gatsby-plugin-image",
    "gatsby-plugin-sharp",
  ],
};
</code></pre>

{% hint style="info" %}
#### Key Gatsby-concept 💡

Het bestand `gatsby-config.js` is een speciaal bestand dat Gatsby automatisch herkent. Hier voeg je plugins en andere site-configuratie toe.

Nadat je je `gatsby-config.js`-bestand hebt bijgewerkt, moet je lokale ontwikkelingsserver opnieuw worden opgestart om de nieuwe wijzigingen op te pikken. **Soms start het automatisch opnieuw op, maar als je onverwacht gedrag ziet, probeer het dan zelf te stoppen en opnieuw op te starten**.
{% endhint %}

Nu je plugins zijn geïnstalleerd en geconfigureerd, kan je de `StaticImage`-component op je Gatsby-site gebruiken! Je kan de `StaticImage`-component op dezelfde manier gebruiken als een `HTML` -tag.

De `StaticImage`-component verwacht de volgende `props`:

* `src` (string): De URL naar de afbeelding die je wilt laden. (Dit is hetzelfde als wat je in het `src`-attribuut van een  HTML-element plaatst.)&#x20;
* `alt` (string): De `alt`-tekst om de afbeelding te beschrijven. Dit wordt gebruikt door schermlezers of als er een probleem is met het laden van de afbeelding.&#x20;

Zoek online een afbeeldings-URL en gebruik vervolgens de `StaticImage`-component om die afbeelding aan je Home page toe te voegen:

{% code title="src/pages/index.js" %}
```jsx
import * as React from 'react'
import Layout from '../components/layout'
import { StaticImage } from 'gatsby-plugin-image'

const IndexPage = () => {
  return (
    <main>
      <Layout pageTitle="Welcome to Inghelbrecht Agency!">
      <p>Lorem ipsum</p>
      <StaticImage
        alt="randomized unsplash image!"
        src="https://source.unsplash.com/random/800x600"
      />
      </Layout>
    </main>
  )
}

export default IndexPage
```
{% endcode %}

Ga in je webbrowser naar localhost:8000 om je startpagina te zien. Er zou nu een foto onder aan de pagina moeten staan:

![](<../../.gitbook/assets/image (112).png>)

{% hint style="info" %}
Niets op localhost:8000? Zorg ervoor dat je lokale ontwikkelingsserver nog steeds actief is!
{% endhint %}

```jsx
gatsby develop
```

### Taak: Werk de statische afbeelding bij om een foto van je lokale bestandssysteem te gebruiken

Tot nu toe heb je de `StaticImage`-component gebruikt om een afbeelding van een externe URL toe te voegen. Maar wat gebeurt er als je een foto wilt gebruiken die niet op internet staat?

Je kan ook de `StaticImage`-component gebruiken om afbeeldingen van je lokale bestandssysteem weer te geven.

Download een foto naar je computer en verplaats deze naar je projectmap. Om dingen georganiseerd te houden, plaats je het in de `src/images` directory. Werk de `src`-prop op je Home page bij om een **relatief pad naar je bestand** te zijn in plaats van een URL. (Zorg ervoor dat het overeenkomt met de naam van je afbeelding!) Vergeet niet om de `alt` prop bij te werken om je afbeelding te beschrijven!

```jsx
import * as React from 'react'
import Layout from '../components/layout'
import { StaticImage } from 'gatsby-plugin-image'

const IndexPage = () => {
  return (
    <main>
      <Layout pageTitle="Welcome to Inghelbrecht Agency!">
      <p>Lorem ipsum</p>
      <StaticImage
        alt="Een Gatsby astronaut"
        src="../images/gatsby-astronaut.png"
      />
      </Layout>
    </main>
  )
}

export default IndexPage
```

Ga in je webbrowser naar localhost:8000. Je nieuwe afbeelding zou nu op de startpagina moeten verschijnen.

![](<../../.gitbook/assets/image (66).png>)
