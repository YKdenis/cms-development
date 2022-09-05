---
description: >-
  Advanced Custom Fields is een plug-in waarmee je extra inhoudsvelden aan je
  posts of pagina's kan toevoegen. Deze velden worden vaak custom fields
  genoemd.
---

# WP plugin 🔌: Advanced Custom Fields

## Wat zijn Custom WordPress-fields?

Custom WordPress-fields zijn metagegevens die worden gebruikt om aanvullende informatie toe te voegen met betrekking tot de post of pagina die je aan het bewerken bent.

Wanneer je een nieuwe post, pagina of een ander inhoudstype schrijft, slaat WordPress deze standaard op in twee verschillende gebieden. Het eerste deel is de hoofdtekst van je inhoud die je toevoegt met de teksteditor. Het tweede deel is de informatie over die specifieke inhoud. Bijvoorbeeld titel, auteur, datum, tijd en meer. Dit informatiegedeelte van het bericht wordt **metadata/metagegevens** genoemd.

{% hint style="info" %}
**Metadata** omschrijft de karakteristieke gegevens van een bepaalde post of pagina binnen WordPress.
{% endhint %}

![Teksteditor van een WordPress pagina.](<../../.gitbook/assets/image (24).png>)

![De metadata van een WordPress pagina.](<../../.gitbook/assets/image (25).png>)

WordPress voegt automatisch metadata toe aan elke post en pagina die je maakt. **Visibility**,, **Permalink**, … vallen allemaal onder de noemer metadata. Deze worden out of the box meegeleverd met elke nieuwe installatie van WordPress. Buiten de standaard metadata van WordPress, kan je ook je eigen metadata maken en opslaan met behulp van custom fields.

## Native custom fields in WordPress

Standaard is de optie voor custom fields verborgen op het bewerkingsscherm voor posts / pagina's. Om het te bekijken, moet je op het menu met drie stippen in de rechterbovenhoek van het scherm klikken en '**Preferences**' selecteren in het menu.

![](<../../.gitbook/assets/image (28).png>)

Dit zal een pop-up openen waarin je de optie ‘**Custom fields**’ onder panels moet aanvinken. Klik daarna op de knop ‘**Enable & Reload**’ om de editor opnieuw te laden.

![](<../../.gitbook/assets/image (31).png>)

![](<../../.gitbook/assets/image (30).png>)

De editor wordt opnieuw geladen en je kan het paneel met custom fields onder de inhoudseditor zien.

![](<../../.gitbook/assets/image (34).png>)

Custom fields kunnen worden gebruikt om informatie toe te voegen met betrekking tot de post, de pagina of elk ander soort inhoudstype.

In plaats van dit manueel toe te voegen gaan wij hiervoor een plugin gebruiken, namelijk **Advanced Custom Fields**. Je mag terug navigeren naar Preferences en de custom fields uitzetten! 

{% hint style="info" %}
Vergeet dit zeker niet te doen, **eenmaal als je ACF installeert en gebruikt zouden de native custom fields van WP problemen kunnen veroorzaken**.
{% endhint %}

## Waarom Advanced Custom Fields?

Als je de standaard optie gebruikt, dus geen plugin zoals ACF, om metagegevens toe te voegen dan zal je voor elke post en pagina manueel de custom fields moeten toevoegen.

Als je veel custom fields hebt of als meerdere gebruikers op je website schrijven, is dit geen ideale oplossing.

Met de Advanced Custom Fields plugin kan je a.d.h.v. een gebruikersinterface custom fields toevoegen aan eender welke post, pagina, user of taxonomy a.d.h.v. conditional rules. De gebruiker moet niet meer manueel bij elke post of pagina custom fields toevoegen. I.p.d.v. wordt dit in de achtergrond automatisch afgehandeld door ACF.
