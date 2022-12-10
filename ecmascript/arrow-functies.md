# Arrow functies

## Arrow functies

Arrow functies zijn geïntroduceerd in de ES6-versie van JavaScript. Hiermee kan je functies op een compactere manier schrijven in vergelijking met traditionele functies. Bijvoorbeeld,

Deze functie:

```javascript
// traditionele functie expressie
let x = function(x, y) {
   return x * y;
}
```

Kan worden geschreven als arrow functie:

```javascript
// arrow functie
let x = (x, y) => x * y;
```

### Arrow functie syntax

De syntax van een arrow functie is:

```javascript
let myFunction = (arg1, arg2, ...argN) => {
    // body
}
```

* **myFunction** is de naam van de functie;&#x20;
* **arg1, arg2, ...argN** zijn de functieargumenten;

Als de body een enkele instructie of expressie heeft, kan je de arrow functie schrijven als:

```javascript
let myFunction = (arg1, arg2, ...argN) => expression
```

#### Voorbeeld 1: Arrow functie zonder argument&#x20;

Als een functie geen enkel argument aanneemt, moet je lege haakjes gebruiken. Bijvoorbeeld,

```javascript
let greet = () => console.log('Hallo');
greet(); // Hallo
```

#### Voorbeeld 2: Arrow functie met één argument&#x20;

Als een functie slechts één argument heeft, kunt u de haakjes weglaten. Bijvoorbeeld,

```javascript
let greeting = 'Hallo';

let greet = x => console.log(x);
greet(greeting); // Hallo
```

#### Voorbeeld 4: Arrow functie met meerdere regels&#x20;

Als de body van een functie meerdere instructies heeft, moet je deze tussen accolades {} plaatsen en het **return** keyword gebruiken. Bijvoorbeeld,

```javascript
let sum = (a, b) => {
    let result = a + b;
    return result;
}

let result1 = sum(5,7);
console.log(result1); // 12
```
