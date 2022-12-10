# Optional Chaining

De optional chaining `?.` is een veilige manier om toegang te krijgen tot eigenschappen van geneste objecten, zelfs als er geen tussenliggende eigenschap bestaat.

### Het "niet-bestaande eigendom" probleem

Laten we als voorbeeld zeggen dat we een object `user` hebben die de informatie over onze gebruikers bevatten.

De meeste van onze gebruikers hebben een adres (`user.address`) met daarin een straat (`user.address.street`), maar de eigenschap adres is niet voor alle gebruikers ingevuld.

In dat geval, wanneer we proberen `user.address.street` te krijgen, en de gebruiker heeft toevallig geen adres, krijgen we een foutmelding:

```javascript
let user = {}; // a gebruiker zonder de "address" eigenschap

alert(user.address.street); // Error!
```

Dat is het verwachte resultaat. JavaScript werkt als volgt. Omdat `user.address` `undefined` is, mislukt een poging om `user.address.street` op te halen en krijg je een foutmelding terug.

In veel praktische gevallen krijgen we hier liever `undefined` in plaats van een foutmelding.

&#x20;Optional chaining lost dit probleem op voor ons.

### Optional Chaining&#x20;

De optional chaining `?.` stopt de evaluatie als de waarde vóór `?.` `undefined` of `null` is en retourneert `undefined`.

Iets "**bestaat**" als het niet `null` en `undefined` is.

Met andere woorden, `value?.prop`:

werkt als `value.prop`, als `value` bestaat, anders (wanneer de `value` `undefined` of `null` is) wordt `undefined` geretourneerd. Dit is de veilige manier om toegang te krijgen tot `user.address.street` met `?.`:

```javascript
let user = {}; // user has no address

alert( user?.address?.street ); // undefined (no error)
```

## Bronnen

{% embed url="https://javascript.info/optional-chaining" %}
