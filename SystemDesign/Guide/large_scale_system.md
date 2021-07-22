# System Design for Large Scale System

## Scale-up
**Stateless Microservices** - each server is exact replica of other and does not store any state information - any user related data like session or profile - on local disc or memory.
State information need to be stored in a centralized datastore accessible from all microservices.

**Modular** - each service design to do one task.

**Communication** - Lightweight messaging protocol like RabittMQ or Apache Kafka

**Service Registration and Discovery** - Consul, etcd, Apache Zookeeper or Netflix Eureka

Scale up, do **Load Analysis** and iterate.

## Database Optimizations

## Use a Cache
Application Cache
Database Cache
CDN
## Introduce Asynchronism
**Message Queue**
**Lazy Loading** - Asynchronous loading of assets

## Other Optimizations
Minimizing **network requests**
- Bundling assets
Server Side Rendering
