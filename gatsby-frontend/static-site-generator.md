---
description: >-
  Een nieuwe trend is in opkomst in de ontwikkelingswereld: statische site
  generatoren (SSG's)
---

# Wat is een static site-generator?

Jarenlang was voor het ontwikkelen, publiceren en bewerken van inhoud op een website kennis van HTML, CSS en Javascript vereist, waardoor deze processen buiten de mogelijkheden van de gemiddelde gebruiker lagen. Sindsdien zijn er contentmanagementsystemen (CMS'en) ontstaan ​​- zoals WordPress, Joomla, Drupal, enz. - **die de technische drempel verlaagde om webcontent te wijzigen**.

Handige en gebruiksvriendelijke CMS'en stellen niet-technische gebruikers in staat hun eigen inhoud op het internet te beheren en controle te krijgen over het ontwerp en de weergave van een website.

In de loop der tijd hebben CMS'en echter evenveel bekendheid verworven om hun beperkingen als om hun voordelen - ze kunnen **traag en omslachtig** zijn om mee te werken en **worstelen met schaalbaarheid en beveiliging**. En dit heeft de weg geëffend voor de terugkeer van static site-generators als antwoord op al deze problemen en meer.

Static site-generators zijn de afgelopen jaren enorm in populariteit gestegen vanwege hun **eenvoud, beveiligingsvoordelen en het vermogen om snel inhoud te leveren**. Maar wat zijn ze, hoe beïnvloeden ze het webontwikkelingsproces en wanneer moet je overwegen er een te gebruiken?

## Wat is een Static Site-generator?

Satic site-generators passen gegevens en inhoud toe op templates en genereren een weergave van een pagina die kan worden weergegeven aan de bezoekers van een site.

Het grootste verschil tussen een static site-generator en een traditionele webapplicatie-stack, is dat in plaats van te wachten tot een pagina wordt opgevraagd en vervolgens elke keer de weergave op aanvraag genereert, **een static site-generator dit van tevoren doet**, zodat de weergave klaar is om op voorhand te serveren. En het doet dit voor elke pagina van een site tijdens het bouwen.

Beschouw een static site-generator als een **bouw proces** dat gegevens, inhoud en templates opneemt, verwerkt en een map vol met alle resulterende pagina's en middelen exporteert (**HTML, CSS en Javascript bestanden**).

Dit heeft een aantal waardevolle effecten, maar het belangrijkste is dat het werk verschuift van "**request time**" (wanneer gebruikers om de weergave vragen) naar "**build time**" (de tijd nodig om het gehele bouwproces te doorlopen).

In een traditionele aanpak, zoals bij de gekoppelde CMS-architectuur van WordPress, wordt er bij elke aanvraag van een pagina **dynamisch een template en databank gegevens gecombineerd**. Dit proces vindt plaats op de server en zal de **request time verhogen**!

**In plaats van bij elke request de pagina dynamisch op te bouwen wordt dit bij een static site-generator op voorhand gedaan tijdens een build proces**. Eenmaal als het build proces is afgerond kunnen de gecreëerde statische bestanden (HTML, CSS en JS) op een server worden gehost en rechtstreeks worden geleverd aan de eindgebruikers. Er moet geen code meer uitgevoerd worden tijdens de request time. **Dit maakt de response tijd van een website gegenereerd door een SSG (static site generator) veel sneller dan een website met een traditionele aanpak!**

![Werking van een static site-generator - bron Netlify](<../.gitbook/assets/image (135).png>)

### Statische en dynamische websites

Websites kunnen over het algemeen worden onderverdeeld in twee categorieën: **statisch** en **dynamisch**.

{% embed url="https://www.youtube.com/watch?v=_wFJj94kSTU&t=337s&ab_channel=Academind" %}

#### Statische websites

Een statische website lijkt veel op zoals het klinkt: statisch, vast, constant. Dat wil zeggen dat het wordt opgeslagen op een server en in de huidige vorm wordt afgeleverd in de webbrowser van de gebruiker. Het verandert niet tussen het moment waarop de ontwikkelaar op de knop "Opslaan" drukt en het moment waarop de eindgebruiker erop klikt.

Ontwikkelaars maken de inhoud met behulp van **HTML, CSS** en **Javascript.** De Javascript van toepassing in statische websites is uitsluitend bedoeld voor in de webbrowser.

{% hint style="info" %}
Javascript zoals NodeJS, dat op een server wordt uitgevoerd, is hier niet van toepassing!
{% endhint %}

De code dat op de hostingserver staat bestaat uitsluitend uit HTML, CSS en Javascript. Deze wordt in zijn geheel naar de eindgebruiker verstuurt wanneer er een request wordt ingediend. De eindgebruiker zal met **één request** de gehele website te zien krijgen. **Er wordt geen dynamische data achteraf opgehaald.**

#### Dynamische Websites

Dynamische websites zijn in een bijna constante staat van verandering en worden doorgaans aangedreven door een CMS. Het CMS bouwt letterlijk elke pagina op aanvraag elke keer dat een gebruiker deze oproept.

Elke pagina bevat een template waarin er dynamisch data wordt ingeladen. Wanneer een gebruiker een bepaalde dynamische pagina oproept zal de hostingserver de **template** aanroepen en invullen. De server zal **meerdere requests** sturen naar het CMS (of externe services) om de dynamische data op te vragen. Vervolgens zal de server de pagina opbouwen a.d.h.v. de ontvangen dynamische data en stuurt deze ten slotte naar de browser.

#### Single Page Application (SPA) - Extra

Een SPA is een applicatie met **één pagina** die wordt **aangedreven door javascript**. Javascript stuurt server requests uit telkens als de gebruiker nieuwe data opvraagt. Dit wordt ook wel eens **clientside rendering** genoemd. In plaats dat de server de inhoud en de template combineert, en vervolgens het als gehele pagina terugstuurt, wordt de data dynamisch opgehaald vanuit de client en in realtime ingevuld.

Het grootste voordeel van een SPA is de gebruiksvriendelijkheid. De gebruiker hoeft niet meer te wachten op de server om een pagina op te maken en terug te sturen. I.p.d.v. zal de client deze taak op zich nemen waardoor **de snelheid van je applicatie drastisch wordt verbeterd**.

{% hint style="info" %}
**React applicaties zijn SPA's** - Je kan het merken aan de snelle response tijd bij het laden van een "nieuwe pagina". Het is instant, geen wit scherm tussen het navigeren van pagina's!
{% endhint %}

{% embed url="https://www.youtube.com/watch?v=Kg0Q_YaQ3Gk&ab_channel=Academind" %}

### Problemen met CMS-aangedreven websites

Helaas brengen CMS'en een reeks problemen met zich mee waarmee webontwikkelaars voortdurend te maken hebben. Om te beginnen, aangezien ze in populariteit zijn gegroeid, zijn ze **het doelwit geworden van cyberaanvallen**. CMS-software en plugins zijn kwetsbaar voor een groot aantal bekende beveiligingsproblemen. [WP WhiteSecurity](https://www.wpwhitesecurity.com/statistics-highlight-main-source-wordpress-vulnerabilities/) detecteert bijvoorbeeld 2.407 WordPress-kern-, plugin- en themakwetsbaarheden waarmee gebruikers voortdurend te maken hebben - en het aantal groeit voortdurend. [ITPRO](https://www.itpro.co.uk/security/33149/90-of-hacked-cms-sites-in-2018-were-powered-by-wordpress) meldt dat 90% van de gehackte CMS-sites in 2018 werd aangedreven door WordPress, hoewel sites die worden aangedreven door andere CMS-systemen, waaronder Drupal en Joomla, ook kwetsbaar zijn.

En niet alleen beveiliging is een probleem. De prestaties van CMS-sites kunnen ook achteruitgaan omdat de server meer werk doet. **Elke pagina moet worden samengesteld uit templates en inhoud, elke keer dat een verzoek wordt verzonden.** Dit is een erg langzame manier om dingen te doen. Voor elke gebruiker die de site bezoekt, moet de PHP-code die op de server wordt uitgevoerd, opstarten, communiceren met een database, een HTTP-reactie opbouwen op basis van de herstelde gegevens, deze teruggeven aan de webserver, die vervolgens een HTML-bestand retourneert naar de browser van de gebruiker om de inhoud voor weergave te interpreteren.

Al deze stappen verlengen de laadtijd van een webpagina - en voor veel sites zijn ze volkomen overbodig, omdat ze alleen maar **complexiteit, prestatieproblemen en beveiligingsproblemen toevoegen**.

Gelukkig is er een andere manier.

### Voordelen van static sites vs dynamic sites

Een static site-generator is in principe een set tools voor het bouwen van statische websites op basis van een set input files. Static site-generators maken voor ontwikkelaars een statische site die voornamelijk bestaat uit een reeks HTML-pagina's die op een HTTP-server worden geïmplementeerd. In die zin zijn er alleen bestanden en mappen, **dus geen database en geen calls naar een externe backend/server**. Bij het opzetten van een server nemen ontwikkelaars de statische site die is gemaakt door de static site-generator en implementeren deze op de server. Wanneer een gebruiker een pagina opvraagt, vindt de server eenvoudig het overeenkomende bestand en stuurt het terug naar de gebruiker.

{% hint style="info" %}
**M.a.w. er worden geen requests gedaan naar externe services die overbodige complexiteit, prestatieproblemen en beveiligingsproblemen zouden toevoegen**.
{% endhint %}

Dit verschilt enorm van een typische WordPress-site, die talloze databasequery's moet uitvoeren om voor elke afzonderlijke gebruiker een pagina weer te geven. Dit wordt nog erger als er WordPress-plugins worden gebruikt, omdat elke plugin ook toegang moet hebben tot gegevens uit de database. **Met static site-generators worden de snelheid en prestaties daarentegen aanzienlijk verbeterd, omdat de webserver alleen een bestand hoeft te retourneren** - niet een pagina samenstellen die moet worden weergegeven voor elk HTTP-verzoek dat door elke client wordt verzonden. Kortom, dezelfde inhoud hoeft niet steeds opnieuw te worden opgebouwd.

#### Verhoogde beveiliging

Naast snelheid en prestaties lossen static site-generators ook de beveiligingsproblemen op die CMS-aangedreven sites teisteren. Aangezien statische websites uitsluitend uit statische bestanden bestaan, hebben ze geen database - en aangezien er **geen database** is, kunnen aanvallers geen standaard hackaanvallen uitvoeren, zoals scripting, SQL-database-injecties of profiteren van beveiligingslekken in de database aan de serverside.

Bovendien zijn platforms zoals WordPress, die door miljoenen mensen over de hele wereld worden gebruikt, vanzelfsprekend gemeenschappelijke doelwitten geworden voor kwaadwillende aanvallers. Er zijn letterlijk honderden tools die een cybercrimineel gemakkelijk kan downloaden en uitvoeren en die proberen om bestaande WordPress-, Drupal- en Joomla-sites automatisch te compromitteren - simpelweg door alle bekende kwetsbaarheden tegen elk CMS-systeem (en zijn plugins) te doorzoeken, op zoek naar beveiligingslekken. Daarom moeten sitebeheerders hun systemen blijven patchen met beveiligingsupdates en constant kat en muis spelen om ervoor te zorgen dat ze niet worden misbruikt door hackers.

Statische sites zijn daarentegen praktisch onmogelijk te hacken. **Er wordt geen code uitgevoerd - wanneer een gebruiker een pagina opvraagt, de server stuurt alleen een bestand voor die pagina - dus er zijn geen kwetsbaarheden die kunnen worden misbruikt.**

#### Verbeterde kosten en betrouwbaarheid

Een ander voordeel van het gebruik van een static site-generator is de verbeterde betrouwbaarheid. Omdat er geen database is, zal de gevreesde foutmelding '**Failed to establish a database connection**' nooit verschijnen. Bij gebruik van een CMS ontstaan vaak problemen door verkeerspieken, waardoor de database crasht of actieve verbindingen worden beperkt. Met SSG's hoeft de server echter alleen platte HTML-bestanden te hosten en te retourneren, wat betekent dat er onderweg minder kans is dat iets kapot gaat.

Dan is er het kostenvoordeel van SSG's. Het runnen van een statische site is niet duur. Nogmaals, **er is geen database**, en veel minder aan doorlopende ondersteunings- en onderhoudskosten, omdat er minder tijd nodig is om het systeem en de plugins bij te werken, patches toe te passen en back-ups uit te voeren.

#### Versiebeheer

Alle broncode voor een statische site kan in een **version control system zoals Git** leven. Met Git is het mogelijk om terug te gaan naar een enkele versie van de site in zijn hele geschiedenis. Hierdoor blijven oude bestanden behouden en kunnen gemaakte wijzigingen of fouten snel ongedaan worden gemaakt of gecorrigeerd. **CMS-databases zijn daarentegen extreem vluchtig**. Elke gebruiker met de juiste machtigingen kan in een opwelling inhoud toevoegen, wijzigen of permanent verwijderen. Het is waar dat je een back-up kunt (en zou moeten maken) van databases, maar zelfs als dit regelmatig wordt gedaan, is de kans groot dat sommige gegevens verloren gaan als iemand een fout maakt of als een aanvaller zijn / haar weg naar binnen vindt.

Een version control system dient als een zeer betrouwbare externe back-up. Het is altijd mogelijk om met een paar toetsaanslagen terug te gaan naar een vorige versie van de site, aangezien alle benodigde bestanden zich in de opslagplaats van het version control system bevinden.

### Een static site-generator is niet altijd de beste optie

Static site-generators bieden een oplossing waarmee bedrijven **een zeer veilige, snelle, schaalbare en flexibele** website kunnen maken. Maar hoewel ze inderdaad de voordelen bieden van zowel de CMS als de static site-wereld, zijn ze niet per se geschikt voor elk project, en er zijn een aantal dingen die je zeker moet overwegen vooraleer je een SSG gebruikt.

Om te beginnen lijken static site-generators misschien ingewikkeld voor niet-programmeurs, en het is waar dat je niet ver komt met een SSG zonder enige ontwikkelingsexpertise aan boord. En hier is nog een knelpunt: de community van static site-generators is nog relatief nieuw en daarom klein in vergelijking met bijvoorbeeld de WordPress-ondersteuningen die er zijn. Relatief, omdat de community van SSG's zoals Gatsby enorm snel aan het groeien zijn.

Bovendien kunnen niet-technische gebruikers met populaire CMS-systemen zoals WordPress hun site gemakkelijk beheren en bewerken - er zijn **talloze kant-en-klare WordPress-thema's beschikbaar voor het bouwen van sites**, en zelfs meer plugins die eenvoudige aanpassing mogelijk maken. Als je daarentegen met een static site-generator werkt, hebben niet-technische mensen waarschijnlijk wat hulp nodig bij de installatie en het gebruik van de technologie.

**Grote sites met honderden of duizenden pagina's kunnen ook moeilijk te beheren zijn met een static site-generator**. Hoewel het mogelijk is, als je bijvoorbeeld meerdere auteurs op meerdere locaties hebt die allemaal regelmatig meerdere artikelen of blogposts bijdragen, wordt het bewerken en publiceren van inhoud een stuk lastiger en tijdrovender met een static site generator. Dit omdat er bij elke bewerking de HTML pagina's opnieuw moeten worden gebouwd. Realtime updates kunnen worden vertraagd en de bouwtijd kan snel toenemen.

En als je een volledig dynamische website nodig hebt waarvan de inhoud van bepaalde pagina's (zoals user admin panels) niet vooraf bekend en gegenereerd kan worden, zijn static site-generators waarschijnlijk niet de beste optie.

### Conclusie

Voor sites die niet de functionaliteit van een dynamische website nodig hebben, bieden static site-generators een hele reeks voordelen. De meeste websites overschrijden zelden enkele tientallen pagina's, en zelfs degenen die niet vaak moeten worden bijgewerkt. Als zodanig is een CMS vaak overkill, wat de prestaties van de site beïnvloedt, de site blootstelt aan beveiligingsrisico's en de kosten verhoogt.

**Met static site-generator zijn er minder bewegende delen, wat de snelheid en prestaties aanzienlijk verbetert.** Ze zijn ook zeer veilig, zeer betrouwbaar, worden steeds krachtiger, vergen minimale onderhoudsinspanning en kosten minder geld om te bedienen. Om deze redenen kunnen we in de toekomst verwachten dat het SSG-gebruik verder zal groeien, evenals verbeteringen van providers die ze gemakkelijk te gebruiken maken voor niet-technische gebruikers.
