# Scope

- Scope is an environment where a certain variable is declared (variable environment in case of functions)
- Scope determines the accessibility (visibility) of variables

## Scope Chain

- Scope chain is a stack of currently accessible scopes
- Only the inner scope has access to the outer scope, not the other way around
- You can declare a new variable inside a child scope that has the same name as one of the parent scope's variables. The newly created variable is a different variable from the other variable. But if you reassign variable inside the child scope, it actually changes the value of the variable in the parent scope.

  ```javascript
  // variables with the same names
  let foo = 'this will be reassigned';
  ('use strict');
  function outer() {
    const bar = 'bar';
    function inner() {
      foo = 'reassigned';
      const bar = 'another bar';
      console.log('inner: ', foo); // inner: reassinged
      console.log('inner: ', bar); // inner: another bar
    }
    inner();
    console.log('outer: ', foo); // outer: reassigned
    console.log('outer: ', bar); // outer: bar
  }
  outer();
  ```

## Lexical Scope

- JS has lexical scope, which means scoping is determined by where it was defined or created in the code
- Lexical scope is also called _static scope_ because the scope is determined at compile time

## Types of Scope

### Global Scope

- Top of the scope chain
- Outside any function or block
- Variables declared here are accessible from everywhere
- <-> Local scope (function scope, block scope)

### Function Scope

- Inside the function declaration, function expression, arrow function
- Variables inside a function are accessible only inside the function

### Block Scope

- Introduced in ES6
- Variables declared with `let` and `const`, not with `var` (`var` is function scope)
- Variables declared inside a block (between `{` and `}`) are accessible only inside the block
- In strict mode, functions are also block scoped, so function declared inside a block is only accessible inside the block
