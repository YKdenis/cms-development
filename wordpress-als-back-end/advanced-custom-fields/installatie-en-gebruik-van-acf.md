---
description: Custom fields toevoegen met behulp van ACF (Advanced Custom Fields)
---

# Installatie en gebruik van ACF

Het eerste dat je moet doen is de plugin voor ACF installeren en activeren. Navigeer naar Plugins, Klik op '**Add New**' en zoek naar **Advanced Custom Fields**. Installeer en en activeer de plugin.

![](<../../.gitbook/assets/image (5) (1).png>)

Na de activatie van ACF zal er een nieuwe menu item in je WP werkbalk verschijnen, namelijk Custom Fields.

![](<../../.gitbook/assets/image (91).png>)

## Field Groups in ACF

Een Field Group is als een container van een set custom fields. Hiermee kan je meerdere groeperingen van custom fields toevoegen en deze vervolgens koppelen aan één of meerdere posts of pagina's.

Klik op '**Custom Fields**' in je werkbalk. Je krijgt onderstaand scherm te zien.

<figure><img src="../../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

### Aanmaken van een Field Group

Laten we samen overlopen hoe je een field group met custom fields aanmaakt en deze koppelt aan de standaard **Sample pagina**. Klik op de knop '**Add Field Group**' in het midden van je scherm.

Op de volgende pagina kan je in het bovenstaande veld (**Add New Field Group**) de naam van je field group invullen. Vul hier **Sample Fields** in.

<figure><img src="../../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure>

Vervolgens zie je een tabel met rechtsonder een knop '**Add Field**'. In deze tabel kan je custom fields toevoegen maar vooraleer we ons hier verder in zullen verdiepen is het belangrijk om te weten hoe je deze field group koppelt aan de sample page.

### Location - Conditionele regels

In de Tabel er onder, met als titel **Settings**, onder de tab **Location Rules** kan je de field group koppelen aan de hand van één of meerdere conditionele regels. Je kan hier opgeven en bepalen op wat voor soort bericht, pagina, gebruiker of form de field group van toepassing is.

We willen dat deze field group van toepassing is op het type '**Page**' en dat deze pagina de naam '**Sample Page**' moet hebben.

<figure><img src="../../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>

Indien je wilt dat deze field group ook van toepassing is op bijvoorbeeld alle posts dan kan je dat verwezenlijken door een extra conditionele regel toe te voegen.

De werking is exact hetzelfde als de **&&** (AND) en **||** (OR) operatoren in programmeren. In het geval van ons voorbeeld willen we een OR. We drukken op de knop '**add rule group**' en voegen een conditionele regel toe waarvan de **Post Type** gelijk moet zijn aan **Post**.

<figure><img src="../../.gitbook/assets/image (214).png" alt=""><figcaption></figcaption></figure>

De field group zal nu worden toegewezen aan de Sample Page als zowel elke post die we hebben aangemaakt, en in de toekomst zullen maken.

{% hint style="warning" %}
Voor dit voorbeeld mag je de conditionele regel '**Post Type is equal to Post**' verwijderen.
{% endhint %}

### Toevoegen van Custom Fields

Met ACF kan je allerlei soorten velden maken, waaronder tekst, afbeelding uploaden, nummer, vervolgkeuzelijst, selectievakjes en meer.

Scroll terug naar boven en klik op de knop '**Add Field**' rechtsonder in de eerste tabel. Je krijgt een hele waslijst van input velden te zien. De belangrijkste zijn de eerste 4 velden:

1. **Field Label:** De naam die de gebruiker ziet op de bewerkingspagina;
2. **Field Name:** De naam die wordt gebruikt in de code m.a.w. de naam die later in onze API wordt weergegeven;
3. **Field Type:** Wat voor type veld het is;
4. **Instructions:** de instructies die de gebruiker ziet bij het invullen van deze custom field op de bewerkingspagina;

Afhankelijk van de Field Type krijg je andere input velden. Bijvoorbeeld, met een Field Type '**Image**' kan je ook de upload grote en dimensies van een foto aanpassen.

{% hint style="info" %}
ACF beschikt over heel een uitgebreide en duidelijke documentatie. Indien je meer wilt weten over een specifieke Field Type dan raad ik je aan om de [documentatie](https://www.advancedcustomfields.com/resources/) eens te bekijken.
{% endhint %}

**Laten we als voorbeeld 2 custom fields toevoegen aan onze field group:**

* Summary
  * **Field Label:** Summary
  * **Field Name:** summary
  * **Field Type:** Text
  * **Instructions:** Geef een korte beschrijving van de pagina.
  * **Required:** True

<figure><img src="../../.gitbook/assets/image (184).png" alt=""><figcaption><p>General tab</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption><p>Validation tab</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (187).png" alt=""><figcaption><p>Presentation tab</p></figcaption></figure>

* Image
  * **Field Label:** Banner Picture
  * **Field Name:** banner\_picture
  * **Field Type:** Image
  * **Instructions:** Upload een banner foto.
  * **Required:** False
  * **Maximum File Size:** 1MB
  * **Allowed File Types:** jpg, jpeg, png

<figure><img src="../../.gitbook/assets/image (218).png" alt=""><figcaption><p>General tab</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (192).png" alt=""><figcaption><p>Validation tab</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (171).png" alt=""><figcaption><p>Presentation tab</p></figcaption></figure>

{% hint style="info" %}
Door een maximum file size op te geven zorg je ervoor dat gebruikers geen grote foto's uploaden. Hoe groter de file size van de foto hoe meer tijd de browser nodig heeft om deze in te laden. Het is nooit een goed idee om een foto groter dan 1 MB te gebruiken!

Met Allowed file types geef je op welke file types er toegelaten zijn.
{% endhint %}

### Settings

Voor elke field group zijn er een paar eenvoudige opties om het bewerkingsscherm waar deze field group verschijnt aan te passen. Als er meerdere field groups op een pagina verschijnen, worden de opties van de eerste field group gebruikt. Daarom kan je een **order no.** instellen onder de Presentation tab. Field groups worden geladen en weergegeven in volgorde van hun '**order no.**', waarbij 0 de eerste is.

Met de laatste optie op de Presentation tab in de rechter zijbalk, '**Hide on screen**', kan je standaard metadata die out of the box wordt meegegeven door WP zoals comments, author, etc. uitschakelen.

De optie onder de **Group Settings** tab '**Active**' moet je aantikken om de field group te activeren. Hiermee kan je de field group aan- en uitschakelen zonder de field group volledig te moeten verwijderen of je conditionele regels aan te passen.

<figure><img src="../../.gitbook/assets/image (147).png" alt=""><figcaption><p>Settings - Presentation tab</p></figcaption></figure>

### Publishen van de field group

Eenmaal als je beide custom fields hebt toegevoegd mag je rechtsboven op '**Save Changes**' klikken.

<figure><img src="../../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>

Als je field group is gepubliceerd en je hebt Active op true staan in je field group settings onder de **Group Settings** tab dan mag je navigeren naar je Sample Page onder pages in je WP werkbalk. Als je op het bewerkingsscherm van je Sample Page naar beneden scrollt zal je zien dat deze 2 nieuwe custom fields zijn toegevoegd.

![](<../../.gitbook/assets/image (76) (1).png>)

op deze manier kan je gemakkelijk custom fields toevoegen aan eender welke soort post of pagina in WP. Het bespaart je een hele hoop tijd dan als je dit met de native functionaliteit van WP zou moeten oplossen.

Tijdens het voorbeeld project en de langlopende opdracht zal je field groups moeten aanmaken met verschillende custom field types op zowel pages als custom post types. Als er iets niet duidelijk is bekijk dan zeker eerst eens de [documentatie](https://www.advancedcustomfields.com/resources/) van ACF. **Indien je geen antwoord vindt op je vraag stel deze dan op het studentenforum op Digitap**.
