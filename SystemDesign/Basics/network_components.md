# Network Components

## Access Control List (ACL)

An access control list (ACL) contains rules that grant or deny access to certain digital environments. There are two types of ACLs:

- **Filesystem ACLs**━filter access to files and/or directories. Filesystem ACLs tell operating systems which users can access the system, and what privileges the users are allowed.

- **Networking ACLs**━filter access to the network. Networking ACLs tell routers and switches which type of traffic can access the network, and which activity is allowed.

  

### Role-Based Access List (RBAL)

RBAC is more effective than ACL in relation to administrative overheads and security



## Network Gateway

A network gateway joins two networks so the devices on one network can communicate with the devices on another network. 

Gateways are network protocol converters. Often the two networks that a gateway joins use different base protocols. The gateway facilitates compatibility between the two protocols. 

Depending on the types of protocols they support, network gateways can operate at any level of the OSI model.



## API Gateway

Rather than provide a one-size-fits-all style API, the API gateway can expose a different API for each client. For example, the Netflix API gateway runs client-specific adapter code that provides each client with an API that’s best suited to its requirements.

The API gateway might also implement security, e.g. verify that the client is authorized to perform the request



## Web Application Firewall(WAF)

A **web application firewall (WAF)** is a specific form of application firewall that filters, monitors, and blocks HTTP traffic to and from a web service.

By inspecting HTTP traffic, it can prevent attacks exploiting a web application's known vulnerabilities, such as SQL injection, cross-site scripting (XSS), file inclusion, and improper system configuration