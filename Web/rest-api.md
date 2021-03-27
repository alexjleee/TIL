# REST API

## What Is REST API

- REST

  **RE**presentational **S**tate **T**ransfer is an architectural style for designing networked applications. A web service that follows this style is called **RESTful**.

- API

  **A**pplication **P**rogramming **I**nterface is an interface that defines interactions between applications. 
  
  APIs are everywhere - from command-line tools to Web applications. 

  In many cases, an API refers to a web-based API that returns data (generally in JSON).

- REST API (RESTful API)

  An API that follows a set of constraints known as REST.

  Most APIs in the world are RESTful. REST has been the de facto standards for API since 2000.

  Technically, there is no _official_ standard for RESTful APIs since REST is an architectural style. But RESTful API makes use of standards, such as HTTP, URI, JSON (or XML). 

## When Do You Need RESTful API

- When the client (ex. a mobile app) needs to store and fetch data from the server but doesn't use HTML
- When the client needs to access the third-party features
- When the client (ex. a browser with SPA) needs to store and fetch data but doesn't render a second HTML page.

## Architectural Constraints

For an API to be _RESTful_, it needs to satisfy the following 6 guiding constraints.

1. Uniform Interface
  - The uniform interface is the fundamental constraint of REST API
    1. Identification of resources
      - anything that can be named is a resource (a document, an image, ...)
      - Resources are identified using URIs
      - Each URI should map a single resource and all the requests to the resource are made through that URI
    2. Resource manipulation through representations
      - The clients can access different representations (typically HTML, JSON and XML) of a resource from the same URI
      - A client request a specific representation of the resource through the HTTP `Accepts` header
    3. Self-descriptive messages
      - The representation in the response should be self-descriptive so that the client can understand and act on the resource
      - If any additional information is needed the response should provide links to the related resources
    4. Hypermedia as the engine of application state (**HATEOAS**)
      - HATEOAS allows the client to dynamically navigate resources through hypermedia links
      - The client enters the REST application through an initial URI and can discover available actions in the representation returned from the server
2. Client-Server Architecture
  - The user interface concerns are clearly separated from the data storage concerns 
3. Stateless
  - Each request must contain all of the information necessary to understand the request
  - The server doesn't store the client context between requests
4. Cacheability
  - The responses must define themselves as either cacheable or non-cacheable
5. Layered System
  - Ther can be multiple intermediate servers between the client and the end server
6. Code On Demand (Optional)
  - The server can temporarily extend the functionality of a client by transferring executable code
