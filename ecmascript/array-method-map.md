# Array Method: map()

Je zal vaak een array hebben waarvan je de elementen wilt manipuleren zodat je een nieuwe array krijgt met de gewijzigde elementen.

In plaats van de array handmatig te herhalen met een `for` loop, kan je eenvoudig de ingebouwde methode `Array.map()` gebruiken.

Met de methode `Array.map()` kan je over een array itereren en de elementen ervan wijzigen met behulp van een **callback-functie**. De **callback-functie** wordt dan uitgevoerd op elk van de elementen van de array.

Stel dat je het volgende array-element hebt:

```javascript
let arr = [3, 4, 5, 6];
```

Stel je nu voor dat je elk van de elementen van de array met 3 moet vermenigvuldigen. Je zou kunnen overwegen om een `for`-loop als volgt te gebruiken:

```javascript
let arr = [3, 4, 5, 6];

for (let i = 0; i < arr.length; i++){
  arr[i] = arr[i] * 3;
}

console.log(arr); // [9, 12, 15, 18]
```

In plaats van met een `for`-loop te werken, kan je beter gebruik maken van de methode `Array.map()` om hetzelfde resultaat te bereiken. Hieronder een voorbeeld:

```javascript
let arr = [3, 4, 5, 6];

let modifiedArr = arr.map(function(element){
    return element *3;
});

console.log(modifiedArr); // [9, 12, 15, 18]
```

De methode `Array.map()` wordt vaak gebruikt om enkele wijzigingen op de elementen uit te voeren, of het nu gaat om vermenigvuldigen met een specifiek getal, zoals in de bovenstaande code, of om andere bewerkingen.

### De map() methode toegepast op een array van objecten

Je kan bijvoorbeeld een reeks objecten hebben waarin de waarden `firstName` en `lastName` van van artiesten als volgt wordt opgeslagen:

```javascript
let artists = [
  {firstName : "Anna", lastName: "Woznak"},
  {firstName : "Kevin", lastName: "`Bismark"},
  {firstName : "Rayan", lastName: "Miller"}
];
```

Je kan de methode `map()` gebruiken om over de array te itereren en de waarden van `firstName` en `lastName` als volgt samen te voegen:

```javascript
let artists = [
  {firstName : "Anna", lastName: "Woznak"},
  {firstName : "Kevin", lastName: "`Bismark"},
  {firstName : "Rayan", lastName: "Miller"}
];

let artistsFullnames = artists.map(function(artist){
    return `${artist.firstName} ${artist.lastName}`;
})

console.log(artistsFullnames);
// ["Anna Woznak", "Kevin Bismark", "Rayan Miller"]
```

### De complete map() methode syntax <a href="#the-complete-map-method-syntax" id="the-complete-map-method-syntax"></a>

De syntax voor de methode `map()` is als volgt:

```javascript
arr.map(function(element, index, array){  }, this);
```

De `callback-functie()` wordt aangeroepen op elk array-element en de methode `map()` geeft altijd het huidige `element`, de `index` van het huidige element en het hele `array`-object door.

Het argument `this` wordt gebruikt in de callback-functie. Standaard is de waarde `undefined`. Je kan bijvoorbeeld de `this`-waarde als volgt wijzigen in het getal 80:

```javascript
let arr = [2, 3, 5, 7]

arr.map(function(element, index, array){
	console.log(this) // 80
}, 80);
```

Je kan ook de andere argumenten testen met `console.log()` als je geïnteresseerd bent:

```javascript
let arr = [2, 3, 5, 7]

arr.map(function(element, index, array){
    console.log(element);
    console.log(index);
    console.log(array);
    return element;
}, 80);
```

En dat is alles wat je moet weten over de methode `Array.map()`. Voor het artist agency project zal je alleen het element en index argument binnen de callback-functie gebruiken terwijl je de rest negeert.

### Callback-functie als arrow functie

Je kan ook gebruik maken van een arrow functie als callback-functie. Hieronder een voorbeeld:

```javascript
let artists = [
  {firstName : "Anna", lastName: "Woznak"},
  {firstName : "Kevin", lastName: "`Bismark"},
  {firstName : "Rayan", lastName: "Miller"}
];

let artistsFullnames = artists.map(artist => {
return `${artist.firstName} ${artist.lastName}`;
});

console.log(artistsFullnames);
// ["Anna Woznak", "Kevin Bismark", "Rayan Miller"]
```

### Destructering van de callback-functie argumenten

Op de callback-functie argumenten kan je ook destructering uitvoeren. Neem aan dat we een array van `artist` objecten hebben met als eigenschappen `firstName` en `lastName`:

```javascript
let artists = [
  {firstName : "Anna", lastName: "Woznak"},
  {firstName : "Kevin", lastName: "`Bismark"},
  {firstName : "Rayan", lastName: "Miller"}
];

let artistsFullnames = artists.map(({firstName, lastName}) => {
return `${firstName} ${lastName}`;
});

console.log(artistsFullnames);
// ["Anna Woznak", "Kevin Bismark", "Rayan Miller"]
```

{% hint style="info" %}
**Let op**: eenmaal als je aan destructering van arrow functie argumenten doet moet je haakjes toevoegen rondom de parameters. Normaliter moet dit niet als je maar met één argument werk, maar bij destructuring van argumenten is dit verplicht.
{% endhint %}
