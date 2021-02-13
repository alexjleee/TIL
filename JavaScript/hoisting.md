# Hoisting

Before code execution, in the parsing phase, JS interpreter moves all the variable & function declarations at the top of the scope. This is called hoisting.

- Hoisting only moves the declarations and the definitions are left in place.
  - Declaration : Hoisted
  - Definition : Not Hoisted
  - Declaration + Definition : Declaration Hoisted, Definition Not Hoisted

- Hoisting Variable : Initialised with `undefined`

```javascript
console.log(msg); // undefined
var msg = 'hello';
```

- Hoisting Function Declaration : Unlike a variable, a function declaration also hoists the actual function definition.

```javascript
console.log(greet()); // hello world
function greet() {
	return 'hello world';
}
```

- Hoisting Function Expression : Same as hoisting a variable - initialised with `undefined`

```javascript
console.log(greet());
// TypeError: greet is not a function
// (because it is 'undefined')
var greet = function () {
	return 'hello world';
};
```

## Temporal Dead Zone (TDZ)

TDZ is the zone where a certain variable is not accessible. TDZ was introduced in ES6 with `let` and `const` variables, to reduce errors.
  - Hoisting Behaviour of Different Variables
    - `var` : initialised with `undefined`
    - `let` : uninitialised
    - `const` : uninitialised

- For every `let` and `const` variable, there is TDZ that starts at the beginning of the scope until the line where it is actually defined.
- The `let` and `const` variables are only sage to use after TDZ. Inside TDZ, if you try to use the variables, it will throw reference error.
- **Declare variables before using them!**

```javascript
if (true) {
	// TDZ of 'msg' Starts ------
	console.log(msg); // Reference Error: Cannot access 'msg' before initialization
	let msg = 'print this message';
	// TDZ of 'msg' Ends ------
	console.log(msg); // print this message
}
```

```javascript
// TDZ of 'greet' Starts ------
greet(); // ReferenceError: Cannot access 'greet' before initialization
const greet = function () {
	// TDZ of 'msg' Starts ------
	console.log(msg);
	const msg = 'hello world';
	// TDZ of 'msg' Ends ------
};
// TDZ of 'greet' Ends ------
greet(); // ReferenceError: Cannot access 'msg' before initialization
```
