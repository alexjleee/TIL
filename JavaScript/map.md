# Map

> `Map` is a new object type introduced in ES6

> `Map` stores key-value pairs (any data type can be used as a key or value)

## Basic Syntax

```javascript
// Create an empty Map
const newMap = new Map();
// Map(0) {}

// You can also create a Map with a 2D key-value Array (key can be any data type)
const arrayToMap = new Map([
	['name', 'Alex'],
	[true, 1],
	[false, 0],
	[{ name: 'Alex' }, 2021],
]);
// Map(4) {"name" => "Alex", true => 1, false => 0, {name: "Alex"} => 2021}
```

## Property & Method

- `size` : return the number of key-value pairs in a `Map` object
- `set(key, value)` : set the value for the key in `Map` object
- `get(key)` : return the value for the specified key (return `undefined` if there is none)
- `has(key)` : return `true` if a `Map` object has the specified key, otherwise, return `false`
- `delete(key)` : remove the value of the specified key
- `forEach(function)` : execute the provided function for each key-value pair in a `Map` object
- `clear()` : removes all key-value pairs from a `Map` object

Iteration Methods

- `keys()` : return a new iterator object (**but not an array**) of the keys
- `values()` : return a new iterator object of the values
- `entries()` : return a new iterator object containing an array of `[key, value]`

```javascript
const farmAnimals = new Map([
	['chickens', 8],
	['ducks', 6],
	['cows', 2],
	['pigs', 4],
]);

farmAnimals.size; // 4

farmAnimals.set('sheep', 10); // Map(5) {...}
farmAnimals.size; // 5

farmAnimals.get('ducks'); // 6
farmAnimals.get('dogs'); // undefined
farmAnimals.has('chickens'); // true

farmAnimals.delete('pigs');
farmAnimals.size; // 4

farmAnimals.forEach((value, key) => {
	console.log(`There are ${value} ${key}`);
});
// There are 8 chickens
// There are 6 ducks
// There are 2 cows
// There are 10 sheep

let totalAnimals = 0;
for (let num of farmAnimals.values()) {
	totalAnimals += num;
}
console.log(`There are ${totalAnimals} animals in total`);
// There are 26 animals in total
```

## Differences Between `Map` & `Object`

`Map` looks similar to `Object` but there are some significant differences :

- The keys of `Object` must be either a `String` or `Symbol`, while `Map` can have any data type as the value for a key (even an `Object`)
- Unlike `Object`, `Map` preserves the insertion order of the keys and use it to iterate its elements
- `Map` is an iterable while `Object` isn't directly iterable

## From `Object` To `Map`

`Object.entries`

```javascript
const colorObj = {
	red: '#FF0000',
	pink: '#FFC0CB',
	orange: '#FFA500',
	magenta: '#FF00FF',
};

const colorMap = new Map(Object.entries(colorObj));

colorMap; // Map(4) {"red" => "#FF0000", "pink" => "#FFC0CB", "orange" => "#FFA500", "magenta" => "#FF00FF"}
```

## From `Map` To `Object`

`Object.fromEntries`

```javascript
const colorMap = new Map([
	['red', '#FF0000'],
	['pink', '#FFC0CB'],
	['orange', '#FFA500'],
	['magenta', '#FF00FF'],
]);

const colorObj = Object.fromEntries(colorMap.entries());

colorObj; // {red: "#FF0000", pink: "#FFC0CB", orange: "#FFA500", magenta: "#FF00FF"}
```
