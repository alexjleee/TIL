# Express Middleware

> **Middleware** functions are functions that have access to the _request object (`req`)_, the _response object(`res`)_, and the `next` function in the application's request-response cycle. (from [Express Guide](https://expressjs.com/en/guide/writing-middleware.html))

**Middleware** is the primary means of code reuse in Express.

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
  // path : a string form of a path
    // default is '/'(root), the middleware function will be applied to all the paths
    // if you pass a specified path, Express will execute the middleware only when it receives a request for a URL that starts with the given path
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

## Frequently Used Middlewares

1. [body-parser](https://github.com/expressjs/body-parser)
  - Parse incoming request bodies in a middleware before the custom handlers, available under the `req.body` property.
  ```javascript
  const express = require('express');
  const bodyParser = require('body-parser');

  const app = express();

  // html form -> .urlencoded(), json -> .json()
  app.use(bodyParser.urlencoded({ extended: true }));
  // extended: true -> qs library, false -> querystring library

  ...
  ```

2. [moran](https://github.com/expressjs/morgan)
  - Log HTTP requests and errors
  ```javascript
  const express = require('express');
  const morgan = require('morgan');

  const app = express();

  // morgan(format, option)
  // predefined format string 'tiny' provides the minimal output when logging HTTP requests (:method :url :status :res[content-length] - :response-time ms)
  app.use(morgan('tiny'));
  // you can use format tokens, or custom format function

  ...
  ```