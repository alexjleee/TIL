# Express

> Express is a minimal and flexible NodeJS  framework to handle HTTP requests. It helps in creating a web server easier.

Install : `$ npm i express`

## Basic Server Example

1. Creating server using **`http` module** in NodeJS

```javascript
const http = require('http');

const requestListener = function(req, res) {
  res.writeHead(200);
  res.write('Hello World');
  res.end();
}

const server = http.createServer(requestListener);

server.listen(3000);
```

2. Creating server using **Express API**

```javascript
// Require the Express module installed via npm
const express = require('express');
// Set up Express application
const app = express();

// Route Handler : take incoming request, look at the path and method and call the appropriate callback function that is registered
app.get('/', (req, res) => {
  // Send a response with content in the body of the response (if the content looks like HTML, the client will treat it like an HTML)
  res.send('Hello World');
}); 
  // .get() : watch for incomming request that has method GET
  // '/' : root route

// Start listening for incoming requests on port 3000
app.listen(3000);
```