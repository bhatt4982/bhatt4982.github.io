# CAP Theorem

![cap_theorem](img\cap_theorem.png)



The **CAP theorem** states that it is impossible for a distributed data system to simultaneously provide more than two out of the following three guarantees:

**Consistency** which means that all clients see the same data at the same time, no matter which node they connect to. For this to happen, whenever data is written to one node, it must be instantly forwarded or replicated to all the other nodes in the system before the write is deemed ‘successful.’

**Availability** which means that that any client making a request for data gets a response, even if one or more nodes are down. 

**Partition tolerance** The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes

In Distributed network, partition failure is unavoidable. When a network partition failure happens should we decide to

1. Cancel the operation and thus decrease the availability but ensure consistency
2. Proceed with the operation and thus provide availability but risk inconsistency



**MongoDB** is a CP system. 

* It is a single-master system—each replica set can have only one primary node that receives all the write operations. 
* When the primary node becomes unavailable, the secondary node with the most recent operation log will be elected as the new primary node. Once all the other secondary nodes catch up with the new master, the cluster becomes available again. 
* As clients can't make any write requests during this interval, the data remains consistent across the entire network.



**Cassandra DB** is an AP system

* It delivers availability and partition tolerance but can't deliver consistency all the time.
* Cassandra doesn't have a master node, all the nodes must be available continuously. 
* However, Cassandra provides **eventual consistency** by allowing clients to write to any nodes at any time and reconciling inconsistencies as quickly as possible.
* However, constant availability results in a highly performant system that might be worth the trade-off in many cases.