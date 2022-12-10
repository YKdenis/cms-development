---
description: >-
  Post types is een term die wordt gebruikt om te verwijzen naar verschillende
  soorten inhoud/content op een WordPress-site.
---

# Wat zijn Custom Post Types?

## **WordPress wordt geleverd met vijf standaard post types:**

* Post (bericht)
* Page (pagina)
* Attachment
* Revision
* Nav-menu

Die laatste drie zijn iets dat we nu niet hoeven te bespreken. Ze volbrengen hun doel stilletjes in de achtergrond van WordPress, en ze vereisen niet veel aandacht van onze kant. Berichten en pagina's is waar wij ons op zullen toespitsen. Vanuit technisch oogpunt werken ze vrijwel hetzelfde, en het belangrijkste verschil tussen hen is dat posts toegankelijk zijn vanuit je wp-admin via het menu **Posts**, terwijl pagina's toegankelijk zijn via **Pages**.

![](<../../.gitbook/assets/image (18) (1).png>)

Deze twee waren de klassieke post types die beschikbaar waren in WordPress tot versie 3.0 erbij kwam. Daarin kregen gebruikers de mogelijkheid om hun eigen post types te creëren, boven de standaard posts en pagina's.

Zo'n nieuwe post type - door jou gedefinieerd - zal verschijnen in de wp-admin direct onder de menu's Posts en Pages in de zijbalk. En het belangrijkste is dat je met dat nieuwe post type kunt werken, net zoals je zou doen met berichten en pagina's.

{% hint style="info" %}
WordPress is geëvolueerd van een eenvoudig blogplatform naar een robuust CMS waardoor de term post type, wat voor blogbericht type stond, nog steeds wordt gebruikt om een content type binnen WordPress te benoemen**. In de praktische zin zou het dus content type moeten zijn i.p.v. post type** maar door de geschiedenis van WordPress is dat nooit aangepast geweest. Het is een verwarrende term maar weet als we over een post type spreken, bedoelen we eigenlijk content type.
{% endhint %}

## Waarvoor / wanneer kan je een Custom Post Type gebruiken?

Custom post types kunnen je in veel situaties helpen, op basis van het type inhoud dat je op je WordPress-site wilt publiceren.

Meestal is een nieuwe custom post type een goed idee als je gewoon iets (een soort inhoud) wilt publiceren dat apart moet worden gehouden van berichten en pagina's.

{% hint style="info" %}
M.a.w. je wilt dat het niet als bericht of als pagina wordt gepresenteerd.
{% endhint %}

### **Laat me je een snel voorbeeld geven:**

Als je een site voor boekrecensies beheert, kan je waarschijnlijk een custom post type gebruiken, genaamd `boeken`.

Als je een apart gedeelte voor `boeken` op je recensie website hebt, wordt de inhoud beter verteerbaar voor je publiek en worden die recensies onderscheiden van de rest van je inhoud. Bovendien kan je hiermee ook specifieke parameters voor elk boek instellen - zoals `auteur` of `genre` - en deze naast de recensie weergeven.

## Hoe worden post types opgeslagen?

Alle post types worden opgeslagen in de databasetabel van posts en worden onderscheiden door een kolom met de naam `post_type`. Je kan via MySQL workbench, adminer of PHPmyAdmin de posts tabel bekijken en je zal zien dat er bij `post_type` een van de 5 hierboven vernoemde types zal staan.

![](<../../.gitbook/assets/image (14) (1).png>)

{% hint style="info" %}
Met Local kan je gemakkelijk je WordPress database bekijken. Navigeer naar Database en klik op '**Open Adminer**'
{% endhint %}

<figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>
