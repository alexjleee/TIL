# Value of 'this'

> `this` refers to the object that is currently calling the function.

The value of `this` is determined by **how a function is called**.

## 1. In Global Scope

If a function which includes `this` is called from the global scope, by default `this` refers to the **global object** (in case of the browser, it is the `window` object).

```javascript
console.log(this); // window

function checkThis() {
	console.log(this);
}
checkThis(); // window
```

But if the function is in strict mode, `this` will yield
`undefined`.

```javascript
function checkThis() {
	'use strict';
	console.log(this);
}
checkThis(); // undefined
```

## 2. In Object Method

`this` refers to the immediate enclosing object that owns the method.

```javascript
const user = {
	name: 'Alex',
	checkThis() {
		console.log(this);
	},
	printName() {
		console.log(this.name);
	},
};
user.checkThis(); // {name: "Alex", checkThis: ƒ, printName: ƒ}
user.printName(); // Alex
```

## 3. In Constructor Function

When creating a new object with `new` operator, `new` creates an empty object and binds it as the `this` context. All the `this` in the constructor function now refer to the newly created object.

```javascript
function User(fName, lName) {
	this.fName = fName;
	this.lName = lName;
	this.checkThis = function () {
		console.log(this);
	};
	this.greet = function () {
		console.log(`Hi, I'm ${fName} ${lName}.`);
	};
}

const user1 = new User('Alex', 'Lee');
user1.checkThis(); // User {fName: "Alex", lName: "Lee", checkThis: ƒ, greet: ƒ}
user1.greet(); // Hi, I'm Alex Lee.
```

## 4. In Event Handler

`this` refers to the element to which the event handler is attached.

```javascript
const introBtn = document.querySelector('#introBtn');

class Person {
	constructor(introBtn, name) {
		this.introBtn = introBtn;
		this.name = name;

		this.introBtn.addEventListener('click', function () {
			this.greet(); // this -> introBtn HTML button element
		});
	}
	greet() {
		console.log('this:', this);
		console.log(`Hi, I'm ${this.name}`);
	}
}

const person1 = new Person(introBtn, 'Alex');
person1.greet(); // this -> person1 object

// 1. When the page is loaded, in the console:
// this: Person {introBtn: button#introBtn, name: "Alex"}
// Hi, I'm Alex

// 2. When you click the intro button, in the console:
// Uncaught ReferenceError: greet is not defined
```

## 5. In Arrow Function

Arrow functions don't have their own `this` so `this` inside an arrow function inherits the value of `this` from its lexical scope.

```javascript
const introBtn = document.querySelector('#introBtn');

class Person {
	constructor(introBtn, name) {
		this.introBtn = introBtn;
		this.name = name;

		this.introBtn.addEventListener('click', () => {
			this.greet(); // this -> person1 object
		});
	}
	greet() {
		console.log('this:', this);
		console.log(`Hi, I'm ${this.name}`);
	}
}

const person1 = new Person(introBtn, 'Alex');
person1.greet(); // this -> person1 object

// 1. When the page is loaded, in the console:
// this: Person {introBtn: button#introBtn, name: "Alex"}
// Hi, I'm Alex

// 2. When you click the intro button, in the console:
// this: Person {introBtn: button#introBtn, name: "Alex"}
// Hi, I'm Alex
```

## How To Explicitly Set The Value Of 'this'

- `bind` : allows you to explicitly set what `this` refers to

```javascript
const user1 = {
	name: 'Alex',
};

function printLoginInfo(date, time) {
	return `${this.name} was logged on ${date} at ${time}`;
}

const bound = printLoginInfo.bind(user1);

console.log(bound('5th February', '9:00PM'));
```

- `call` : similar to `bind` but unlike `bind`, `call` accepts additional parameters as well and immediately calls the function

```javascript
const user1 = {
	name: 'Alex',
};

function printLoginInfo(date, time) {
	return `${this.name} was logged on ${date} at ${time}`;
}

console.log(printLoginInfo.call(user1, '5th February', '9:00PM'));
```

- `apply` : similar to `call` but it accepts additional parameters as an array

```javascript
const user1 = {
	name: 'Alex',
};

function printLoginInfo(date, time) {
	return `${this.name} was logged on ${date} at ${time}`;
}

console.log(printLoginInfo.apply(user1, ['5th February', '9:00PM']));
```
