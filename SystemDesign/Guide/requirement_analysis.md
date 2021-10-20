# Ask the right questions - Requirement Analysis

* Recognize the number of users
* Estimate users growth rate (for the next year/next five years)
* Define average response time
* Understand database size
* Understand storage requirements
* Define acceptable downtime of the system
* Define time to market

## Functional Requirements (FR)
* defines a system or its component
* product **feature** and user **requirements**
* define the basic system behavior - **what** the system does or must not do
* It is captured in use case - user stories
* Functional Testing like System, Integration, End to End, API testing etc.

## Non-Functional Requirements (NFR)
* defines the performance attribute of a software system
* product **properties** and focus on user **expectations**
* Non-Functional Testing like Performance, Stress, Usability, Security testing etc.
* PASSME
  * Performance
  * Availability
  * Scalability
  * Security
  * Maintainability
  * Extensibility

## Define Scope
* which **features** system supports and which **properties** are critical
* what system design will reflect on
* Identify key problem and algorithm to support it

## Define Out-of-Scope
* what is oblivious or less important and could be skipped in further discussion

## Key Questions to answer

### Users/Customers

* Who will use the system?
* How the system will be used?

### Scale (Reads & Writes)

* How many read queries per second?
* How much data is queries per request?
* Can there be any spikes in traffic?

### Performance

* What is expected write-to-read data delay?
* What is expected P99 latency for read queries?

### Cost

* Should the design minimize the cost of development?
* Should the design minimize the cost of Maintainance?

