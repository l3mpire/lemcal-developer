# User

## Get User Information

This endpoint retrieves your information.

  ```shell
curl -X GET "http://api.lemcal.com/api/lemcal/me" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "usr_BuDuyx4chjoNfcmzM",
    "email": "john@email.com",
    "publicIdentifier": "john",
    "createdAt": "2022-10-17T07:43:50.740Z"
}
```

### HTTP Request

`GET http://api.lemcal.com/api/lemcal/me`

### Query Parameters

No query parameters are required for this endpoint.