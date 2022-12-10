# Spread Operator

## De Spread operator in JavaScript

De JavaScript-spread-operator (`...`) stelt je in staat om snel alle, of een deel van een bestaande array of object, naar een andere array of object te kopiëren.

### Spread operator met arrays

De spread operator kan gebruikt worden om twee, of meerdere, arrays te combineren tot een nieuwe array.

```javascript
const array = [1, 2, 3];
const arrayTwo = [4, 5, 6];
const arraysCombined = [...array, ...arrayTwo];

console.log(arraysCombined) // [1, 2, 3, 4, 5, 6]
```

### Spread operator met objects

Je kan de spread operator ook op objecten toepassen.

```javascript
const myBook = {
  title: 'CMS Dev inleiding',
  author: 'Denis',
};

const updateMyBook = {
  pages: 199,
  year: 2022, 
  secondHand: false
};

const myUpdatedBook = {...myBook, ...updateMyBook};

console.log(myUpdatedBook);
// {
//   title: 'CMS Dev inleiding',
//   author: 'Denis',
//   pages: 199,
//   year: 2022,
//   secondHand: false;
// }
```

### Spread operator met destructering

De spread operator wordt vaak gebruikt in combinatie met destructurering.

```javascript
const numbers = [1, 2, 3, 4, 5, 6];

const [one, two, ...rest] = numbers;

console.log(one); // 1
console.log(two); // 2
console.log(rest); // [3, 4, 5, 6]
```
