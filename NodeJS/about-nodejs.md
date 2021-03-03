# About Node.js

> JavaScript out of the browser!

## What Is Node.js

Node.js is a JavaScript runtime environment built on Chrome's V8 JavaScript engine (which compiles JS into machine code very fast!)

Node.js is open-source and cross-platform.

Node.js is suitable for building scalable network applications because it uses an _event-driven, non-blocking (asynchronous)_ _I/O_ model which enables the server to handle multiple requests at the same time using only one thread (efficient and fast).

- Event-Driven, Non-Blocking (Asynchronous) : Able to handle requests without waiting for the response to the previous requests. Node.js uses _event loop_ and _callbacks_ to avoid blocking.
- I/O : Input/Output.

## Why Node.js

- It is fast
- You can use JS for both frontend and backend
- Rich ecosystem : **npm** (Node.js Package Manager) allows access to a wide range of open-source packages

## What Is Node.js For

- To create, open, read, write, delete, and close files on the server
- To collect data from the users
- To add, delete, modify data in the database
- To generate dynamic web page content using templates (HTML pages are created dynamically on the server <-> static web page)

## How To Use Node.js

1. Install (for Mac)

  - `$ brew install node`

  - Or you can use **nvm** to install a specific version

  2. Manage Versions

  - `$ brew install nvm`

  - Install the latest LTS release of Node.js
    `$ nvm install --lts`

  - Install a specific version
    `$ nvm install 15.11.0`

  - List of installed versions
    `$ nvm ls`

  - Switch to another version
    `$ nvm use 14.16.0`

  - Switch to the latest LTS version
    `$ nvm use --lts`

3. Write Node.js File

```javascript
// index.js
const http = require('http');

http
	.createServer((req, res) => {
		res.statusCode = 200;
		res.setHeader('Content-Type', 'text/plain');
		res.end('Hello World!\n');
	})
	.listen(3000);
```

4. Initiate the Node.js File in the CLI
   `$ node index.js`
  - Now you can see the "Hello World" message on http://localhost:3000
