# Client-Server Communication Protocols

## HTTP Request

![http_request](img\http_request.png)

**HTTP** works as a **request**-response protocol between a client and server. 

* A client (browser) sends an **HTTP request** to the server
* The server returns a response to the client
* The response contains status information about the **request** and may also contain the requested content

### HTTP Methods

- **GET**
- **POST**
- **PUT**
- **HEAD**
- **DELETE**
- **PATCH**
- **OPTIONS**

### HTTP Error Codes

* Informational responses (`100`–`199`)
  * `100 Continue`
  * `101 Switching Protocols`

* Successful responses (`200`–`299`)
  * `200 OK`
  * `201 Created`

* Redirects (`300`–`399`)
  * `307 Temporary Redirect`
  * `308 Permanent Redirect`

* Client errors (`400`–`499`)
  * `400 Bad Request`
  * `404 Page Not Found`

* Server errors (`500`–`599`)
  * `500 Internal Server Error`
  * `502 Bad Gateway`

## Ajax Polling

*  The client (browser) opens a connection and sends an **HTTP request** to the server

* The webpage sends requests to the server at regular interval (e.g. 500 milliseconds)

* The server returns a response to the client

  

## HTTP Long Polling

* The client (browser) opens a connection and sends an **HTTP request** to the server exactly as in normal polling
* The server holds the request open for a long time until timeout occurs or new data is available. 
* Once available, the server responds and sends the new information. 
* When the client receives the new information, it immediately sends another request, and the operation is repeated. 
* effectively emulates a server push feature. 



## Server Sent Events

* The client (browser) opens a connection and sends an **HTTP request** to the server
* The server holds the request open indefinitely until new data is available. 
* The server sends the data to the client whenever new information is available
* It provides half duplex communication channel
* SSEs are best when we need real time traffic from the server to the client



## Web Socket

* Web Socket provides **full duplex** communication channels over a single TCP channel.

* provides a persistent connection between a client and a server that both parties can use to start sending data at any time

  

## Pub/Sub - Push Notifications

* *Pub*/*Sub* is a flexible, reliable, real-time messaging service for independent applications to publish and subscribe to asynchronous events.
* The client subscribe to a channel with a server
* The server sends the data to the client whenever new information is available
* provides **full duplex** communication channels 

