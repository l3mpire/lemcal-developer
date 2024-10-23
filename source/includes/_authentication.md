# Authentication

> To authorize, use this code:

```shell
curl -X GET "http://api.lemcal.com/api/lemcal/me" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)"
```

All lemcal API routes are accessed via the dedicated subdomain api.lemcal.com.

Authentication is performed using the Basic authentication type in the Authorization header. The format for this header is username:password that can be obtained [here](https://app.lemcal.com/integrations).