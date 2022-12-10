---
description: >-
  In dit hoofdstuk zal je leren hoe je een formulier toevoegt aan je statische
  website en de inzendingen daarvan binnenhaalt in je Netlify dashboard.
---

# 🗒 Formulier afhandeling in Netlify

Netlify voorziet een ingebouwde formulierverwerking die toegankelijk is voor gebruikers met een **gratis tier.** Het proces is eenvoudig en zal stap per stap hieronder worden uitgelegd.

### 1) Toevoegen van een formulier aan de contact pagina

In dit hoofdstuk zullen we het gehele proces bespreken door als voorbeeld een formulier toe te voegen aan de contact page van de artiesten agentschap.

Laten we beginnen met het coderen van een simpel HTML-formulier in de contact.js file.

{% code title="contact.js" %}
```jsx
// section met className "header"

      <section className={form}>
        <form name="contact" method="POST" data-netlify="true">
            <label>Your Name:</label>
            <input type="text" name="name" required={true} />
            <label>Your Email:</label>
            <input type="email" name="email" required={true} />
            <label>Message:</label>
            <textarea name="message" required={true}></textarea>
            <button type="submit">Send</button>
        </form>
      </section>
    </Layout>
  )
}
// default export
```
{% endcode %}

Zoals je waarschijnlijk al hebt opgemerkt volgt het de standaard structuur van een formulier in HTML met twee kleine aanpassingen. Boven aan in je `form`-element staan er twee extra attributen gedefinieerd namelijk `data-netlify="true"` en `name="contact"`.

1. Met het `data-netlify="true"` attribuut laat je Netlify weten dat deze form moet afgehandeld worden en dat de inzendingen zichtbaar moeten zijn in het Netlify admin paneel;
2. Het attribuut `name="contact"` bepaalt welke naam het formulier krijgt in je Netlify admin paneel. Als je meer dan één formulier op een site hebt, moet elk formulier natuurlijk een unieke naam krijgen;

Wanneer Netlify het build process van je statische website uitvoert, zullen de attributen `data-netlify` en `name` automatisch worden verwijderd. Netlify zal vervolgens een verborgen input veld injecteren met als naam de waarde van je `name` attribuut (in ons geval "**contact**").

In de resulterende HTML (na het builden van je website door Netlify), zijn de attributen `data-netlify="true"` en `name="contact"` verdwenen en krijg je volgend verborgen input veld te zien in de code:

```jsx
<input type="hidden" name="form-name" value="contact">
```

#### Wat als je een website manueel upload naar Netlify?

Indien je niet aan continuous deployment doet en je website manueel upload naar Netlify zal je de verborgen input zelf moeten toevoegen in je code.

Je code ziet er dan als volgt uit:

{% code title="contact.js" %}
```jsx
 // section met className "header"
 
 <section className={form}>
        <form name="contact" method="POST" data-netlify="true">
            <label>Your Name:</label>
            <input type="text" name="name" required={true} />
            <label>Your Email:</label>
            <input type="email" name="email" required={true} />
            <label>Message:</label>
            <textarea name="message" required={true}></textarea>
            <input type="hidden" name="form-name" value="contact" />
            <button type="submit">Send</button>
        </form>
      </section>
    </Layout>
  )
  
  // default export
```
{% endcode %}

### 2) Styling van het formulier

Voeg de volgende stijl regels toe onderaan je `page.module.css` file:

{% code title="page.module.css" %}
```css
/* Form ********* */

.form {
  margin-top: 60px;
}

.form label {
  display:block;
  margin-top: 15px;
}

.form input, .form textarea {
  width: 100%;
  padding: 5px;
}

.form textarea {
 min-height: 300px;
}

.form button {
  display: block;
  background-color: #37ba83;
  color: white;
  font-size: 1rem;
  font-weight: bold;
  border: 1px solid #000;
  border-radius: 4px;
  padding: 10px 20px;
  margin-right: auto;
  margin-top: 10px;
  text-decoration: none;
  transition: all 0.2s ease;
  text-transform: uppercase;
}
```
{% endcode %}

Je formulier ziet er nu als volgt uit:

<figure><img src="../../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

### 3) Deploy je formulier naar Netlify

De volgende stap is het deployen van je formulier naar Netlify. Dit doe je door je code te pushen naar je Github repo (indien je werkt met continuous deployment) of door je website lokaal te builden met `gatsby build` en de public folder opnieuw manueel te uploaden naar Netlify.

Eenmaal als je website klaar is met builden, navigeer je naar de contact pagina en vul je het formulier in.

<figure><img src="../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>

Druk op de verzend knop en indien je alles correct hebt ingesteld krijg je volgend scherm te zien.

<figure><img src="../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

Voila! :tada: Je inzending is verwerkt en kan geraadpleegd worden in je Netlify admin paneel.&#x20;

In het volgende hoofdstuk vind je meer uitleg over het admin paneel en de instellingen er van.
