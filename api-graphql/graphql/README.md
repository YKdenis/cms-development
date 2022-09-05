---
description: >-
  GraphQL is een nieuwe API-standaard die een efficiënter, krachtiger en
  flexibeler alternatief biedt voor REST.
---

# GraphQL API | voor- en nadelen

Het is ontwikkeld en open source gemaakt door Facebook en wordt nu onderhouden door een grote gemeenschap van bedrijven en individuen van over de hele wereld.

Je kan een GraphQL-query zien als een GET-verzoek in REST. GraphQL-query's worden gebruikt om net zoals bij REST gegevens die de client nodig heeft op te vragen.

GraphQL maakt het **declaratief** ophalen van gegevens mogelijk, waarbij een client precies kan specificeren welke gegevens hij nodig heeft van een API. In plaats van meerdere endpoints die vaste datastructuren retourneren, stelt een GraphQL-server slechts **één endpoint** bloot en reageert met precies de data waar een gebruiker om vraagt.

{% hint style="info" %}
**Declaratief programmeren** is een programmeer paradigma waarbij de code voor zich spreekt. Je kan de functionaliteit afleiden uit de manier waarop de code geschreven is.
{% endhint %}

GraphQL wordt vaak verward met een databasetechnologie. Dit is een misvatting, **GraphQL is een zoektaal voor API's** - niet voor databases. In die zin is het **database-agnostisch** en kan het effectief worden gebruikt in elke context waarin een API wordt gebruikt. M.a.w. je kan gegevens ophalen vanuit eender welke soort databasetechnologie MySQL, MongoDB, Redis, Neo4j, …

### Het verschil tussen REST en GraphQL

GraphQL is ontwikkeld met de behoefte aan **meer flexibiliteit en efficiëntie** te voldoen! Het lost veel van de tekortkomingen en inefficiënties op die ontwikkelaars ervaren bij interactie met REST API's.

De oplossing die Facebook bedacht is conceptueel heel eenvoudig: in plaats van **meerdere endpoints** te hebben, moet je **een enkel endpoint** hebben dat complexe requests kan verwerken en vervolgens alleen de gegevens terugstuurt dat de gebruiker nodig heeft. Er zal **geen overhead zijn aan gegevens**. M.a.w. het probleem van overfetching, waarmee de meeste REST API's kampen, wordt opgelost.

### Voorbeeld REST vs GraphQL

Om de belangrijkste verschillen tussen REST en GraphQL te illustreren, als het gaat om het ophalen van gegevens uit een API, laten we een eenvoudig voorbeeld bekijken: 

{% hint style="success" %}
in een blogtoepassing moet een app de titels van de berichten van een specifieke gebruiker weergeven. Hetzelfde scherm toont ook de namen van de laatste 3 volgers van die gebruiker. Hoe zou die situatie worden opgelost met REST en met GraphQL?
{% endhint %}

#### **REST**

Met een REST API verzamel je de gegevens doorgaans door toegang te krijgen tot meerdere endpoints. In het voorbeeld zou dit een `/users/<id> `endpoint kunnen zijn om de initiële gebruikersgegevens op te halen. Ten tweede is er waarschijnlijk een `/users/<id>/posts/` endpoint dat alle posts voor een gebruiker retourneert. Het derde endpoint is de `/users/<id>/followers/` die een lijst met volgers per gebruiker retourneert.

![](<../../.gitbook/assets/image (60).png>)

Met REST moet je drie verzoeken doen aan verschillende endpoints om de vereiste gegevens op te halen. Je haalt ook te veel gegevens op omdat de endpoints aanvullende informatie retourneren die niet we in de front-end niet zullen gebruiken. M.a.w. er wordt aan **overfetching** gedaan!

#### GraphQL

In GraphQL daarentegen, stuur je** één enkele query** naar de GraphQL-server waarin je concreet vermeld welke data je nodig hebt. De server reageert vervolgens met een JSON-object dat alleen de gevraagde data bevat.

![](<../../.gitbook/assets/image (61).png>)

aan de hand van een query kan de gebruiker in GraphQL precies de gegevens specificeren die hij/zij nodig heeft. In de bovenstaande foto wordt er een query geleverd aan de GraphQL-server met daarin de vraag achter specifieke informatie van de user. **De client ontvangt vervolgens precies de informatie die hij/zij in de query heeft gedefinieerd** en niets meer, waardoor **overfetching** gegevens wordt **vermeden**. Merk op dat de structuur van het antwoord van de server precies de geneste structuur volgt die in de query is gedefinieerd.

Daarbij wordt er maar **één request** naar de server gestuurd en wordt het probleem van **underfetching vermeden**.

### Voordelen van GraphQL

GraphQL zorgt ervoor dat de verschillende pijnpunten waarmee REST kampt worden opgelost. Met GraphQL **vermijd je overfetching en underfetching **door het gebruik van een voorgedefinieerd schema. Je moet maar **één endpoint** aanspreken, m.a.w. één request sturen naar de server, en je krijgt alleen de gevraagde data terug. **Geen overhead van data** en geen complexe kettingreacties van requests naar verschillende endpoints. Dit maakt het voor de front-end developer veel aangenamer en gemakkelijker om data vanuit de server op te vragen en te verwerken in de front-end.

GraphQL werkt met een **voorgedefinieerd schema **die de structuur van de opvraagbare data bevat. Dit maakt de API zeer eenvoudig te begrijpen en gemakkelijk te gebruiken. Je kan een schema in GraphQL zien als de documentatie waarmee de front-end developer te weten kan komen hoe hij/zij data kan opvragen van de server. M.a.w. er is nogmaals een vermindering van complexiteit voor de front-end developers!

* Duidelijke documentatie die out of the box wordt voorzien;
* Geen overhead van data in de responds van de server;
* Er moet maar één endpoint aangesproken worden m.a.w. één roundtrip naar de server en terug;

### Nadelen van GraphQL

Als GraphQL alleen maar voordelen heeft tegenover REST dan werd REST hoogstwaarschijnlijk al lang niet meer gebruikt. Het kiezen tussen een GraphQL of REST API hangt af van de use case waarin de API zal worden gebruikt.

#### Serverside Complexiteit

Een groot nadeel is dat **alle complexiteit op de schouders van de back-end developers valt**. Een GraphQL API maakt het gemakkelijk voor de front-end developers. Hoe data wordt opgevraagd, gewijzigd en verwijderd kan afgeleid worden uit het GraphQL schema. 

De back-end developers daarin tegen moeten er voor zorgen dat de databank structuur in één overzichtelijk en gemakkelijk te gebruiken schema wordt gegoten. Hoe groter het project, hoe ingewikkelder dit wordt. Je centraliseert alles tot één geheel, één GraphQL schema. Als er zich ooit een fout optreedt dan is de kans groot dat heel de werking van de API wordt belemmerd.

#### Stijle Leercurve

Een ander nadeel is dat de werking van GraphQL heel anders is dan dat van REST. In GraphQL schrijf je queries waarmee je data kan opvragen en mutaties om data weg te schrijven. Buiten deze twee nieuwe termen moet de ontwikkelaar ook verschillende begrippen leren zoals query-argumenten, fragmenten, etc.Het kan even duren vooraleer nieuwe developers er mee weg zijn.

#### POST requests

Alle requests van GraphQL zijn POST requests. Zelfs als je data opvraagt zal GraphQL dit behandelen als een POST. Dit heeft als nadeel dat de browser niet automatisch de opgevraagde gegevens cached. Ook al is de data al eens vanuit de server opgevraagd toch zal GraphQL hiervoor een request naar de server sturen. 

Er zijn hiervoor natuurlijk oplossingen voorzien zoals [Apollo GraphQL](https://www.apollographql.com) maar dan ben je weer afhankelijk van een externe partij om je data weg te schrijven naar je lokale cache. Je kan Apollo vergelijken met wat JQuery is voor Javascript. Het is super handig en eenvoudig maar het kan snel omkeren en limiterend worden of bizarre errors gooien.

### Conclusie

GraphQL lost de pijnpunten van REST op maar brengt andere kwesties met zich mee zoals serverside complexiteit en een stijle leercurve. Afhankelijk van het project zal je moeten kiezen tussen beide technologieën.

{% hint style="info" %}
In de praktijk wordt GraphQL over REST gekozen voor **interne applicaties**. Applicaties waarbij de backend en de frontend door hetzelfde bedrijf worden beheerd. Als er een API wordt gemaakt voor **externe bedrijven** dan kiest men hoofdzakelijk voor een REST API.
{% endhint %}

* **GraphQL -> Private API's**
* **REST -> Public API's**

Dit heeft te maken met de server complexiteit van GraphQL. Met REST kan je meerdere endpoints aanspreken. Als er een endpoint eens niet werkt dan is dat geen ramp. Bij GraphQL centraliseer je alle data en geef je deze vrij via één endpoint. M.a.w. de kans dat de gehele API plat ligt is veel groter. Als je API wordt gebruikt door verschillende externe bedrijven is dit iets dat je echt niet wilt meemaken!

Met GraphQL kan je snel een flexibele en efficiënte API opzetten. Voor interne applicaties is dit perfect. Het duidelijk en leesbaar schema helpt werknemers snel data op te vragen en weg te schrijven. Als je weet waarvoor de API wordt gebruikt dan kan je het schema hier perfect op afstellen. 

{% hint style="info" %}
Facebook, de maker van GraphQL, gebruikt voor haar externe services nog steeds REST. Alleen voor interne services gebruiken ze GraphQL. 
{% endhint %}

_**Raadpleeg de GraphQL website via deze link **_[_**graphql.org**_](https://graphql.org)_** indien je meer informatie wenst omtrent de query language.**_

{% embed url="https://www.youtube.com/watch?v=sdqBPtXClHI&t=1s&ab_channel=RapidAPI" %}
