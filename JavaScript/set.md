# Set

> `Set` is a new object type introduced in ES6

> `Set` stores UNIQUE values of any type (string, number, boolean, array, ...)

## Basic Syntax

```javascript
// Create an empty Set
const newSet = new Set();
// Set(0) {}

// You can also create a Set with an iterable object(string or array)
const stringSet = new Set('string');
// Set(6) {"s", "t", "r", "i", "n", "g"}
const arraySet = new Set([
	12,
	true,
	'string',
	[1, 2, 3],
	{ type: 'object' },
	undefined,
	null,
]);
// Set(7) {12, true, "string", Array(3), Object, undefined, null}
```

## Property & Method

- `size` : return the number of elements in a `Set` object
- `add(value)` : add a new element in a `Set` object
- `has(value)` : return `true` if a `Set` object has the specified value, otherwise, return `false`
- `delete(value)` : remove the specified value from a `Set` object
- `forEach(function)` : execute the provided function for each value in a `Set` object
- `clear()` : removes all elements from a `Set` object

```javascript
const missedCalls = new Set();

missedCalls.add('Lewis');
missedCalls.add('Ines');
missedCalls.add('Lewis').add('Sun').add('Ellie');

missedCalls.size; // 4

missedCalls.has('Sun'); // true
missedCalls.has('Mike'); // false

missedCalls.delete('Ines');

missedCalls.size; // 3

missedCalls.forEach((name) => {
	console.log(`${name} called you.`);
});
// "Lewis called you."
// "Sun called you."
// "Ellie called you."

missedCalls.clear();

missedCalls.size; // 0
```

## Differences Between `Set` & `Array`

`Set` looks similar to `Array` but there are some significant differences :

- `Array` is an indexed collection while `Set` is a keyed collection
- Unlike `Array`, you cannot re-order or randomly access `Set`
- When iterated, `Set` follows insertion order and you cannot change the order

## When To Use `Set`

`Set` is useful when you want to remove duplicates in data.

- Example : remove duplicated values from an array

```javascript
// Example data
const menu = [
	'paella',
	'fabada',
	'salmorejo',
	'morcilla',
	'gazpacho',
	'paella',
	'fabada',
	'gazpacho',
	'gazpacho',
];
```

```javascript
// (1) Removing duplicates using Set
const uniqueMenu = [...new Set(menu)];
// ['paella', 'fabada', 'salmorejo', 'morcilla', 'gazpacho']
```

```javascript
// (2) Removing duplicates without using Set
const removeDuplicates = (arr) => {
	let uniqueArr = [];
	arr.map((el) => {
		if (!uniqueArr.includes(el)) {
			uniqueArr.push(el);
		}
	});
	return uniqueArr;
};

const uniqueMenu = removeDuplicates(menu);
// ['paella', 'fabada', 'salmorejo', 'morcilla', 'gazpacho']
```
