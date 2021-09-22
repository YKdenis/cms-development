---
description: >-
  De ontwikkelingsserver is een handig hulpmiddel wanneer je lokaal (vanaf je
  eigen computer) aan je site wilt werken.
---

# Lokaal ontwikkelen met Gatsby - gatsby develop

## Run je site lokaal

Proficiat! Je hebt de code voor je site gegenereerd a.d.h.v. een starter template, maar hoe ziet deze er eigenlijk uit in een webbrowser zoals Firefox of Google Chrome? **Om daar achter te komen, moet je eerst de lokale ontwikkelingsserver van je site opstarten**.

**De ontwikkelingsserver is een handig hulpmiddel wanneer je lokaal \(vanaf je eigen computer\) aan je site wilt werken.** Wanneer je ontwikkelingsserver actief is, kan je een webbrowser gebruiken om te communiceren met je lokale site. Op die manier kan je wijzigingen in je code testen om er zeker van te zijn dat ze werken voordat je daadwerkelijk een nieuwe versie van je site op internet publiceert.

### **Ga als volgt te werk om je ontwikkelingsserver op te starten:**

1\) Ga in de command line naar de map die je voor je site hebt gemaakt:

```bash
cd artist-agency
```

{% hint style="info" %}
Je kan ook navigeren naar de terminal in VScode en via deze weg verder werken! \`\`cntrl + shift + \`\`\` _\*\*_voor mac
{% endhint %}

![](../../.gitbook/assets/image%20%2820%29.png)

2\) Start de ontwikkelingsserver vanuit je sitemap door de volgende opdracht uit te voeren:

```bash
gatsby develop
```

3\) Na enkele ogenblikken zou de command line een bericht als het volgende moeten weergeven, waarin staat dat je ontwikkelingsserver klaar is voor gebruik!

```bash
You can now view gatsby-starter-default in the browser.
⠀
  http://localhost:8000/
⠀
View GraphiQL, an in-browser IDE, to explore your site's data and schema
⠀
  http://localhost:8000/___graphql
⠀
Note that the development build is not optimized.
To create a production build, use gatsby build
⠀
success Building development bundle - 11.051s
success Writing page-data.json files to public directory - 0.498s - 3/6 12.06/s
```

4\) Open je favoriete webbrowser en navigeer naar [http://localhost:8000](http://localhost:8000).

![http://localhost:8000/](../../.gitbook/assets/image%20%2823%29.png)

je allereerste Gatsby-site! 🎉

Je kan de site lokaal bezoeken op [http://localhost:8000/](http://localhost:8000/) zolang je ontwikkelingsserver actief is. **\(Dat is het proces dat je startte door de opdracht** `gatsby develop` **uit te voeren.\)** Om te stoppen met het uitvoeren van dat proces \(of om te stoppen met het uitvoeren van de ontwikkelingsserver\), ga je terug naar je command line, hou je de `control` -toets ingedrukt en drukt je vervolgens op **c** \(`ctrl-c`\). Om het opnieuw te starten, voer je _\*\*_`gatsby develop` opnieuw uit!

