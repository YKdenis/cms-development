# Logical Operators

Er zijn vier logische operatoren in JavaScript: || (**OR**), && (**AND**), ! (**NOT**) en ?? (**Nullish Coalescing**). Hier behandelen we de eerste drie. Indien je meer wil weten over de ?? operator kan je [dit artikel](https://www.javascripttutorial.net/es-next/javascript-nullish-coalescing-operator/) bekijken.

Hoewel ze "**logisch**" worden genoemd, kunnen ze worden toegepast op waarden van elk type, niet alleen op boolean. Hun resultaat kan ook van elk type zijn.

Logical operators worden gebruikt om de logica tussen variabelen of waarden te bepalen.

Neem aan dat x = 6 en y = 3 voor de onderstaande tabel met logische operatoren:

| Operator | Beschrijving | Voorbeeld                     |
| -------- | ------------ | ----------------------------- |
| &&       | AND          | (x < 10 && y > 1) is true     |
| \|\|     | OR           | (x == 5 \|\| y == 5) is false |
| !        | NOT          | !(x == y) is true             |

### || (OR)

De operator "**OR**" wordt weergegeven met twee verticale lijnsymbolen:

```javascript
result = a || b;
```

In klassiek programmeren is de logische OR alleen bedoeld om booleaanse waarden te manipuleren. Als één van de argumenten waar is, retourneert het `true`, anders retourneert het `false`.

In JavaScript is de operator een beetje lastiger en krachtiger. Maar laten we eerst eens kijken wat er gebeurt met booleaanse waarden.

Er zijn vier mogelijke logische combinaties:

```javascript
console.log( true || true );   // true
console.log( false || true );  // true
console.log( true || false );  // true
console.log( false || false ); // false
```

Zoals we kunnen zien, is het resultaat altijd true`,` behalve in het geval dat beide operanden `false` zijn.

Als een operand geen boolean is, wordt deze voor de evaluatie geconverteerd naar een boolean.

Het cijfer 1 wordt bijvoorbeeld als `true` behandeld, het cijfer 0 als `false`:

```javascript
if (1 || 0) { // werkt net zoals if( true || false )
  alert( 'truthy!' );
}
```

Meestal wordt de **OR** `||` operator gebruikt in een `if`-statement om te testen of een van de gegeven voorwaarden waar is.

Bijvoorbeeld:

```javascript
let hour = 12;
let isWeekend = true;

if (hour < 10 || hour > 18 || isWeekend) {
  alert( 'The office is closed.' ); // het is weekend
}
```

#### OR "||" vindt de eerste truthy waarde&#x20;

De hierboven beschreven logica is enigszins klassiek. Laten we nu de "extra" functies van JavaScript toevoegen.

Het uitgebreide algoritme werkt als volgt.

Gegeven meerdere OR-waarden:

```javascript
result = value1 || value2 || value3;
```

De **OR** `||` operator doet het volgende:

* Evalueert operanden van links naar rechts;
* Converteert deze voor elke operand naar booleaans. Als het resultaat `true` is, stopt en retourneert de oorspronkelijke waarde van die operand.
* Als alle operanden zijn geëvalueerd (d.w.z. ze waren allemaal `false`), retourneert de laatste operand. Een waarde wordt geretourneerd in zijn oorspronkelijke vorm, zonder conversie.

Met andere woorden, een keten van **OR** `||` retourneert de eerste truthy waarde of de laatste als er geen turthy waarde wordt gevonden.

Bijvoorbeeld:

```javascript
alert( 1 || 0 ); // 1 (1 is truthy)

alert( null || 1 ); // 1 (1 is de eerste truthy waarde)
alert( null || 0 || 1 ); // 1 (1 is de eerste truthy waarde)

alert( undefined || null || 0 ); // 0 (alles is falsy, geeft de laaste waarde terug)
```

#### "kortsluiting" evaluatie

Een ander kenmerk van **OR** `||` operator is de zogenaamde “kortsluiting” evaluatie.

Het betekent dat `||` zijn argumenten doorloopt totdat de eerste truthy waarde is bereikt, en dan wordt de waarde onmiddellijk geretourneerd, zonder het andere argument zelfs maar aan te raken.

Het belang van deze functie wordt duidelijk als een operand niet alleen een waarde is, maar een expressie met een neveneffect, zoals een variabele toewijzing of een functie-call.

In het onderstaande voorbeeld wordt alleen het tweede bericht afgedrukt:

```javascript
true || alert("not printed");
false || alert("printed");
```

### && (AND)

De **AND**-operator wordt weergegeven met twee ampersands &&:

```javascript
result = a && b;
```

In klassieke programmering geeft **AND** `true` als beide operanden `true` zijn en anders `false`:

```javascript
alert( true && true );   // true
alert( false && true );  // false
alert( true && false );  // false
alert( false && false ); // false
```

Een voorbeeld met if-statement:

```javascript
let hour = 12;
let minute = 30;

if (hour == 12 && minute == 30) {
  alert( 'The time is 12:30' );
}
```

#### AND "&&" vindt de eerste falsy waarde&#x20;

Gegeven meerdere **AND**-waarden:

```javascript
result = value1 && value2 && value3;
```

De operator AND && doet het volgende:

* Evalueert operanden van links naar rechts.&#x20;
* Converteert deze voor elke operand naar een boolean. Als het resultaat `false` is, stopt en retourneert de oorspronkelijke waarde van die operand.&#x20;
* Als alle operanden zijn geëvalueerd (d.w.z. ze waren allemaal `true`), retourneert de laatste operand. Met andere woorden, **AND** retourneert de eerste falsy waarde of de laatste waarde als er geen werd gevonden.

De bovenstaande regels zijn vergelijkbaar met **OR**. Het verschil is dat **AND** de eerste falsy waarde retourneert, terwijl **OR** de eerste truthy retourneert.

Voorbeelden:

```javascript
// Als de eerste operand truthy is,
// retourneert AND de tweede operand:
alert( 1 && 0 ); // 0
alert( 1 && 5 ); // 5

// Als de eerste operand falsy is,
// retourneert AND de eerste operand. De tweede operand wordt genegeerd.
alert( null && 5 ); // null
alert( 0 && "no matter what" ); // 0
```

We kunnen ook meerdere waarden achter elkaar doorgeven. Zie hoe de eerste falsy waarde wordt geretourneerd:

```javascript
alert( 1 && 2 && null && 3 ); // null
```

Wanneer alle waarden truthy zijn, wordt de laatste waarde geretourneerd:

```javascript
alert( 1 && 2 && 3 ); // 3
```

### ! (NOT)&#x20;

De booleaanse NOT-operator wordt weergegeven met een uitroepteken **!**.

De syntax is vrij eenvoudig:

```javascript
result = !value;
```

De operator accepteert een enkel argument en doet het volgende:

* Converteert de operand naar het booleaanse type: `true`/`false`.&#x20;
* Retourneert de inverse waarde. Bijvoorbeeld:

```javascript
alert( !true ); // false
alert( !0 ); // true
```

## Bronnen

{% embed url="https://javascript.info/logical-operators" %}
