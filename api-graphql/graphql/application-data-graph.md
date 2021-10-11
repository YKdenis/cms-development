---
description: >-
  Bij het bespreken van Graph Data Structures blijft de vraag naar een
  gemeenschappelijke zoektaal vaak komen.
---

# De Application Data Graph

Op een zeer hoog niveau is een Application Data Graph een niet-lineaire gegevensstructuur waarin data wordt opgeslagen in een verzameling onderling verbonden **nodes** (knooppunten) en **edges** (paden).

**Daarom bestaat een datastructuur van een grafiek uit:**

*
  * Een verzameling **nodes** of knooppunten.
  * Een verzameling **edges** of paden.

 Hieronder zie je een afbeelding die een **Application Data Graph** visualiseert toegepast op onze WordPress installatie. 

![ ](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MacHjpBjW0NOSAD0CGT%2Fuploads%2FqzhgoPJBtDp3tDS7Q7iE%2Ffile.png?alt=media)

In de afbeelding vertegenwoordigen de cirkels individuele bronnen, of "**nodes**". De "nodes" hebben zowel **individuele eigenschappen** als **verbindingen met andere bronnen**. Een Artist in WordPress kan bijvoorbeeld **eigenschappen** hebben zoals "`firstName`", en kan worden verbonden met** andere "nodes"** zoals `Images` en `Roles`. 

De `Image`- en `Role`-nodes kunnen hun **eigen** **eigenschappen** hebben zoals "`name`" en "`sourceUrl`", en kunnen ook verbindingen hebben met andere nodes. De paarse lijnen tussen de "nodes" vertegenwoordigen de "edge"**. Een edge is een verbinding waar contextuele gegevens kunnen worden opgeslagen**.

Neem een sociaal netwerk waar twee gebruikers vrienden kunnen zijn als voorbeeld. De datum waarop de twee gebruikers vrienden werden, is geen eigendom van beide gebruikers, maar** een contextuele eigenschap** over hun connectie als vrienden. **Die contextuele gegevens, die alleen bestaat​​ in de context van een verbintenis tussen twee nodes, worden beschouwd als "edge" data**.

**Samengevat:**

*
  * **Node (knooppunt)**: een node is een individuele bron. Bijvoorbeeld een artist, pagina of gebruiker;
  * **Nodes (knooppunten)**: een verzameling van één of meer bronnen;
  * **Edge**: de verbintenis tussen twee nodes waar contextuele gegevens worden opgeslagen;
  * **Edges**: een verzameling van één of meer edges;

{% hint style="info" %}
Meer dan dat hierboven is samengevat moet je niet weten omtrent een **Application Data Graph**. Het is belangrijk dat je de structuur van een query in de GraphiQL IDE begrijpt!
{% endhint %}

### Documentatie

{% embed url="https://www.wpgraphql.com/docs/connections/" %}

Video: [Application Data Graph](https://www.screencast.com/t/Hhm43hspr7) (vervang)
