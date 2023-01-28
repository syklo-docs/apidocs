---
layout: default
title: General info
nav_order: 2
---

# General API Information

- The base endpoint is:
`https://public-api.syklo.io/`
- All endpoints return either a JSON object or array.
- Data is returned in ascending order. Oldest first, newest last.
- All time and timestamp related fields are in milliseconds.
- HTTP 4XX return codes are used for for malformed requests; the issue is on the sender's side.
- HTTP 429 return code is used when breaking a request rate limit.
- HTTP 418 return code is used when an IP has been auto-banned for continuing to send requests after receiving 429 codes.
- HTTP 5XX return codes are used for internal errors; the issue is on Binance's side. It is important to NOT treat this as a failure operation; the execution status is UNKNOWN and could have been a success.
- Any endpoint can return an ERROR. The error payload is as follows:
```js
{
   "error":"TypeError: Cannot read property 'trim' of undefined"
}
```
- Specific error codes and messages defined in Error Codes.
- For GET endpoints, parameters must be sent as a query string.
- For POST, PUT, and DELETE endpoints, the parameters may be sent as a query string or in the request body with content type application/x-www-form-urlencoded. You may mix parameters between both the query string and request body if you wish to do so.
- Parameters may be sent in any order.
- If a parameter sent in both the query string and request body, the query string parameter will be used.

# LIMITS

- A 429 will be returned when either rate limit is violated.
- Each route has a weight which determines for the number of requests each endpoint counts for. Heavier endpoints and endpoints that do operations on multiple symbols will have a heavier weight.
- Every request will contain a X-MBX-USED-WEIGHT header which has the current used weight for the IP for the current minute.
- When a 429 returned, it's your obligation as an API to back off and not spam the API.
- Repeatedly violating rate limits and/or failing to back off after receiving 429 will result in an automated IP ban (http status 418).
- IP bans are tracked and scale in duration for repeat offenders, from 2 minutes to 3 days.
- A Retry-After header is sent with a 418 or 429 responses and will give the number of seconds required to wait, in the case of a 418, to prevent a ban, or, in the case of a 429, until the ban is over.

# Endpoint Security Type

- Each endpoint has a security type that determines the how you will interact with it.