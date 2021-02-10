# Client-Server Model

* The server component provides a function or service to one or many clients, which initiate requests for such services.

# ![client-server](img\client-server.png)



## Monolith Architecture

* a unified model for the design of a software program
* tightly coupled components
* designed to be self-contained

### Benefits

* Simple to develop
* Simple to test
* Simple to deploy
* Simple to scale
* Fit for early stages of the project

### Drawbacks

* difficult to scale when different modules have conflicting resource requirements.
* require redeployment of the entire application on each update
* creates barrier to adopt new technologies
* less reliable - as a bug in one module affects complete system

## Microservice

* a variant of the service-oriented architecture (SOA) structural style – arranges an application as a collection of loosely coupled services.

### Benefits

* each service to be developed independently
* enables each service to be scaled independently
* reduces barrier of adopting new technologies

### Drawbacks

* adds a complexity
  * inter-process communication mechanism based on either messaging or RPC 
  * code to handle partial failure 
* difficult to implement changes that span multiple services
* difficult to test
* deploying a microservices-based application is also more complex

### Stateless Microservices

* server processes requests based only on information relayed with each request and doesn’t rely on information from earlier requests
* server doesn’t need to hold onto state information between requests (or the state can be held into an external service, like a database)
* different requests can be processed by different servers
* enables resiliency, elasticity, and improves availability



![server_type](E:\git\bhatt4982.github.io\SystemDesign\Basics\img\server_type.jpg)

## Distributed System

* A distributed system, also known as distributed computing, is a system with multiple components located on different machines that communicate and coordinate actions in order to appear as a single coherent system to the end-use

## Characteristics

* all components run concurrently
* no global clock
* all components fail independently of each other

## Benefits

* Horizontal Scalability
* Reliability
* Performance

## Challenges

* Scheduling
* Latency
* Observability

