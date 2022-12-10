---
description: >-
  In dit hoofdstuk overlopen we belangrijke ECMAScript standaarden zoals Arrow
  functies, de spread operator en meer.
---

# ⏪ ECMAScript

## Wat is Ecmascript

ECMAScript **(ES)** is een programmeertaal voor algemene doeleinden die is geïmplementeerd in Javascript en enkele andere talen. Het is de scripttaal die de basis vormt van Javascript en Node.js. ECMA is een acroniem voor **European Computer Manufacturer's Association**, die standaarden ontwikkelt voor informatietechnologie en consumentenelektronica. Talen zoals ECMAScript, Dart-lang en C# werden gestandaardiseerd door ECMA.

Elk jaar verschijnt er (meestal) een nieuwe editie van ECMAScript. In julie 2022 is de nieuwste versie uitgekomen namelijk [ECMAScript2022](https://dev.to/jasmin/whats-new-in-es2022-1de6) **(ES2022)**.

De populairste versie van ECMAScript was **ES6** dat in 2015 is uitgekomen. ES6 introduceerde veel nieuwe dingen in de taal van JavaScript. Een van de belangrijkste dingen die het introduceerde, was [Block Scope](https://www.geeksforgeeks.org/javascript-es2015-block-scoping/) en het `let`-sleutelwoord. **Dit is belangrijk omdat er vóór ES2015 (ES6) slechts twee soorten scope waren: Global Scope en Function Scope**. De reden dat ze besloten om het `let`-sleutelwoord te introduceren, was dat wanneer je `var` gebruikte, het alleen globaal kon worden gebruikt. Met ES6 kan je met het sleutelwoord `let` een variabele declareren dat **alleen binnen een Block Scope** kan gebruikt worden.&#x20;

Hieronder zie je een voorbeeld van het gebruik van Block Scope om een variabele opnieuw te declareren.

```javascript
var x = 10;

// Hier is x = 10

{ 

  let x = 2;

  // Hier is x = 2

}

// Hier is x = 10
```

ECMAScript definieert nieuwe manieren om JavaScript code te schrijven. In dit hoofdstuk zullen we verschillende ECMAScript standaarden bespreken die we doorheen de cursus zullen gebruiken. Sommige hebben jullie al eens gezien, anderen misschien dan weer niet. Er wordt veronderstelt dat je de basis standaarden als het declareren van `let` of `const` al kent.

### ECMAScript standaarden

1. Arrow Functies;
2. Object Destructering;
3. Spread Operator;
4. Template Literals;
5. Logical Operators:
   * AND (&&);
   * OR (||);
   * NOT (!);
6. Optional Chaining;
7. Array Method:
   1. map();
