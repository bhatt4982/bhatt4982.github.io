# Designing a URL Shortening Service

**[Examples]**
[tinyurl](https://tinyurl.com/)
[bitly](https://bitly.com/)
[ow.ly](https://www.hootsuite.com/pages/owly)
[short.io](https://short.io/)

**[Difficulty Level]**
**Easy** :innocent:

## Requirement

### FR

* Generate **shorter and unique alias** for a URL
* Short link **redirects** to Original links
* Support for **Custom URL**
* **TTL** for links

### NFR

* High availability
* Minimal latency

### Extended Requirements

* Analytics
* REST API

## Estimations

### Capacity Estimation

* 500M new URL shortening requests per month
* 100:1 read-write ratio
  * 500M write requests
  * 100 * 500M => 50B read requests
* Queries per second - 500M/30*100k => 200 requests/sec
* Peak traffic
  * 500M request per month => 20M request per day
  * 10% --> 2M request per hr => 500 requests/sec
* URL Redirections
  * 100 * 200 requests/sec => 20k requests/sec

### Storage Estimation

* One URL shortening record => 1Kb
* 5 yrs records => 500M * 12 months * 5 yrs => 30B records
* 30 B records * 1KB => 30 TB

### Bandwidth Estimation

* URL shortening => 200 * 1KB => 200 KB/s
* Peak URL shortening => 500 * 1KB => 500 KB/s
* URL redirection => 20k * 1KB => 20 MB/s

### Memory Estimation

* [80-20 rule] 20% URLs generate 80% traffic
* 20k requests/sec => 20k * 100k => ~2B request/day
* 20% hot URLs
  * 20% of 2B * 1KB => 4B * 1KB => 4 GB

## API Design

* Shorten URL
* Redirect URL
* Delete URL

## Data Model

* URL
  * hash [PK]
  * url
  * user_id
  * ttl
  * is_valid
  * created_at

###
