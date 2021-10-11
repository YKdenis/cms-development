---
description: >-
  Creëert ImageSharp-nodes van afbeeldingstypen die worden ondersteund door de
  Sharp image processing library en biedt velden in hun GraphQL-typen voor het
  verwerken van je afbeeldingen.
---

# Gatsby plugin: gatsby-transformer-sharp

Om de `GatsbyImage`-component te gebruiken, moet je de plugin `gatsby-transformer-sharp` aan je site toevoegen.

Wanneer Gatsby tijdens het bouwen nodes aan de Data Layer toevoegt, zoekt de plugin `gatsby-transformer-sharp` naar `File` nodes die eindigen op een afbeeldingsextensie \(zoals .png of .jpg\) en maakt een `ImageSharp`-node voor dat bestand.

{% embed url="https://www.gatsbyjs.com/plugins/gatsby-transformer-sharp/" caption="" %}

`gatsby-transformer-sharp` is al geïnstalleerd in je project aangezien het gebaseerd is op een starter template. Het enigste dat je moet doen is het toevoegen aan je `gatsby-config.js`-file zoals hieronder weergegeven:

{% code title="gatsby-config.js" %}
```yaml
module.exports = {
  siteMetadata: {
    title: "Inghelbrecht Agency",
    description: "Artist Agency was founded in 1977 by founder, John Doe. AA continues to be at the forefront of art by establishing the careers of our talents on a holistic level -- and setting trends within the industry.",
    author: "@gatsbyjs",
    siteUrl: "https://gatsbystarterdefaultsource.gatsbyjs.io/",
  },
  plugins: [
    "gatsby-plugin-image",
    "gatsby-plugin-sharp",
    "gatsby-transformer-sharp",
    {
      resolve: "gatsby-source-wordpress",
      options: {
        /*
         * De volledige URL van je Headless WordPress site's GraphQL API.
         * Voorbeeld : "https://www.example-site.com/graphql"
         */
        url: "http://artist-agency-2021.local/graphql",
      },
    },
  ],
};
```
{% endcode %}

Aangezien je `gatsby-transformer-sharp` aan je site hebt toegevoegd, moet je je lokale ontwikkelingsserver opnieuw opstarten om de wijzigingen in GraphiQL te zien. In de volgende stap zal je in GraphiQL verder werken.

