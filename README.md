# RedisRateLimiter
Rate Limiter implemented by Spring Cloud Gateway and Redis Lua Script.

This is an example for Spring Cloud Gateway's rate limit and it can be used in our service router.

Ramain tokens and calling times are counted in Redis, and we can define our default rate limit rules in traditional relation database or in nosql database, such as MongoDB and Redis.

It is recommanded default rules should be cached permantly in Redis. Because each calling will be rate limited according to those rules, and fetching them from database should be considered ASAP. We use Redis, nor local cache, when it happens in distributed system.

There are two algorithoms, in YEAR/MONTH/DAY and in HOUR/MINUTE/SECOND.

- YEAR/MONTH/DAY
    - Nature calendar time
    - Period time, which means we choose the start time and the end time.

- HOUR/MINUTE/SECOND

This uses token bucket algorithm, you can also find the similar codes in RedisRateLimiter in the given object in Spring Cloud Gateway.

## Technology Stack

- Spring Boot
- Spring Cloud
- Spring Cloud Gateway
- Redis
- Mongo(TBD)

## Programming Languages

- Java
- Lua

## Rate Limit Rule
### Default Rate Limit Rule
### Defined Rate Limit Rule

## Defined Rate Limiter's Key
**KeyResolver** is used to get you into multiple rate limited keys, and it combines them into one key.

**RateLimiterGatewayFilterFactory** is used to filter each api calling, we can also define our own filters with **extends** AbstractGatewayFilterFactory

# Author
- AtticusLv
- Beckjing