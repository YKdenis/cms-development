---
description: >-
  Elk goed WordPress-thema kan als hoofdthema worden gebruikt. Er zijn echter
  veel verschillende soorten thema's en sommige zijn misschien niet de
  gemakkelijkste om mee te werken.
---

# Aanmaken van een Child-thema

In het belang van deze zelfstudie gebruiken we **Twenty Twenty-One**, een van de standaard WordPress-thema's.

Eerst moet je `/app/public/wp-content/themes/` openen in je WordPress directory en een nieuwe map maken voor je child-thema. De directory heeft een naam nodig. Het is een goede gewoonte om een ​​child-thema dezelfde naam te geven als de ouder, maar met -child aan het einde. In ons geval is dat `twentytwentyone-child`.

{% hint style="info" %}
Je kan gemakkelijk navigeren naar je WordPress directory via het pijltje aangeduid in onderstaande foto! 
{% endhint %}

![](../../.gitbook/assets/image%20%28138%29.png)

Open een teksteditor zoals Vscode, maak een nieuwe file aan en plak er deze code in:

{% code title="style.css" %}
```css
/*
Theme Name: Twenty Twenty-One Child
Theme URL: http://yourdomain.com
Description: Twenty Twenty-One Child
Theme Author: Your Name
Author URL: http://yourdomain.com
Template: twentytwentyone
Version: 1.0.0
Text Domain: twentytwentyone-child
*/
```
{% endcode %}

Sla dit bestand op als style.css in de map `twentytwentyone-child` die je zojuist hebt aangemaakt.

De meeste dingen in dit bestand spreken voor zich en zijn niet echt van belang. **Alleen de twee volgende regels zijn vereist**:

* **Theme Name**: moet uniek zijn.
* **Template**: Dit vertelt WordPress dat ons thema een child-thema is en dat de naam van onze hoofdthema-directory `twentytwentyone` is. De naam van de bovenliggende map is hoofdlettergevoelig. Als we WordPress voorzien van een template genaamd `TwentyTwentyOne`, dan zal het niet werken.

Maak een ander bestand met je teksteditor naar keuze en noem het `functions.php`. Plak de volgende code in de `functies.php` van je child-thema. Dit stukje code laad de css file `style.css` in van `twentytwentyone`, het hoofdthema. Wens je meer informatie over wat deze functie juist doet bekijk dan eens de WordPress documentatie via deze [link](https://developer.wordpress.org/themes/advanced-topics/child-themes/).

{% code title="functions.php" %}
```php
<?php

add_action( 'wp_enqueue_scripts', 'tt_child_enqueue_parent_styles' );

function tt_child_enqueue_parent_styles() {

wp_enqueue_style( 'parent-style', get_template_directory_uri().'/style.css' );

}

?>
```
{% endcode %}

Dit zijn de minimumvereiste voor het maken van een child-thema. Je kunt nu naar _**Appearance -&gt; Themes**_ gaan waar je Twenty Twenty-One Child Theme ziet. Je moet op de knop '**activate**' klikken om het child-thema op je site te gebruiken.

![](../../.gitbook/assets/image%20%284%29.png)

![](../../.gitbook/assets/image%20%28126%29.png)

### style.css

Je hoofdthema heeft ook een `style.css`. Deze wordt overgeërfd door het child-thema en met de `style.css` van je child-thema kan je de styling van je hoofdthema overschrijven. 

{% hint style="info" %}
**Let op** 👀: In ons geval gaan we voor onze child-thema geen custom CSS schrijven. We gebruiken niet de front-end van WordPress m.a.w. wijzigingen aan de front-end hebben geen effect!
{% endhint %}

### functions.php

In tegenstelling tot `style.css`, overschrijft de `functions.php` van een child-thema de `functions.php` van het hoofdthema niet. In plaats daarvan wordt de `functions.php` van het child-thema file toegevoegd aan die van het hoofdthema. \(Het wordt net voor het bestand van de ouder ingeladen.\)

Op die manier bieden de `functions.php` van een child-thema een slimme, probleemloze methode om de functionaliteit van een hoofdthema aan te passen. Stel dat je een PHP-functie aan je thema wilt toevoegen. De snelste manier is om het bestand `functions.php` in je hoofdthema-map te openen en de functie daar te plaatsen. Maar dat is niet zo slim: de volgende keer dat je thema wordt bijgewerkt, verdwijnt je functie. Door de functie in de `functions.php` file van je child-thema te zetten zal je functie niet worden beïnvloed door toekomstige updates van het hoofdthema. **M.a.w. door een child-thema te gebruiken vermijd je code te verliezen bij elke thema update.**

