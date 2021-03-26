# Modules

In the Node.js, each file is treated as a separate module.

```javascript
// message.js
const msg = 'Hello World';
const getMessage = () => {
	return msg;
};
module.exports.getMessage = getMessage;
```

```javascript
// index.js
const message = require('./message.js');
console.log(message.getMessage()); // Hello World
console.log(msg); // ReferenceError!
```

Functions and objects are added to the root of a module by adding them to the `module.exports` object.

- `getMessage()` function in _message.js_ has been added to `module.exports` object and it can be used in other files that `require` _message.js_

Top-level variables in the module are scoped to the module rather than the global object. Because each module is wrapped in a function by Node.js (**the module wrapper**).

- `msg` variable cannot be accessed from _index.js_ because it is a private variable of _message.js_.
- `getMessage()` function has a closure scope reference to the `msg` variable. So, even if it is called inside of _index.js_ file, still has access to `msg` variable.

## The Module Wrapper

Node.js wraps a module with a function wrapper before a it is executed.

```javascript
(function (exports, require, module, __filename, __dirname) {
	// Module code here
});
```

- `exports`

  A reference to the `module.exports` object

- `require(id)`

  It takes the id of a module (path/name) and returns the exported content of the module.

  - id prefixed with `/` : absolute path
  - id prefixed with `./` : relative to the file calling require()
  - id without a leading `/`, `./`, or `../` : core module or module loaded from a `node_modules` folder

  A module is cached in `require.cache` object when it is required for the first time. So, if a module is required several times, it won't be reloaded (unless you delete a key value from this object).

- `module`

  A reference to the current module

  `module` may appear to be global but it is actually local to each module.

- `__filename`

  The filename of the current module

  - For example, `/Users/mjr/example.js`

- `__dirname`

  The directory name of the current module

  - For example, `/Users/mjr`

## `exports` vs. `module.exports`

Every time we use `require()`, it returns `module.exports` object. `exports` is referencing the same object, `module.exports`.

For adding properties or functions, both works the same. Because either way, the properties or functions are added to the `module.exports` object as key-value pairs.

```javascript
// greet.js
module.exports.greet = function () {
	console.log('Hello');
};
// OR
exports.greet = function () {
	console.log('Hello');
};
```

```javascript
// index.js
require('./greet.js').greet();
```

But if you reassign `exports`, then it is no longer equal to `modele.exports`.

```javascript
// greet.js
module.exports = function greet() {
	console.log('Hello');
}; // OK
exports = function greet() {
	console.log('Hello');
}; // ERROR!
```

```javascript
// index.js
require('./greet.js')();
```

In the above case, `exports = function greet() {}` doesn't add a key-value pair to the `module.exports` object. Instead, it makes `exports` lose the reference to the `module.exports` object and make it reference the `greet` function.

## CJS vs. ESM
Node had its own module system, **Common JS (CJS)**. Since v14, Node.js introduced support for **ES modules (ESM)** (with `import` and `export`) but it requires using `.mjs` extension or configuration option in `package.json`, with a `type` property set to `module` - this will make your files be interpreted ad ESM, not as CJS.

### Syntaxes
  1. CJS
  ```javascript
  // utils.js
  exports.add = (a, b) => {
    return a + b;
  }
  exports.sub = (a, b) => {
    return a - b;
  }
  ```
  ```javascript
  //main.js
  const utils = require('./utils');
  utils.add(4, 2); // 6
  utils.sub(4, 2); // 2
  ```

  2. ESM
  ```javascript
  // utils.js
  export const add = (a, b) => {
    return a + b;
  }
  export const sub = (a, b) => {
    return a - b;
  }
  ```
  ```javascript
  // main.js
  import {add, sub} from './utils.js';
  add(4, 2); // 6
  sub(4, 2); // 2
  ```