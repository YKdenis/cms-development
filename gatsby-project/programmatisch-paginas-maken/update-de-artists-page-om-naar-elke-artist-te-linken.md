---
description: >-
  De laatste stap dit deel is het doorlinken van je Artists page naar je aparte
  Artist pages.
---

# Update de Artists page om naar elke artist te linken

Tot nu toe heb je de File System Route API en GraphQL-query variabelen gebruikt om afzonderlijke pagina's te maken voor elk van je artiesten.

## Voeg het `slug`-veld toe aan je page query en gebruik het om een link toe te voegen naar je artiesten.

Aangezien deze links tussen pagina's op je eigen site staan, kan je **Gatsby's Link-component** gebruiken om wat extra prestatievoordelen te krijgen. Als je absolute URL's gebruikt, moet je de extra `/artists/` **path parameter** toevoegen, aangezien het veld `slug` alleen het laatste deel van het pad bevat \(zoals `kevin-bismark`\).

```jsx
import * as React from 'react'
import { Link, graphql } from 'gatsby'
import Layout from '../../components/layout'

const ArtistsPage = ({data: {allWpArtist: {edges}}}) => {
  return (
    <Layout pageTitle="Artists of Inghelbrecht Agency">
      {edges.map((item) => {
        const artist = item.node.artistMeta;
        const slug = item.node.slug;
        return <Link to={`/artists/${slug}`}>
          <p key={item.node.id}>{artist.firstName} {artist.lastName}</p>
        </Link>

      })}
    </Layout>
  )
}

export const query = graphql`
  query {
  allWpArtist {
    edges {
      node {
        artistMeta {
          firstName
          lastName
          artistName
        }
                id
        slug
      }
    }
  }
}

`

export default ArtistsPage
```

Ga in een webbrowser naar[ localhost:8000/artists](http://localhost:8000/artists). Je Artists page zou nu links naar elk van je Artist pages moeten tonen.

![](../../.gitbook/assets/image%20%2873%29.png)

Gefeliciteerd, je hebt nu een artiesten agentschap website met meerdere pagina's! 🎉 Probeer enkele nieuwe artiesten in WordPress toe te voegen. Ze zouden automatisch aan je website moeten worden toegevoegd wanneer je site opnieuw wordt opgebouwd!

