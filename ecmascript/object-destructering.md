---
description: >-
  in dit hoofdstuk leer je meer over het destructureren van JavaScript-objecten,
  waarbij eigenschappen van een object worden toegewezen aan afzonderlijke
  variabelen.
---

# Object Destructering

Inleiding tot destructering van JavaScript-objecten

&#x20;Stel dat je een object genaamd `book` hebt met twee eigenschappen: `title` en `author`.

Voorafgaand aan ES6, wanneer je eigenschappen van het `book` object aan variabelen wilt toewijzen, doe je dit meestal als volgt:

```javascript
let book = {
    title: 'Inleiding CMS Dev',
    author: 'Denis'
};

let title = book.title;
let author = book.author;
```

ES6 introduceerde de object destructering syntax die een alternatieve manier biedt om eigenschappen van een object aan variabelen toe te wijzen:

```javascript
let book = {
    title: 'Inleiding CMS Dev',
    author: 'Denis'
};

let { title, author } = book;

console.log(title, author) // Inleiding CMS Dev, Denis
```

### Destructuring van een eigenschap dat niet bestaat

Wanneer je een eigenschap die niet bestaat toewijst aan een variabele met behulp van object destructering, wordt de variabele ingesteld op `undefined`. Bijvoorbeeld:

```javascript
let book = {
    title: 'Inleiding CMS Dev',
    author: 'Denis'
};

let { title, author, genre } = book;

console.log(genre) // undefined
```

In dit voorbeeld bestaat de eigenschap `genre` niet in het book-object, daarom is de `genre`-variabele niet gedefinieerd (`undefined`).

### Nested object destructuring

Laten we er van uitgaan dat we een `student` object hebben met een eigenschap `name` dat ook een object is met daarin de eigenschappen `firstName` en `lastName`:

```javascript
let student = {
    name: {
        firstName: 'John',
        lastName: 'Doe'
    }
};

let {
    name: {
        firstName,
        lastName
    }
} = student;

console.log(firstName); // John
console.log(lastName); // Doe
```

De bovenstaande code destructureert de eigenschappen van het geneste `name`-object in afzonderlijke variabelen.

### Destructering functie argumenten

Stel dat je een functie hebt die het `book`-object weergeeft:

```javascript
let display = (book) => console.log(book.title + ' by ' + book.author);

let book = {
    title: 'CMS Dev inleiding',
    author: 'Denis'
};

display(book); // CMS Dev inleiding by Denis
```

Het is mogelijk om het objectargument dat aan de functie is doorgegeven als volgt te destructureren:

```javascript
let display = ({title, author}) => console.log(title + ' by ' + author);

let book = {
    title: 'CMS Dev inleiding',
    author: 'Denis'
};

display(book); // CMS Dev inleiding by Denis
```

Het ziet er minder uitgebreid uit, vooral wanneer je veel eigenschappen van het argumentobject gebruikt. **Deze techniek zal vaak worden gebruikt in de cursus!**
