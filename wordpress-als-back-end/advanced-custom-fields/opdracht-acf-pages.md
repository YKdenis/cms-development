---
description: >-
  Voor onze agency website zullen we 4 pagina's creëren: home, artists, about us
  en contact us. Aan deze pagina's geven we extra metadata mee die we later via
  onze API kunnen opvragen in onze front-end!
---

# Opdracht ACF - Pages

## Aanmaken van de nieuwe pagina's

Navigeer naar Pages in je WordPress werkbalk en voeg 4 nieuwe pagina's toe en verwijder de Privacy Policy en de Sample Page.

* Home
* About us
* Contact us
* Artists
* ~~Privacy Policy~~
* ~~Sample Page~~

![](../../.gitbook/assets/image%20%28127%29.png)

![](../../.gitbook/assets/image%20%2887%29.png)

We hebben de Sample Page verwijderd terwijl er nog een field group aanhing. Navigeer terug naar Custom fields en zet de Sample Page Fields op inactive. 

_Je mag de Sample Page Fields ook verwijderen maar het kan handig zijn als referentie voor later._

![](../../.gitbook/assets/image%20%28117%29.png)

## Toevoegen van een field group aan elke pagina

Als opdracht zullen jullie voor elke pagina een nieuwe field group moeten aanmaken en daaraan metadata meegeven. **\* is required.**

* Home Page Fields
  * Header Home\* **\(Group\)**
    * Title\* **\(Text\)**
    * Picture\* **\(Image\)**
    * Description\* **\(Textarea\)**
  * Call To Action\* **\(Group\)**
    * Link\* **\(URL\)**
    * Link Text\* **\(Text\)**
  * Featured Artists\* **\(Group\)**
    * Title\* **\(Text\)**
    * Description\* **\(Textarea\)**
    * Artists\* **\(Post Object\)**
* About Page Fields
  * Header About Us\* **\(Group\)**
    * Title\* **\(Text\)**
    * Picture\* **\(Image\)**
    * Description\* **\(Textarea\)**
  * Mission\* **\(Group\)**
    * Title\* **\(Text\)**
    * Banner Picture\* **\(Image\)**
    * Description\* **\(Textarea\)**
* Contact Page Fields
  * Header Contact\* **\(Group\)**
    * Title\* **\(Text\)**
    * Picture\* **\(Image\)**
    * Description\* **\(Textarea\)**
  * Company Information\* **\(Group\)**
    * Email\* **\(Email\)**
    * Phone Number\* **\(Text\)**
    * Address\* **\(Text\)**
    * Postcode\* **\(Number\)**
    * City\* **\(Text\)**
    * Socials\* **\(Group\)**
      * Instagram\* **\(URL\)**
      * Twitter\* **\(URL\)**
      * Facebook\* **\(URL\)**
* Artists Page Fields
  * Header Artists\* **\(Group\)**
    * Title\* **\(Text\)**
    * Picture\* **\(Image\)**
    * Description\* **\(Textarea\)**

Vergeet niet voor elke field group de correcte Location toe te voegen. M.a.w. de correcte conditionele regels voor het koppelen van de field group aan de correcte pagina.

Je kan uittesten of je conditionele regels correct zijn ingesteld door te navigeren naar het bewerkingsscherm van de pagina en te checken of de field group degelijk zichtbaar is.

## Oplossing

De correcte oplossing zal in les 3 op Digitap worden gezet!

Nu dat je de correcte structuur hebt voorzien voor de field group mag je voor alle pagina's de metadata invullen! Gebruik hiervoor echte data of dummy data dat de grote van elk inputveld reflecteert. 4 woorden voor een description is niet voldoende!

Je kan hiervoor een Lorem Ipsum generator gebruiken. Er zijn verschillende gratis generators te vinden op het internet! 



