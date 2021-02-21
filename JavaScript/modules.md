# Modules

> ES module became an official built-in feature in ES6

## What Is A Module

A module is a piece of code that can be independently created and maintained.

- Module : a collection of related components
- Component : a unit (a variable, a function, or a class) that can be exported from a module by `export`

## Why Do You Need Modules

- Reusability : each module is reusable
- Encapsulation : each module has its own top-level scope
- Maintainability : easy to adapt and easy to scale

## Features

1. Modules are always in strict mode (`use strict`). So, assigning to a non-existing variable will throw an error.

2. A module is executed only the first time (even if it is imported into multiple places). Export is created once and shared between importers (so all the importers get exactly the same export).

3. In a module, top-level `this` is `undefined`.

4. Module execution is deferred (only run after a document is loaded) by default so you don't need to use `defer` attribute.

## How To Use Modules

In modern JS, modules are separate files and they can load each other using `export` and `import`. Modules can `export` functions, classes or variables and other modules can `import` to use them.

Because ES modules are _static_, `import` and `export` must be at the top level (cannot be inside a block).

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

### Export

You can place `export` before a declaration or declare and `export` separately.

And if you want to export a component with a different name for the importers you can use `export {name as otherName}` syntax.

#### Named Export

A module can export multiple components and each of them is distinguished by its name.

```javascript
export const year = 2021;
export function greet(name) {
	return `Hello, ${name}`;
} // no ; after export class/function
```

```javascript
const year = 2021;
function greet(name) {
	return `Hello, ${name}`;
}
export { year, greet };
```

#### Default Export

For the modules that declare a single entity, `export default` syntax can be used. There can be **only one `default` per module**.

```javascript
export default class User {
	constructor(name) {
		this.name = name;
	}
	greet() {
		return `Hello, ${this.name}`;
	}
}
```

```javascript
class User {
	constructor(name) {
		this.name = name;
	}
	welcome() {
		return `Welcome, ${this.name}`;
	}
}
export { User as default };
```

### Import

You can place `export` before a declaration or declare and `export` separately.

And similar to `export` if you want to import a component with a different name, you can use `import {name as otherName}` syntax.

#### Importing Named Exports

```javascript
import { year, greet } from './user.js';
```

```javascript
// In case there are so many components to import
import * as user from './user.js';

user.year; // 2021
user.greet('Alex'); // Hello, Alex
```

#### Importing Default Export

Unlike names exports, when importing default export, you can choose the name while importing. In the example, it doesn't have to be called 'User'. But to keep the consistency, it is recommended to follow the convention - name it corresponding to the file name.

```javascript
import User from './user.js';
```

#### Importing Default & Named Exports

```javascript
import { default as User, year, welcome } from './user.js';
```

```javascript
import User, { year, welcome } from './user.js';
```

```javascript
import User, * as user from './user.js';
```
