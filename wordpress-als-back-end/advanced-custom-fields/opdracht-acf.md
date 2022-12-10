---
description: >-
  In het deel over custom posts hebben we een entiteit aangemaakt voor Artists.
  Laten we hiervoor een Field Group maken en elke artist standaard bepaalde
  metagegevens meegeven.
---

# Opdracht ACF - Artist Fields

We hebben eerder een custom post type aangemaakt voor het creëren van artiesten. Momenteel heeft elke artiest alleen standaard metagegevens van een post uit WordPress. Deze metagegevens zijn afgestemd voor het aanmaken van blog posts niet voor het aanmaken van artiesten. Wij willen graag dat elke artiest een set custom fields krijgt die we later via onze API kunnen doorsluizen naar onze zelfgemaakte front-end.

Nu is het aan jullie! Verken de [ACF documentatie](https://www.advancedcustomfields.com/resources/) en maak de volgende oefening.&#x20;

{% hint style="info" %}
**Let op**:  Alle velden hebben een engelse benaming!
{% endhint %}

### **Volg het stappenplan hieronder:**

1. Maak een nieuwe field group aan en geef het de naam **Artist Fields;**
2. Koppel de field group aan de **custom post type** Artist;
   1. Je kan conditionele regels toevoegen in de sectie '**Location**';
3. Geef de field group volgende custom fields **(\* is required)**:
   1. **First Name\***
      1. Field Name: first\_name
      2. Field Type: Text
   2. **Last Name\***
      1. Field Name: last\_name
      2. Field Type: Text
   3. **Artist Name**
      1. Field Name: artist\_name
      2. Field Type: Text
   4. **Email\***
      1. Field Name: email
      2. Field Type: Email
   5. **Phone Number\***
      1. Field Name: phone\_number
      2. Field Type: Text
   6. **Description\***
      1. Field Name: description
      2. Field Type: Text Area
      3. New Lines: Automatically add paragraphs
   7. **Height**
      1. Field Name: height
      2. Field Type: Number
   8. **Origin**
      1. Field Name: origin
      2. Field Type: Text
   9. **Shoe Size**
      1. Field Name: shoe\_size
      2. Field Type: Range
      3. Minimum Value: 30
      4. Maximum Value: 55
      5. Step Size: 0.5
   10. **Shirt Size**
       1. Field Name: shirt\_size
       2. Field Type: Select
       3. Choices: S, M, L, XL, XXL
   11. **Picture 1**&#x20;
       1. Field Name: picture\_1
       2. Field Type: Image
       3. Return Format: Image Array
       4. Maximum File Size: 5MB
       5. Allowed File Types: jpg, jpeg, png
   12. **Picture 2**
       1. Field Name: picture\_2
       2. Field Type: Image
       3. Return Format: Image Array
       4. Maximum File Size: 5MB
       5. Allowed File Types: jpg, jpeg, png
   13. **Picture 3**
       1. Field Name: picture\_3
       2. Field Type: Image
       3. Return Format: Image Array
       4. Maximum File Size: 5MB
       5. Allowed File Types: jpg, jpeg, png
   14. **Profile Picture\***
       1. Field Name: profile\_picture
       2. Field Type: image
       3. Return Format: Image Array
       4. Maximum File Size: 5MB
       5. Allowed File Types: jpg, jpeg, png

Je kan de documentatie voor elke Field Type [hier](https://www.advancedcustomfields.com/resources/) raadplegen!

Tweak elke custom field naar maximale gebruiksvriendelijkheid en flexibiliteit. Soms zal je flexibiliteit moeten opgeven voor gebruiksvriendelijkheid en vice versa. Help gebruikers met het vermijden van fouten maar zorg ervoor dat ze genoeg vrijheid behouden om flexibel te werk te gaan.

{% hint style="info" %}
_**Bv. een maximum file size op een image zetten.** _ Je helpt de gebruiker met het behouden van een snelle website. Maar indien je de maximum file size te klein zet dan belemmer je hun in het snel aanmaken van content!
{% endhint %}
