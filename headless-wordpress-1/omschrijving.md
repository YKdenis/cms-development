---
description: >-
  Hoe geweldig WordPress ook is, in sommige gevallen heb je misschien nog meer
  flexibiliteit nodig. In dat geval kan het nuttig zijn om WordPress te
  gebruiken als een headless CMS.
---

# Headless WordPress

WordPress als Content Management Systeem (CMS) is een krachtig platform waarmee je inhoud/content gemakkelijk kunt maken, beheren en bijwerken zonder dat je veel moet kennen van coderen.

Maar hoe geweldig WordPress als monolitisch CMS ook is, in sommige gevallen heb je misschien nog meer flexibiliteit nodig. In dat geval kan het nuttig zijn om WordPress te gebruiken als een headless CMS. Hieronder zullen we alles omtrent Headless WordPress bespreken. Van de fundamentele begrippen, de pro's en cons tot scenario's waarin je het kan toepassen.

## Wat is Headless WordPress? <a href="#yui_3_17_2_1_1622719799529_34" id="yui_3_17_2_1_1622719799529_34"></a>

Zoals eerder besproken bestaat een monolitische CMS uit twee delen:&#x20;

* de front-end;
* de back-end;

Aan de back-end komt het gedeelte "**beheer**" om de hoek kijken. In WordPress maak en publiceer je blogposts en pagina's, en beheer je verschillende aspecten van je website, zoals instellingen, uiterlijk en andere gebruikers.

Hopelijk herinner je het dashboard hieronder nog van vorig jaar!

![Dashboard in WordPress (back-end)](<../.gitbook/assets/image (2).png>)

De front-end is wat mensen zien wanneer ze je website bezoeken. In WordPress verandert het uiterlijk van je website door achter de schermen pagina's, instellingen, je thema, etc aan te passen.

&#x20;De front-end vraagt gegevens op van de verborgen back-end met behulp van een [REST API](https://restfulapi.net/). Als je iets aanpast in je back-end (dashboard van WP), wordt dit automatisch gereflecteerd in de front-end.

![Website in WordPress (front-end)](<../.gitbook/assets/image (108).png>)

Voor de meeste gebruikers werkt deze gekoppelde CMS-oplossing goed en biedt zowel een manier om eenvoudig een website te bouwen als geschreven inhoud te beheren. Het nadeel is dat de front-end en back-end van dit type applicatie vaak **onafscheidelijk zijn omdat ze zo sterk van elkaar afhangen**.

Een headless WordPress CMS ontkoppelt deze twee delen in namelijk de back-end en de front-end. **De front-end zal niet meer worden gebruikt** waardoor alleen de back-end intact blijft. Je behoudt je database, admin-paneel en tools voor contentbeheer. M.a.w. we zullen de dashboard in WordPress blijven gebruiken maar het gebruik van de WordPress front-end valt weg.&#x20;

We moeten ons niet druk maken over de manier waarop onze content wordt weergegeven. **We zullen geen sjablonen of visuele thema's gebruiken**.

Met behulp van een API kan je de data die je instelt in de back-end omzetten in endpoints. Met andere woorden je **WordPress back-end kan worden gebruikt als** [**API**](https://en.wikipedia.org/wiki/API) **om data op te vragen**. Aan deze API kan je van alles koppelen: een applicatie geschreven in React Native of Ionic, een op maat gemaakte website in Vue, React of Gatsby en de lijst gaat maar door. De implicaties hiervan zijn enorm voor ontwikkelaars!

{% hint style="info" %}
Vorig jaar heb je gewerkt met WordPress als een gekoppelde (monolitische) CMS, dit jaar gaan we alleen de back-end van WordPress gebruiken. M.a.w. we zullen werken met het dashboard hierboven en deze omzetten in een API en vervolgens koppelen aan een externe front-end.
{% endhint %}
