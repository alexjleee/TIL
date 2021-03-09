# Currying

## What Is Currying

In _functional programming_, **currying** is the technique of converting a function that takes multiple arguments into a sequence of functions that each take a single argument.

-> converting `f(a, b, c)` into `f(a)(b)(c)`

Currying is used to create more reusable functions.

### Currying In JS

- JS is a multi-paradigm programming language that includes _functional_, object-oriented, procedural and prototypal programming.

- You can do functional programming in JS because JS supports **functions as first-class objects** and [**closure**](/JavaScript/closure.md).

  - In JS, functions are first-class objects, which means that they can be passed to functions or returned from functions.


```javascript
const curry = (func) => {
	return function curriedFunc(...args) {
		if (args.length >= func.length) {
			return func(...args);
		} else {
			return (...args2) => curriedFunc(...args, ...args2);
		}
	};
};

function sum(a, b, c) {
	return a + b + c;
}

const result = sum(1, 2, 3);
console.log(result); // 6

// currying
const curriedSum = curry(sum);
const result2 = curriedSum(1)(2)(3);
console.log(result2); // 6
```

## Partial Application vs. Currying

Partial application refers to the process of fixing a number of arguments to a function, producing another function with smaller number of arguments.

### Difference

- Partial application takes as many arguments at a time as needed.
- Curried function returns a function that takes one argument at a time.

```javascript
function sum(a, b, c) {
	return a + b + c;
}

const sum1 = sum(1, 2, 3);
console.log(sum1); // 6

// partial application
function addToN(n) {
	return function (x, y) {
		return n + x + y;
	};
}

const addTo1 = addToN(1);
const sum2 = addTo1(2, 3);
console.log(sum2); // 6

// currying
function curry(func) {
	return function (a) {
		return function (b) {
			return function (c) {
				return func(a, b, c);
			};
		};
	};
}
const curriedSum = curry(sum);
const sum3 = curriedSum(1)(2)(3);
console.log(sum3); // 6
```
