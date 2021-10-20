# API Design

## API Protocol

### REST vs SOAP

|                     REST                     |                         SOAP                          |
| :------------------------------------------: | :---------------------------------------------------: |
| REpresentational State Transfer Architecture |             Simple Object Access Protocol             |
|            Like a Postcard - Easy            |           Like an Envelop - Extra overhead            |
|              Easy to understand              |                      WS-Security                      |
|                Low bandwidth                 |                 Built-in retry logic                  |
|           Data formats - JSON/XML            |               Built-in ACID properties                |
|   Swagger - Interface Defination Language    |             Can not use cache efficiently             |
|                                              | Function driven WSDL(Web Service Defination Language) |

### REST vs GraphQL

|                     REST                     |                         Graph QL                         |
| :------------------------------------------: | :------------------------------------------------------: |
| REpresentational State Transfer Architecture |                   Graph Query Language                   |
|  Follows predefined endpoints and requests   | Allows it to tailor the request to the developer’s needs |
|  Problems likes overfetching/underfetching   |            Solves overfetching/underfetching             |
|                 Ease of use                  |                    Better performance                    |
|  Design based on HTTP(status, method & uri)  |             Design based on message exchange             |



## Throttling

1. Rate Limiting
2. API level
3. Concurrent connection limit
4. Resource level



## Security

1. HTTPS
2. Hashing
3. Never expose data in URL
4. OAuth