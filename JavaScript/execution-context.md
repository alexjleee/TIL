# Execution Context

Execution Context (EC) is an environment where a piece of code is executed. It stores all the information (local variables, arguments, etc) that is necessary for the code to be executed.

## Global EC & Function EC
When JS code is loaded into a browser, JS engine creates a **global execution context**. And every time a function is called, a new **function execution context** is pushed to the *call stack*. After being executed, the function EC pops off from the call stack but the global EC pops off only when the browser window is closed.

## Inside Execution Context
1. Variable Environment
  - variable declarations
  - functions
  - `arguments` object (in case of function EC)
  - the values of the variables only become known during execution phase (not in the creation phase)
2. Scope Chain (Reference to the outer environment)
  - Scope is an environment where a certain variable is declared and accessible/visible 
  - Scope chain is a stack of currently accessible scopes
  - If a scope needs to use a certain variable, it starts to look for the variable in the current scope and if it cannot find it it will look up in the scope chain and find the variable in the parent scopes, from the most immediate scope to the global scope.
3. `this`object binding
4. Global object `window`(in case of global EC in a web browser)

