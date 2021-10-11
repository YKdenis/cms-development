---
description: >-
  In het deel over custom posts hebben we een entiteit aangemaakt voor Artists.
  Laten we hiervoor een Field Group maken en elke artist standaard bepaalde
  metagegevens meegeven.
---

# Opdracht ACF - Artist Fields

We hebben eerder een custom post type aangemaakt voor het creëren van artiesten. Momenteel heeft elke artiest alleen standaard metagegevens van een post uit WordPress. Deze metagegevens zijn afgestemd voor het aanmaken van blog posts niet voor het aanmaken van artiesten. Wij willen graag dat elke artiest een set custom fields krijgt die we later via onze API kunnen doorsluizen naar onze zelfgemaakte front-end.

Nu is het aan jullie! Verken de ACF documentatie en maak de volgende oefening.

#### **Volg het stappenplan hieronder: **

1. Maak een nieuwe field group aan en geef het de naam **Artist Fields;**
2. Koppel de field group aan de** custom post type** Artist;
3. Geef de field group volgende custom fields **(\* is required)**:
   1. First Name\* **(Text)**
   2. Last Name\* **(Text)**
   3. Artist Name **(Text)**
   4. Email\* **(Email)**
   5. Phone Number **(Text)**
   6. Description\* **(Textarea)**
   7. Height **(Number)**
   8. Origin **(Text)**
   9. Shoe Size **(Range)**
   10. Shirt Size** (Select)**
   11. Pictures **(Group)**
       1. Picture 1 **(Image)**
       2. Picture 2 **(Image)**
       3. Picture 3** (Image)**
   12. Profile Picture\* **(Image)**

Je kan de documentatie voor elke Field Type [hier](https://www.advancedcustomfields.com/resources/) raadplegen! 

Tweak elke custom field naar maximale gebruiksvriendelijkheid en flexibiliteit. Soms zal je flexibiliteit moeten opgeven voor gebruiksvriendelijkheid en vice versa. Help gebruikers met het vermijden van fouten maar zorg ervoor dat ze genoeg vrijheid behouden om flexibel te werk te gaan.

_**Bv. een maximum file size op een image zetten.** Je helpt de gebruiker met het behouden van een snelle website. Maar indien je de maximum file size te klein zet dan belemmer je hun in het snel aanmaken van content!_

## Oplossing

De correcte oplossing zal in les 3 op Digitap worden gezet!

Nu dat je de correcte structuur hebt voorzien voor de field group mag je een vijftal artiesten toevoegen. Je kan dit doen door te navigeren naar de artist tab in je WordPress werkbalk en op '**New Artist**' te klikken. Je zal een bewerkingsscherm te zien krijgen met alle inputvelden die we hebben toegevoegd met de field group van ACF. 



