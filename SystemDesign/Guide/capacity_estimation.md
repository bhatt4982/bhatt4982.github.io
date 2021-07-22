# Back of the envelop estimations

## Capacity Estimation

* One million transactions per day is:
  * ~42k per hour
  * ~700 per minute
  * ~12 per second

* 1 million per day --> ~12/second (12 * 1)
* 5 million per day --> ~60/second (12 * 5)
* 30 million per day --> ~360/second (12 * 30)
* 100 million per day --> ~1200/second (12 * 100)

* If a typical user generates 50 API calls during their session

  * 12 * 50 = ~600 TPS



| Users /day | Users (/second) | TPS (avg 50 txn per user) |
| ---------- | --------------- | ------------------------- |
| 1M         | 12              | 600                       |
| 5M         | 60              | 3000                      |
| 30M        | 360             | 18000                     |
| 100M       | 1200            | 60000                     |



### Approximates

* **Seconds in a day** 24 hours × 60 minutes × 60 seconds = 86,400 seconds = 100K seconds (Approximate)

* Let assume, we might expect to have 1K active users, each issuing 15 requests per day.

* That's 15K requests per day, or 15K/86400 requests per second.

* [Approximate] 20k requests in 100k seconds --> 0.2 requests per second

* For 1M users - 50 request per day --> 50M requests per day

  * 50M/86400 requests per second --> 600TPS
  * 50M/100k requests per second --> 500TPS
  *



### Peak Capacity

* For peak capacity, we could assume 10% traffic in an hour.
* For 1M users, that's 100k users per hour
* For 1 txn per user, that's 30 TPS (instead of 12 TPS)
* For 50 txn per user, that's 1500 TPS (instead of 600 TPS)



## Network Bandwidth

* 1 Gbps link

## Storage Estimations



## Storage Capacity
