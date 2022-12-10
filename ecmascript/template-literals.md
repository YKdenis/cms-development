# Template Literals

## Template Literals

Template Literals gebruiken back-ticks (` `` `) in plaats van de aanhalingstekens (`""`) om een string te definiëren:

```javascript
let hello = `Hello World!`;
```

### Aanhalingstekens in strings&#x20;

Met template literals kan je zowel enkele als dubbele aanhalingstekens in een string gebruiken:

```javascript
let text = `Hij zei: "Ik heb zin in Ben & Jerry's"`;
```

### Variabele substitutie

template literals staan variabelen in strings toe:

```javascript
let firstName = "John";
let lastName = "Doe";

let text = `Welcome ${firstName}, ${lastName}!`;
```

**Variabele substitutie met template literals zullen we veel gebruiken!**
