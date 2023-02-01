---
layout: default
title: General info
nav_order: 2
---

# General API Information

- The base endpoint is: `https://public-api.syklo.io/`
- Data is updated every 5 minutes.
- All endpoints return either a JSON object or array.
- Unix timestamps are in milliseconds.
- Any endpoint can return an ERROR. The error payload is as follows:
```js
{
   "error":"TypeError: Cannot read property 'trim' of undefined"
}
```

# LIMITS

- A 429 will be returned when either rate limit is violated.
- When a 429 returned, it's your obligation as an API to back off and not spam the API.
- Repeatedly violating rate limits and/or failing to back off after receiving 429 will result in an automated IP ban (http status 418).
- IP bans are tracked and scale in duration for repeat offenders, from 2 minutes to 3 days.
- A Retry-After header is sent with a 418 or 429 responses and will give the number of seconds required to wait, in the case of a 418, to prevent a ban, or, in the case of a 429, until the ban is over.
