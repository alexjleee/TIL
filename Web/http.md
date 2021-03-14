# HTTP

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
