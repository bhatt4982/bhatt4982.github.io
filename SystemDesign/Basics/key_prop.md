# Key Properties

## Scalability

Scalability defines how your system reacts to the steep increase in workload.

**Workload** could refer to simultaneous users, storage capacity, the maximum number of transactions handled, or anything else that pushes the system past its original capacity. As the workload rises past the software’s ability to scale, performance drops.

### Vertical Scaling

**Scaling Up** essentially means using higher configuration hardware - bigger storage, higher computing power.

Vertical scaling is not the best solution as it has limitations - upper limit of hardware configuration and also hardware tends to become expensive as we go towards higher configuration.

### Horizontal Scaling

**Scaling Out** means scaling by adding more machines to pool of resources, without changing the size of any individual machine.

![scaling](img\scaling.png)

**[Example]**

Good examples of horizontal scaling are **Cassandra** and **MongoDB** as they both provide an easy way to scale horizontally by adding more machines to meet growing needs. Similarly, a good example of vertical scaling is **MySQL** as it allows for an easy way to scale vertically by switching from smaller to bigger machines. However, this process often involves downtime

#### [IMP] Scaling down

When we could scale down without a loss of performance, we should.

#### [IMP] Auto Scaling

Dynamically adjusts the amount of computational resources.

**AWS Auto Scaling** monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost.

## Availability

Availability means the probability that a system is operational at a given time, the time a system remains functional to perform its required task in a specific period.

Availability is presented as up time percent - AWS provides 99.999 percent ("five nines") availability

## Performance vs Scalability

## Reliability

Reliability denotes the ability of a distributed system to deliver its services even when one or several of its software of hardware components fail.

Reliability measures the ability of a system to function correctly and is assessed by maturity, fault tolerance, recoverability, and availability.

An immediate and obvious solution to provide reliability it to add **redundancy** -multiple services doing the same task(**replicas**), so if one fails, other could take its workload.

Obviously, redundancy has a cost and a reliable system has to pay that to achieve such resilience for services by eliminating every single point of failure.

If a system is reliable, it is available. However, if it is available, it is not necessarily reliable.

#### [IMP] Single point of failure

A single point of failure (SPOF) is a part of a system that, if it fails, will stop the entire system from working. We should eliminate every single point of failure.

## Serviceability

Serviceability or maintainability is the simplicity and speed with which a system can be repaired or maintained; if the time to repair a failed system increases, then availability will decrease.
