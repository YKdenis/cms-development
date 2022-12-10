---
description: >-
  Voor onze agency website zullen we 4 pagina's creëren: home, artists, about us
  en contact us. Aan deze pagina's geven we extra metadata mee die we later via
  onze API kunnen opvragen in onze front-end!
---

# Opdracht ACF - Page Fields

## Aanmaken van de nieuwe pagina's

Navigeer naar Pages in je WordPress werkbalk en voeg 4 nieuwe pagina's toe en verwijder de Privacy Policy en de Sample Page.

* Home
* About us
* Contact us
* Artists
* ~~Privacy Policy~~
* ~~Sample Page~~

![](<../../.gitbook/assets/image (127).png>)

![](<../../.gitbook/assets/image (87) (1).png>)

We hebben de Sample Page verwijderd terwijl er nog een field group aanhing. **Navigeer terug naar Custom fields en zet de Sample Page Fields op inactive onder de Group Settings tab.**

{% hint style="info" %}
Je mag de Sample Page Fields ook verwijderen maar het kan handig zijn als referentie voor later.
{% endhint %}

## Toevoegen van een field group aan elke pagina

Als opdracht zullen jullie voor elke pagina een nieuwe field group aanmaken en daaraan metadata meegeven. **\* is required.**

Raadpleeg de [ACF documentatie](https://www.advancedcustomfields.com/resources/).

{% tabs %}
{% tab title="Home Fields" %}
### **Home Fields**

1. Maak een nieuwe field group aan en geef het de naam **Home Fields;**
2. Koppel de field group aan de **Home** pagina;
   1. Je kan conditionele regels toevoegen in de sectie '**Location**';
   2. **Page** is equal to **Home**;
3. Geef de field group volgende custom fields **(\* is required)**:
   1. **Title\***
      * Field Name: title
      * Field Type: Text
   2. **Picture\***
      * Field Name: picture
      * Field Type: image
      * Return Format: Image Array
      * Maximum File Size: 5MB
      * Allowed File Types: jpg, jpeg, png
   3. **Description\***
      * Field Name: description
      * Field Type: Text Area
      * New Lines: Automatically add paragraphs
   4. **Call To Action\***
      * Field Name: call\_to\_action
      * Field Type: Link
   5. **Artists\***
      * Field Name: artists
      * Field Type: Post Object
      * Filter By Post Type: Artist
      * Select Multiple Values: true
      * Return Format: Post Object
{% endtab %}

{% tab title="About Us Fields" %}
### **About Us Fields**

1. Maak een nieuwe field group aan en geef het de naam **About Us Fields;**
2. Koppel de field group aan de **About Us** pagina;
   1. Je kan conditionele regels toevoegen in de sectie '**Location**';
   2. **Page** is equal to **About Us**;
3. Geef de field group volgende custom fields **(\* is required)**:
   1. **Goal Title\***
      * Field Name: goal\_title
      * Field Type: Text
   2. **Goal Picture\***
      * Field Name: goal\_picture
      * Field Type: image
      * Return Format: Image Array
      * Maximum File Size: 5MB
      * Allowed File Types: jpg, jpeg, png
   3. **Goal Description\***
      * Field Name: goal\_description
      * Field Type: Text Area
      * New Lines: Automatically add paragraphs
   4. **Mission Title\***
      * Field Name: mission\_title
      * Field Type: Text
   5. **Mission Picture\***
      * Field Name: mission\_picture
      * Field Type: image
      * Return Format: Image Array
      * Maximum File Size: 5MB
      * Allowed File Types: jpg, jpeg, png
   6. **Mission Description\***
      * Field Name: mission\_description
      * Field Type: Text Area
      * New Lines: Automatically add paragraphs
{% endtab %}

{% tab title="Contact Us Fields" %}
### **Contact Us Fields**

1. Maak een nieuwe field group aan en geef het de naam **Contact Us Fields;**
2. Koppel de field group aan de **Contact Us** pagina;
   1. Je kan conditionele regels toevoegen in de sectie '**Location**';
   2. **Page** is equal to **Contact Us**;
3. Geef de field group volgende custom fields **(\* is required)**:
   1. **Title\***
      * Field Name: title
      * Field Type: Text
   2. **Picture\***
      * Field Name: picture
      * Field Type: image
      * Return Format: Image Array
      * Maximum File Size: 5MB
      * Allowed File Types: jpg, jpeg, png
   3. **Description\***
      * Field Name: description
      * Field Type: Text Area
      * New Lines: Automatically add paragraphs
   4. **Email\***
      * Field Name: email
      * Field Type: Email
   5. **Phone Number\***
      * Field Name: phone\_number
      * Field Type: Text
   6. **Address\***
      * Field Name: address
      * Field Type: Text
   7. **Zip Code\***
      * Field Name: zip\_code
      * Field Type: Text
   8. **City\***
      * Field Name: city
      * Field Type: Text
   9. **Instagram\***
      * Field Name: instagram
      * Field Type: URL
   10. **Twitter\***
       * Field Name: twitter
       * Field Type: URL
   11. **Facebook\***
       * Field Name: facebook
       * Field Type: URL
{% endtab %}

{% tab title="Artists Fields" %}
### Artists Fields

1. Maak een nieuwe field group aan en geef het de naam **Artists Fields;**
2. Koppel de field group aan de **Artists** pagina;
   1. Je kan conditionele regels toevoegen in de sectie '**Location**';
   2. **Page** is equal to **Artists**;
3. Geef de field group volgende custom fields **(\* is required)**:
   1. **Title\***
      * Field Name: title
      * Field Type: Text
   2. **Picture\***
      * Field Name: picture
      * Field Type: image
      * Return Format: Image Array
      * Maximum File Size: 5MB
      * Allowed File Types: jpg, jpeg, png
   3. **Description\***
      * Field Name: description
      * Field Type: Text Area
      * New Lines: Automatically add paragraphs
{% endtab %}
{% endtabs %}

**Vergeet niet voor elke field group de correcte Location toe te voegen.** M.a.w. de correcte conditionele regels voor het koppelen van de field group aan de correcte pagina of post type.

Je kan uittesten of je conditionele regels correct zijn ingesteld door te navigeren naar het bewerkingsscherm van de pagina of artiest en te checken of de metadata van je field group degelijk zichtbaar zijn als inputvelden.

