# Tools

## Key Value Stores

* [ETcd](https://etcd.io)
  * a strongly consistent, distributed key-value store
  * read and write values using standard HTTP tools, such as curl
  * written in [Go](https://golang.org/), which has excellent cross-platform support

## Databases

* [Dynamo](https://aws.amazon.com/dynamodb/)
  * a key-value and document database(NoSQL)
* [Cassandra](https://cassandra.apache.org/)

## Message Queue

* [Apache Kafka](https://kafka.apache.org/)
  * an open-source distributed event streaming platform for high-performance data pipelines, streaming analytics, data integration, and mission-critical applications
* [RabbitMQ](https://www.rabbitmq.com/)

## Configuration

* [Apache Zookeeper](https://zookeeper.apache.org/)
  * a centralized service for maintaining configuration information, naming, providing distributed synchronization, and providing group services.

## File System

* [Apache Hadoop](https://hadoop.apache.org/)
  * a distributed file system

## Map Reduce

* [Hadoop MapReduce](https://hadoop.apache.org/docs/r1.2.1/mapred_tutorial.html)
  * Simplified data processing on large clusters
* [Dockers](https://www.docker.com)
  * a tool designed to make it easier to create, deploy, and run applications by using containers.
  * Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies, and deploy it as one package.

## CI/CD

* [Jenkins](https://www.jenkins.io)
  * a free and open source automation server
  * helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery.
* [Bitrise.io](https://www.bitrise.io/)
* [GitLab](https://about.gitlab.com/)

## Cache

* [Redis](https://redis.io/)
  * an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker
  * provides data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes, and streams
  * has built-in replication, Lua scripting, LRU eviction, transactions, and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.
* [MemCache](https://memcached.org)
  * an in-memory key-value store for small chunks of arbitrary data (strings, objects) from results of database calls, API calls, or page rendering.
  * its simple design promotes quick deployment, and ease of development.
* [nginx](https://nginx.org)
  * **nginx** is a web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.



------



# Protocol

## Leader Selection

* [Paxos Protocol](https://www.cs.rutgers.edu/~pxk/417/notes/paxos.html)
  * Paxos is an algorithm that is used to achieve **consensus among a distributed set** of computers that communicate via an asynchronous network.
  * One or more clients proposes a value to Paxos and we have consensus when a majority of systems running Paxos agrees on one of the proposed values.

## Peer-to-peer Communication

* [Gossip Protocol](https://en.wikipedia.org/wiki/Gossip_protocol)
  * a procedure or process of computer peer-to-peer communication
  * maintain relaxed consistency requirements amongst a very large group of nodes
  * simple in concept - each nodes sends out some data to a set of other nodes. Data propagates through the system node by node like a virus.
  * used by Cassandra/Riak NoSQL databases.
