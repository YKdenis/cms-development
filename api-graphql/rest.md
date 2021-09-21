---
description: >-
  REST (afkorting van representational state transfer) is gebaseerd op een
  vooraf gedefinieerde reeks staatloze bewerkingen waarmee gebruikers toegang
  hebben tot webgegevens en deze kunnen manipuleren.
---

# REST API \| voor- en nadelen

#### Wat is REST?

Het architecturale principe van REST wordt al meer dan tien jaar gebruikt door ontwikkelaars. Het vereenvoudigt de communicatie tussen machines en ondersteunt vele gegevensformaten, zoals JSON, XML of YAML. Ondanks het feit dat het duidelijk een van de meest populaire benaderingen is in de bedrijven van vandaag, met steun van grote giganten zoals Google en Netflix, heeft het nog steeds bepaalde gebreken die de toepasbaarheid ervan beperken.

REST \(afkorting van **RE**presentational **S**tate **T**ransfer\) is gebaseerd op een uniforme en vooraf gedefinieerde reeks staatloze bewerkingen waarmee gebruikers toegang hebben tot webgegevens en deze kunnen manipuleren. API's die voldoen aan REST-ontwerpprincipes worden meestal **RESTful API's** genoemd.

In REST-architectuur stellen API's hun functionaliteit bloot als bronnen, dit zijn alle soorten services, gegevens of objecten waartoe een client toegang heeft. Elke bron wordt geleverd met zijn eigen unieke URI \(Uniform Resource Identifier\) waartoe een client toegang kan krijgen door een verzoek naar de server te sturen.

{% hint style="info" %}
Een bepaalde bron van een API wordt ook wel eens een endpoint genoemd!
{% endhint %}

Dus wanneer een client een RESTful API aanroept, reageert de server met een weergave van de status van de opgevraagde bron. Veel gangbare REST-implementaties gebruiken de standaard HTTP-methoden \(GET, POST, PUT, DELETE en PATCH\) om een server aan te roepen.

{% hint style="info" %}
Dit betekent dat wanneer een RESTful API wordt aangeroepen, de server een weergave van de status van de aangevraagde bron naar de client zal overdragen.
{% endhint %}

#### SWAPI REST API voorbeeld

SWAPI is een API voor het ophalen van alle gegevens uit het Star Wars universum en een perfect voorbeeld om de werking van REST uit te leggen.

Een REST API kan je aanroepen door een bepaalde URI aan te spreken. In het geval van Swapi is dit: [https://swapi.dev/api/](https://swapi.dev/api/)

Je kan bepaalde resources opvragen door achter `api/` iets op te geven. Je kan daar natuurlijk niet zo maar iets typen, er zijn hiervoor bepaalde endpoints voor voorzien. Je kan alle endpoints terugvinden in de [documentatie](https://swapi.dev/documentation) van Swapi.

Voor het ophalen van alle personen in Star Wars kan je het endpoint [https://swapi.dev/api/people/](https://swapi.dev/api/people/) gebruiken. Indien je 1 persoon wilt opvragen dan kan je dat doen a.d.h.v. een ID. 

* `/people/` -- Fetch alle personen
* `/people/:id/` -- Fetch een specifieke persoon

Laten we samen als voorbeeld de persoon met id 1 ophalen. We krijgen een object terug met data van Luke Skywalker.

{% code title="GET https://swapi.dev/api/people/1/" %}
```yaml
HTTP 200 OK
Content-Type: application/json
Vary: Accept
Allow: GET, HEAD, OPTIONS

{
    "name": "Luke Skywalker", 
    "height": "172", 
    "mass": "77", 
    "hair_color": "blond", 
    "skin_color": "fair", 
    "eye_color": "blue", 
    "birth_year": "19BBY", 
    "gender": "male", 
    "homeworld": "http://swapi.dev/api/planets/1/", 
    "films": [
        "http://swapi.dev/api/films/1/", 
        "http://swapi.dev/api/films/2/", 
        "http://swapi.dev/api/films/3/", 
        "http://swapi.dev/api/films/6/"
    ], 
    "species": [], 
    "vehicles": [
        "http://swapi.dev/api/vehicles/14/", 
        "http://swapi.dev/api/vehicles/30/"
    ], 
    "starships": [
        "http://swapi.dev/api/starships/12/", 
        "http://swapi.dev/api/starships/22/"
    ], 
    "created": "2014-12-09T13:50:51.644000Z", 
    "edited": "2014-12-20T21:17:56.891000Z", 
    "url": "http://swapi.dev/api/people/1/"
}
```
{% endcode %}

Zoals je hierboven te zien krijgt, worden er bij sommige object keys een URI of een array van URI's terug. Bv. de '`homeworld`' van Luke Skywalker heeft als waarde "`http://swapi.dev/api/planets/1/`"

Indien we de data van de `homeworld` willen opvragen moeten we het boven vernoemde endpoint aanspreken.

{% code title="GET https://swapi.dev/api/planets/1/" %}
```yaml
HTTP 200 OK
Content-Type: application/json
Vary: Accept
Allow: GET, HEAD, OPTIONS

{
    "name": "Tatooine", 
    "rotation_period": "23", 
    "orbital_period": "304", 
    "diameter": "10465", 
    "climate": "arid", 
    "gravity": "1 standard", 
    "terrain": "desert", 
    "surface_water": "1", 
    "population": "200000", 
    "residents": [
        "http://swapi.dev/api/people/1/", 
        "http://swapi.dev/api/people/2/", 
        "http://swapi.dev/api/people/4/", 
        "http://swapi.dev/api/people/6/", 
        "http://swapi.dev/api/people/7/", 
        "http://swapi.dev/api/people/8/", 
        "http://swapi.dev/api/people/9/", 
        "http://swapi.dev/api/people/11/", 
        "http://swapi.dev/api/people/43/", 
        "http://swapi.dev/api/people/62/"
    ], 
    "films": [
        "http://swapi.dev/api/films/1/", 
        "http://swapi.dev/api/films/3/", 
        "http://swapi.dev/api/films/4/", 
        "http://swapi.dev/api/films/5/", 
        "http://swapi.dev/api/films/6/"
    ], 
    "created": "2014-12-09T13:50:49.641000Z", 
    "edited": "2014-12-20T20:58:18.411000Z", 
    "url": "http://swapi.dev/api/planets/1/"
}
```
{% endcode %}

Je zal niet altijd alle data nodig hebben van een persoon. Het is dus onnodig om bij elke request de hele waslijst van gegevens te retourneren. 

In plaats daarvan geeft SWAPI voor sommige velden een URI terug die op haar beurt kan worden aangeroepen indien de consument toch meer informatie wenst. Door niet alle data in een request terug te sturen los je het probleem van overfetching op.

Het principe van URI's terug te sturen als data is een good practice voor het bouwen van REST API's. **één groot nadeel is wel dat je verschillende endpoints moet aanspreken indien je toch bepaalde informatie nodig hebt.** Er zullen dus meerdere roundtrips naar de server worden gedaan waardoor de performantie van je front-end aftakelt!

#### Overfetching en Underfetching

Overfetching treedt op wanneer een eindpunt overbodige gegevens retourneert dan eigenlijk nodig is. Omgekeerd houdt underfetching in dat een eindpunt niet voldoende van de vereiste gegevens kan retourneren.

* **Overfetching:** treedt op wanneer een endpoint overbodige gegevens retourneert dan eigenlijk nodig is.
* **underfetching:** houdt in dat een endpoint niet voldoende van de vereiste gegevens kan retourneren.

Aangezien een REST-API een gegevensstructuur heeft die ontworpen is om voorgeschreven gegevens te retourneren, kan je onnodige gegevens krijgen of gedwongen worden om meerdere roundtrips naar de server te doen voordat je de relevante gegevens krijgt. **Deze tekortkomingen vergroten ook de tijd die de server nodig heeft om alle gevraagde informatie terug te sturen.**

#### **Nadelen van een REST API:**

* Je hebt veel endpoints, wordt snel onoverzichtelijk. 
* Je moet de tijd nemen om documentatie te schrijven zodat ontwikkelaars je API kunnen leren en gebruiken.
* Er wordt te veel of te weinig informatie opgehaald \(**overfetching**, **underfetching**\). Beslissen tussen underfetching, creëren van veel endpoints m.a.w. veel roundtrips naar de server, of overfetching van data m.a.w. endpoints aanspreken die de data die je nodig hebt terug sturen plus een extra overhead aan data.

### Conclusie

REST wordt al meer dan twee decennia gebruikt en heeft er voor gezorgd dat de implementatie van de client en de implementatie van de server onafhankelijk worden gedaan zonder dat ze van elkaar weten. **Dit betekent dat de front-end code op elk moment kan worden gewijzigd zonder de werking van de server te beïnvloeden, en de back-end code kan worden gewijzigd zonder de werking van de client te beïnvloeden**.

Door een REST-API te gebruiken, kunnen verschillende clients \(front-ends\) dezelfde REST-endpoints aanspreken en dus dezelfde data opvragen van, en wijzigen in de databank.

REST heeft het programmeer landschap drastisch veranderd in de positieve zin! Het heeft de security, scalability en performance van applicaties verbeterd als de interoperabiliteit en herbruikbaarheid.

We zijn nu 20 jaar verder en er zijn nieuwe innovatieve technologieën in opkomst die dezelfde functie als REST invullen maar dan beter. In het volgende hoofdstuk zullen we een van de snelst opkomende technologieën bespreken namelijk GraphQL. GraphQL kan de nadelen van REST, zoals hierboven besproken, rechtzetten.



