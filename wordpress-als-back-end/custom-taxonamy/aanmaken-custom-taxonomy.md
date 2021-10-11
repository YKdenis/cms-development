---
description: >-
  Om een custom taxonomy aan te maken zullen we ons moeten verdiepen in de
  WordPress source code.
---

# Aanmaken van een Custom Taxonomy

## Een Custom Taxonomies manueel aanmaken

Voeg de volgende code toe aan het `functions.php` van je child-thema. Als je nog geen child-thema hebt aangemaakt doe dat eerst. Indien er ooit een update komt van je hoofdthema zal al de onderstaande code verloren gaan!

Let er op dat je deze code plakt binnen de opening en closing tags van je PHP code en niet binnen de body van een andere functie. Als je al een custom post type hebt aangemaakt kan je de taxonomy code op het zelfde niveau juist daaronder plaatsen. Als je meer informatie wenst omtrent de code en hoe WordPress dit interpreteert bekijk dan zeker eens de [documentatie.](https://developer.wordpress.org/reference/functions/register_taxonomy/)

{% code title="functions.php" %}
```php
<?php

add_action( 'wp_enqueue_scripts', 'tt_child_enqueue_parent_styles' );

function tt_child_enqueue_parent_styles() {

wp_enqueue_style( 'parent-style', get_template_directory_uri().'/style.css' );

}

add_action('init', function() {
  register_post_type('artist',
  [
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

add_action('init', function() {
    register_taxonomy( 'role', 'artist',
    [
        'public' => true,
        'labels' => [
        'name' => _x( 'Role', 'taxonomy general name' ),
        'singular_name' => _x( 'Role', 'taxonomy singular name' ),
        'search_items' => __( 'Search Roles' ),
        'popular_items' => __( 'Popular Roles' ),
        'all_items' => __( 'All Roles' ),
        'parent_item' => null,
        'parent_item_colon' => null,
        'edit_item' => __( 'Edit Role' ),
        'update_item' => __( 'Update Role' ),
        'add_new_item' => __( 'Add New Role' ),
        'new_item_name' => __( 'New Role Name' ),
        'separate_items_with_commas' => __( 'Separate roles with commas' ),
        'add_or_remove_items' => __( 'Add or remove roles' ),
        'choose_from_most_used' => __( 'Choose from the most used roles' ),
        'menu_name' => __( 'Roles' ),
    ],
        'show_in_graphql' => true,
        'show_admin_column' => true,
        'graphql_single_name' => 'role',
        'graphql_plural_name' => 'roles',
    ]);
});
?>
```
{% endcode %}

In dit voorbeeld maken we een taxonomy aan met de naam '`role`' als eerste argument. Het tweede argument bepaald op welke soort post type de taxonomy van toepassing is. In ons geval is dat de custom post type '`artist`'. Het derde argument is een array van object types waarmee de taxonomy geassocieerd wordt. Aan de hand van deze object types kan je de taxonomy aanpassen net zoals je dat bij de custom post type hebt gedaan.

### Object Types

* **public**: Of een taxonomy bedoeld is voor openbaar gebruik, hetzij via de admin-interface, hetzij door front-end gebruikers.
* **Labels**: Een reeks labels die worden gebruikt in de GUI van WordPress.
* **show_admin_column**: Of er een kolom voor de taxonomy moet worden weergegeven op de schermen met post type lijsten.
* De 3 onderste array waarden zullen worden besproken wanneer we ons verder zullen verdiepen in GraphQL.

Eenmaal als je de code hebt toegevoegd zou je bij je Artists een nieuwe kolom moeten zien met de naam **Role**. We kunnen vervolgens onder de **Artists** tab op het submenu '**Roles**' klikken en nieuwe rollen toevoegen.

![](<../../.gitbook/assets/image (49).png>)

Voeg een paar rollen toe zoals Actor, Model, Singer, ...

![](<../../.gitbook/assets/image (100).png>)

Voeg twee artiesten toe en geef ze beide een paar roles mee. Om meerdere roles toe te voegen aan een artiest moet je ze onderscheiden met een komma zoals hierboven weergegeven. Vergeet niet op **publish/update** te klikken om de roles op te slaan!

![](<../../.gitbook/assets/image (6).png>)

Je kan ze vervolgens filteren op basis van hun role. Dit kan je doen door op de naam van een role te klikken onder de kolom '**Role**'. Als je de filter wilt verwijderen klik je op de knop '**Filter**' in de werkbalk boven de tabel.

Voila! Je hebt een custom taxonomy toegevoegd aan je WP installatie zonder hulp van een plugin! Je mag beide artiesten verwijderen. Later zullen we er opnieuw toevoegen maar dan met wat meer informatie dan alleen een titel.
