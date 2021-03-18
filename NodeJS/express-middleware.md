# Express Middleware

> **Middleware** functions are functions that have access to the _request object (`req`)_, the _response object(`res`)_, and the `next` function in the application's request-response cycle. (from [Express Guide](https://expressjs.com/en/guide/writing-middleware.html))

**Middleware** functions can execute any code after the server receives the request and before the response is sent.

```javascript
const express = require('express');
const app = express();

function logger(req, res, next) {
  console.log('LOG');
  next();
}

app.use(logger);
// use([path,] callback[, callback...]) : mount specified middleware function(s) at the specified path.
  // path : a string form of a path - default is '/'(root)
  // callback : middleware function

app.get('/', function(req, res) {
  console.log('Home Page');
  res.send('Home Page');
});
// get : HTTP method for which the middleware function applied
// '/' : route for which the middleware function applied

// Middleware
// function(req, res[, next]) { ... } : middleware function
  // req : HTTP request
  // res : HTTP response
  // next : the next middleware to be executed

app.listen(3000);

// LOG (the logger function is executed first)
// Home Page
```

Middlewares run in the order that they are defined (**written order** is important!). So, in general, write the global actions at the top of the file so that they happen before all the other controller actions.

## `req` & `res`

Middleware functions have access to the `req` and `res` objects and can make changes to them.

## `next`

`next()` calls the next middleware function in the application (middleware chaining). 

It could be named anything but follow the convention to avoid confusion.

If the current middleware does not end the _request-response cycle_, it must call `next()`.
- The **request-response cycle** starts when an HTTP request for a specific resource is made and it ends when a response is sent back to the user (for example, `res.send('Hello World')`).