# Modules

> ES module became an official built-in feature in ES6

## What Is A Module

A module is a piece of code that can be independently created and maintained.

## Why Do You Need Modules

- Reusability : each module is reusable
- Encapsulation : each module has its own top-level scope
- Maintainability : easy to adapt and easy to scale

## How To Use Modules

In modern JS, modules are separate files and they can load each other using `export` and `import`. Modules can `export` functions, classes or variables and other modules can `import` to use them.

```javascript
// main.js
import { getUserName } from './modules/getUserName.js';

const user1 = {
	firstName: 'Alex',
	lastName: 'Lee',
	joined: '14/02/2021',
	comments: 15,
	posts: 10,
};

console.log(getUserName(user1)); // "Alex Lee"
```

```javascript
// modules/getUserName.js
export function getUserName(user) {
	return `${user.firstName} ${user.lastName}`;
}
```

You must use `type="module"` attribute in the `script` tag to tell the browser that it should be treated as a module.

```html
<!-- inside the HTML file -->
<script type="module" src="main.js"></script>
```
