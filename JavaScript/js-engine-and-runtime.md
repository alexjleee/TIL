# JS Engine & Runtime
JS is a single-threaded language. JS runtime environment (in case of the web, a browser) handles asynchronous callbacks.

## JS Engine

Javascript engine is a program that interprets and executes the JS code. It is the centre of the JS runtime.

- Every browser has its own JS engine. For example, Chrome has V8 JS engine. V8 is also used in Node.js.

### Compilation

JS engine takes JS source code and parses (into AST), compiles (into machine code), executes and optimises during execution.

- Compilation : source code -> compile -> portable file (machine code) -> execute -> run
- Interpretation : source code -> execute line by line -> run

JS used to be an interpreted language. But interpretation is too slow. So, the modern JS uses the mix between compilation and interpretation, *Just-in-time Compilation*
- Just-in-time Compilation : source code -> compile -> machine code -> execution -> run

### Call Stack & Heap

JS engine consists of call stack & memory heap

- Call Stack : The call stack keeps track of the order of executions. When JS engine comes across a function call, it adds it to the call stack.
  - Synchronous. One function at a time.
  - Last in first out (LIFO) 
  - When a function returns a value or is sent to the Web API container, it is popped off the stack and moves to the next function in the stack. 

- Memory Heap : A place to store and write information. When JS engine comes across variables and function declarations, it stores them in the heap.

## JS Runtime Environment

JS engine runs inside an environment called Javascript runtime environment along with many other components (such as Web APIs and callback queue).

- Web APIs : A Web API call (such as event listener, HTTP/AJAX request or timer function) from the call stack is sent to the Web API container and wait until it is triggered. When it is triggered, a callback function is sent to the *callback queue*.

- Callback Queue : A place where all the callback functions from Web APIs are stored. When the call stack is empty it will send the callback function at the start of the queue to the call stack.
  - First in first out (FIFO)

- Event Loop : It constantly checks the call stack and the callback queue. If it sees the stack is empty, tell the Queue to send the next callback function. 

Browser environment provides Web APIs(such as DOM and AJAX) but Node.js doesn't. Instead, you can install any packages into the Node environment as needed.

