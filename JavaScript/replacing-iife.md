# Replacing IIFE

> Immediately Invoked Function Expression (IIFE) is a JS function that is executed as soon as it is defined.

> Syntax : `(function () { statements })();`

## Replace IIFE with Block

Before ES6, IIFE was used to avoid global scope pollution, by keeping `var` variables inside the IIFE scope that cannot be accessed from the outside.

```javascript
(function () {
	var msg = 'this cannot be accessed from outside';
})();
```

In ES6, you can create a local scope using a block and `let`/`const` declaration.

```javascript
{
	let msg = 'this is inside a block';
}
```

## Replace IIFE with module

Before ES6, libraries were needed to use modules. Without libraries, IIFE was used to make _revealing module pattern_.

- Revealing Module Pattern : It is a JS design pattern that uses IIFE to wrap the module function to create local scope for variables and methods.

```javascript
var printDay = (function () {
	var dayList = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
	function today() {
		var d = new Date();
		var n = d.getDay();
		console.log(dayList[n]);
	}
	function tomorrow() {
		var d = new Date();
		var n = d.getDay() + 1;
		if ((n = 7)) {
			console.log(dayList[0]);
		} else {
			console.log(dayList[n]);
		}
	}
	function yesterday() {
		var d = new Date();
		var n = d.getDay() - 1;
		if ((n = -1)) {
			console.log(dayList[6]);
		} else {
			console.log(dayList[n]);
		}
	}
	return {
		today: today,
		tomorrow: tomorrow,
		yesterday: yesterday,
	};
})();
```

ES6 has built-in modules. With ES6 modules, you can combine all scripts in one main script by using `export` and `import` keywords.

```javascript
// modules/printDay.js
const dayList = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
const d = new Date();
const n = d.getDay();

export function printToday() {
	console.log(dayList[n]);
}
export function printTomorrow() {
	if ((n = 6)) {
		console.log(dayList[0]);
	} else {
		console.log(dayList[n + 1]);
	}
}
export function printYesterday() {
	if ((n = 0)) {
		console.log(dayList[6]);
	} else {
		console.log(dayList[n - 1]);
	}
}
```

```javascript
// main.js
import { printToday, printTomorrow, printYesterday } from './modules/printDay.js';
```
