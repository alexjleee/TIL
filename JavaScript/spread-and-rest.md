# Spread & Rest

> The **spread** operator and the **rest** parameters look the same (`...`) but they are certainly different.

## Spread Operator

The spread operator takes an iterable (or an object) and spreads/expands it.

1. In a function call

```javascript
// Spread an iterable into a list of arguments
const numsArray = [5, 8, 9, 4, 7];
Math.max(numsArray); // NaN
Math.max(...numsArray); // 9
```

2. In an array literal

```javascript
// Spread the elements from one array into another array
const girls = ['Alex', 'Ellie', 'Sun'];
const boys = ['Lewis', 'Juan', 'Eric'];
const girlsAndBoys = [...girls, ...boys];
girlsAndBoys; // ["Alex", "Ellie", "Sun", "Lewis", "Juan", "Eric"]

// You can spread a string into an array
let str = 'abcd';
const charArray = [...str];
charArray; // ["a", "b", "c", "d"]
```

3. In an object literal

```javascript
// Spread the properties from one object into another object
const npc = {
	isPlayable: false,
	speed: 0,
};

const enemy = {
	...npc,
	speed: 10,
	attackDamage: 10,
};
// enemy has all the properties of npc
// 'speed' property is overwritten
// the latter overwrites the former if the key name is same

// Spread can be used to simply copy an object
const npcCopy = {
	...npc,
};
npc === npcCopy; // false
```

\*You CANNOT spread an object in an array!

However, you can spread an iterable (an array or a string) in an object.

```javascript
// You can't do this
const cat = {
	family: 'Felidae',
	isPet: true
}
[...cat]; // Uncaught TypeError: cat is not iterable

// But you can do this
const word = 'cat';
{...word}; // { 0: "c", 1: "a", 2: "t" }
```

## Rest Parameters

The rest parameter syntax allows a function to accept an indefinite number of arguments as an _array_.

```javascript
function sum(...nums) {
  // now, no matter how many arguments you pass in to the function, they will be turn into an array called 'nums'
  // you can use 'reduce' since 'nums' is an array
	return nums.reduce((acc, c) => acc + c);
}
sum(1, 3, 5, 7); // 16
```

If there are other parameters too, the rest parameters have to be the last parameter

```javascript
function cities(country, first, second, ...rest) {
    console.log(`The largest city in ${country} is ${first}.`);
    console.log(`The second largest city is ${	second}.`);
    console.log(`And there are ${rest.join(', ')} and more.`);
};

cities('Scotland', 'Glasgow', 'Edinburgh', 'Aberdeen', 'Dundee', 'Inverness', 'Perth', 'Stirling');
// The largest city in Scotland is Glasgow
// The second largest city is Edinburgh
// And there are Aberdeen, Dundee, Inverness, Perth, Stirling and more.
```