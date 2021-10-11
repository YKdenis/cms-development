---
description: >-
  Om een custom post type te kunnen aanmaken zullen we ons moeten verdiepen in
  de WordPress source code.
---

# Aanmaken van een Custom Post Type

## Hoe maak je een Custom Post Type in WordPress aan?

Vooraleer je begint aan het creëren van een Custom Post Type is het belangrijk dat je een child-thema hebt geïnstalleerd. Dit om te voorkomen dat de code, die je zo zult schrijven, wordt verwijderd bij het updaten van je WordPress thema/sjabloon.

Navigeer naar je `functions.php` file in je child-thema map. In deze file zullen we de custom post type toevoegen. Normaal gezien staat er in je `functions.php` file al een functie die de parent `style.css` file inlaadt.

![functions.php](<../../.gitbook/assets/image (7).png>)

Juist onder de functie `tt_child_enqueue_parent_styles` schrijf je deze code:

{% code title="functions.php" %}
```php
<?php

add_action( 'wp_enqueue_scripts', 'tt_child_enqueue_parent_styles' );

function tt_child_enqueue_parent_styles() {

wp_enqueue_style( 'parent-style', get_template_directory_uri().'/style.css' );

}

add_action('init', function() {
  register_post_type('artist', [
      'public' => true,
      'labels' => [
      'name' => 'Artists',
      'singular_name' => 'Artist',
      'add_new_item' => 'Add New Artist',
      'edit_item' => 'Edit Artist',
      'new_item' => 'New Artist',
      'view_item' => 'View Artist',
      'view_items' => 'View Artists',
      'search_items' => 'Search Artists'
  ],
      'show_in_graphql' => true,
      'graphql_single_name' => 'Artist',
      'graphql_plural_name' => 'Artists',
  ]);
});

?>
```
{% endcode %}

We registreren een post type voor onze artiesten genaamd '`artist`'. We zetten `public` op `true` en geven er een labels aan mee. De 3 onderste array waarden zullen worden besproken wanneer we ons verder zullen verdiepen in GraphQL. Als je meer informatie wenst omtrent de code en hoe WordPress dit interpreteert bekijk dan zeker eens de [documentatie](https://developer.wordpress.org/reference/functions/register_post_type/).

{% hint style="info" %}
Labels worden gebruikt in het dashboard van WordPress om de gebruiker **een betere gebruikservaring** te geven wanneer ze een artiest toevoegen, bewerken, verwijderen, ...
{% endhint %}

Eenmaal als je de code hebben opgeslagen, krijgen we een nieuwe tab in ons dashboard te zien waarmee we gemakkelijk artiesten kunnen toevoegen, bewerken en verwijderen.

![](<../../.gitbook/assets/image (113).png>)

Navigeer naar '**Add New**' onder '**Artists**' in je WP dashboard. Bij het aanmaken van een artiest krijg je de standaard velden van een post te zien, een titel en een HTML teksteditor. Dit is niet echt handig sinds we een artiest bv. ook een naam en geboortedatum willen geven. We zullen dit later aan de hand van de plugin **Advanced Custom Fields** kunnen toevoegen. We zullen velden zoals naam en geboortedatum toevoegen en de standaardvelden zoals de teksteditor verwijderen.

![](<../../.gitbook/assets/image (131).png>)
