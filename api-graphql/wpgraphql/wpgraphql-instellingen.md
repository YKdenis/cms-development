# WPGraphQL correct instellen

Wanneer de plugin geïnstalleerd en geactiveerd is, zal je een nieuwe item zien in je WP dashboard menu met de naam “**GraphQL**”. Onder deze menu-item kan je de instellingen van je GraphQL API aanpassen en de GraphiQL IDE raadplegen.

Als je navigeert naar je GraphQL instellingen zal je zien dat je helemaal vanboven je graphQL endpoint kan instellen. Met deze link wordt de API vrijgegeven en hebben andere applicaties de mogelijkheid om data op te vragen aan de hand van GraphQL queries.

<figure><img src="../../.gitbook/assets/image (219).png" alt=""><figcaption></figcaption></figure>

Pas de GraphQL instelling niet aan. We zullen de standaard instellingen gebruiken voor onze artist agency met als endpoint `/graphql`_._

Als je nu navigeert naar [http://yourdomain/graphql](http://yourdomain/graphql), in mijn geval is dat [_http://inghelbrecht-agency.local/graphql_](http://artist-agency-2021.local/graphql)_,_ dan zou je onderstaande error moeten zien.

![](https://firebasestorage.googleapis.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-McK0L74fqwFUdPmFPHF%2Fuploads%2FbGdrz1djdDOMhMA1Tx41%2Ffile.png?alt=media)

Indien dat het geval is dan is GraphQL correct ingesteld. **Als je een andere error krijgt is er iets mis met je installatie of met de code van je custom post type/taxonomy.** Let er op dat je voor beide de velden `graphql_plural_name` en `graphql_single_name` hebt voorzien!

{% hint style="info" %}
Je hebt de velden`graphql_plural_name` en `graphql_single_name` toegevoegd in je `functions.php` van je child-thema.
{% endhint %}
