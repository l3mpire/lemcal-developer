---
title: lemcal - Developer Documentation

toc_footers:
  - <a href='https://lemcal.com'>lemcal homepage</a>
  - <a href='https://help.lemcal.com'>lemcal FAQ</a>

includes:
  - definitions
  - authentication
  - meetings
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API

---

# Introduction

Welcome to the lemcal Developer Documentation.
# Rate Limit

lemcal's API rate limits requests in order to prevent abuse and overload of our services.  
Rate limits are applied on all routes and per api key performing the request.  
The rate limits are **20** requests per **2** seconds.

The response provide any information you may need about it:

> Example of values for the rate limit headers

```json
{
  "Retry-After": 2,
  "X-RateLimit-Limit": 20,
  "X-RateLimit-Remaining": 7,
  "Retry-After" : "Tue Feb 16 2021 09:02:42 GMT+0100 (Central European Standard Time)"
}
```

Header    | Description
--------- | -----------
Retry-After | The number of second in which you can retry
X-RateLimit-Limit | The maximum requests in that time
X-RateLimit-Remaining | The number of remaining requests you can make
X-RateLimit-Reset | The date when the rate limit will reset


