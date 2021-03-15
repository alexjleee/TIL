# HTTP

## What Is HTTP

> **H**yper**T**ext **T**ransfer **P**rotocol is the foundation of data communication between the web browsers (_clients_) and the web _servers_.

- HTTP is a **TCP/IP** based communication protocol.

  - TCP : Transmission Control Protocol. Handle packet ordering and error checking.
  - IP : Internet Protocol. Deliver packets of information from the source host to the destination host based on the _IP addresses_ (a numeric label assigned to each device connected to a computer network).
  - TCP/IP, also know as **Internet Protocol Suite**, is a suite of communication protocols used for communication and data exchange over the internet.

- HTTP is media independent. HTTP can deliver **any type of data** (not only HTML but also images, videos and many others) as long as both the client and the server know how to handle the data content.

- HTTP is a **client-server (request-response) protocol**. The client makes a **request** and the server **responds**.

- HTTP is **connectionless (non-persistent)**. After receiving a response back from the server, the client closes the connection.

  1. Client makes a TCP connection to the server
  2. Server accepts connection
  3. Client sends HTTP request
  4. Server sends HTTP response
  5. Client closes connection

- HTTP is a **stateless protocol**. The requests are independent of each other and the server doesn't need to track the state information.

- But HTTP cookies allow the use of **stateful sessions**. HTTP requests can share the same state through HTTP cookies.

## What Is HTTPS

> **H**yper**T**ext **T**ransfer **P**rotocol **S**ecure is HTTP with a _security_ feature.

In standard HTTP, all information is sent in readable text which makes it vulnerable to hackers.

All the data that is retrieved by HTTP is encrypted (turned into unreadable text) by SSL(Secure Sockets Layer) or by TLS(Transport Layer Security)

- SSL : A protocol that uses public-key encryption to secure data.
- TLS : It is the successor to SSL and like SSL, it authenticates the server, client and encrypts the data.

If the user needs to send sensitive information, make sure to use HTTPS over HTTP. You can do it by installing a certificate on the web host.

Google warns the users ("_Your connection to this site is not secure_") if the website is not SSL protected. So, many websites use HTTPS regardless if sensitive data is being exchanged or not.

## HTTP Request

The client submits an HTTP request to the server. An HTTP request consists of 3 parts: the _request line_, the _request headers_, and the _request body_. The request line and the request headers are called the _request message header_ and a blank line separates the header and the body.

### Request Line

The request line consists of 3 parts: the _request method_, the _request-URI_ and the _HTTP version_

- Example : `GET /doc/test.html HTTP/1.1`

#### HTTP Request Methods

1. GET

    To request data from the server

    - A query string(`name=value` pairs) is sent in the URL of a GET request.
    - If you use GET request on a form, it is not secure since the data is visible in the URL. So don't use GET on a form (unless it is a kind of search form), use GET only to retrieve data.
    - It is considered a safe, **idempotent** method since a GET request does not modify any resources.
    - It is cacheable, can be bookmarked and it remains in the browser history.
    - It has a restriction on data length (2,048 characters - the number of characters in the actual path)

2. POST

    To send data to the server to create or update a resource

    - The data sent is stored in the _request body_
    - It is **non-idempotent** since a POST request modifies a resource in the server.
    - Calling the same POST request multiple times will create the same resource multiple times (unwanted side effect)
    - It is not cacheable, cannot be bookmarked and does not remain in the browser history.
    - It does not have any restriction on data length.

3. PUT

    To update data already on the server or add if the resource does not exist

    - Beware that PUT assumes the resource does not exist or it is okay to be overwritten.
    - It is similar to POST. The difference is that a PUT request is **idempotent**.
    - Calling the same PUT request multiple times will not produce side effects.

4. DELETE

    To delete the targeted resource from the server

    - Be careful not to delete data unintentionally
