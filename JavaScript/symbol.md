# Symbol

> Symbol is a **primitive data type** that cannot be recreated (unique)

Syntax : `let id = Symbol();`
- `let id = new Symbol(); // TypeError` : You can't use `new` keyword since symbol is an incomplete constructor.
- `let id = Symbol('id')` : You can give symbol a description(symbol name), for debugging purpose.
- `let user = {[id]: 123}` : In object literal, you need to put square brackets(`[]`) around it

Symbols are unique.
- `Symbol() === Symbol(); // false` 

Even if the symbols have the same description, they are different values.
- `Symbol('id') === Symbol('id'); //fasle`

Symbols are not enumerated. They are not included in `for...in`, `Object.keys()` nor `Object.getOwnPropertyNames()`. You can access the symbols using `Object.getOwnPropertySymbols()` method.

## Where & Why Do You Use Symbol

A symbol is used as a unique identifier for object properties.

1. To avoid name collision
```javascript
// adding property inside `user` object from third-party code
let user = {
  id: 123,
  name: 'Alex'
}

// (1) if you use a string as the key,
user.id = 1;
// This will overwrite the original value
user; // {id: 1, name: "Alex"}

// (2) instead, if you use a symbol as the key,
let id = Symbol('id');
user[id] = 1;
// It won't overwrite the original value
user; // {id: 123, name: "Alex", Symbol(id): 1};

```
2. To defined metadata on an object
```javascript
class BookCollection {
  constructor() {
    this.length = 0;
  }
  add(title, author) {
    this[title] = author;
    this.length++;
  }
}

let bestSellers = new BookCollection();
bestSellers.add('Hungry', 'Grace Dent');
bestSellers.add('A Deadly Influence', 'Mike Omer');
bestSellers.add('Unnatural Causes', 'Richard Shepherd');
bestSellers.add('The Crossing', 'Matt Brolly');

for (book in bestSellers) {
  console.log(book, bestSellers[book]);
}

// length 4 // << we don't want this to be printed 
// Hungry Grace Dent
// A Deadly Influence Mike Omer
// Unnatural Causes Richard Shepherd
// The Crossing Matt Brolly
```
```javascript
const length = Symbol('length');
class BookCollection {
  constructor() {
    this[length] = 0;
  }
  add(title, author) {
    this[title] = author;
    this[length]++;
  }
}

// ...

// Hungry Grace Dent
// A Deadly Influence Mike Omer
// Unnatural Causes Richard Shepherd
// The Crossing Matt Brolly
```
- But remember, symbols are not private

## Global Symbols
If you need same-named symbols to be same  entities, you can create symbols in _global symbol space_ using `Symbol.for(key)`.

```javascript
const id1 = Symbol.for('id'); // create Symbol(id) in global symbol space
const id2 = Symbol.for('id'); // read Symbol(id) from the global symbol space
id1 === id2; // true
```

- Get symbol by name
```javascript
let idSym = Symbol.for('id');
```
- Get name by symbol
```javascript
console.log(Symbol.keyFor(idSym)); // id
```