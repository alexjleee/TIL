# View Engine (Template Engine)

> The view engines allow you to write **static template** files with _HTML syntax_, but also allows you to _insert dynamic data and logic_ into it.

Popular View Engines

  - [EJS](https://ejs.co/)
  - [pug](https://pugjs.org/api/getting-started.html)

## EJS

Install

```$ npm install ejs```

Syntax

  - `<%` ... `%>` : control-flow, no output
  - `<%=` ... `%>` : output the value into the template

How To Use

  ```javascript
  // app.js
  const express = require('express');
  const app = express();

  // register view engine
  app.set('view engine', 'ejs');

  // by default express will look into the 'views' folder but if you want to have views in a different folder, you have to tell the express
  app.set('views', '<name of the folder that holds views>'); 

  // render view
  app.get('/', (req, res) => {
    const blog = [
      {title: 'How To Go Plastic Free', snippet: 'Don\'t know where to start? Check this tips for an easy start'},
      {title: 'Eco Gifts for Christmas', snippet: 'Because Christmas will be so much nicer without plastics'},
      {title: 'Zero Waste Cleaning', snippet: 'Start zero waste cleaning with only 3 ingredients!'}
    ]
    // pass data as a second argument in the render method
    res.render('index', {title: 'Home', blogs})
  })
  ```

  ```javascript
  // index.ejs
  <html lang="en">
    <head>
      <meta charset="UTF=8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>MyBlog | <%= title %></title>
    </head>
    <body>
      <div class="title">
        <a href="/"><h1>MyBlog</h1></a>
        <p>Welcome to MyBlog</p>
      </div>
      <div class="content">
        <h2>Blog Posts</h2>
        <% if (blogs.length > 0) { %>
          <% blogs.forEach((blog) => { %>
            <h3 class="title"><%= blog.title %></h3>
            <p class="snippet"><%= blog.snippet %></p>
          <% }) %>
        <% } else { %>
          <p>No Blog Post</p>
        <% } %>
      </div>
    </body>
  </html>
  ```

- **Server-Side Rendering** : The EJS templates are processed through the EJS view engine on the server and the view engine makes a HTML based on the template and hand it over to the client. 