# Meetings

## List booked meetings

  This endpoint retrieves your booked meetings.

### HTTP Request

```shell
curl -X GET "http://api.lemcal.com/api/lemcal/meetings" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)"
```

> The above command returns JSON structured like this:

```json

[
  {
      "_id": "mee_NSXBft76yJoMh5Bik",
      "userId": "usr_BuDuyx4chjoNfcmzM",
      "meetingTypeId": "met_4HdebtnSiwFpFb6BF",
      "providedInfos": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
      "eventId": "fkne3iuvmjsvi9cf746s39obfc",
      "start": "2023-03-24T15:30:00.000Z",
      "end": "2023-03-24T16:00:00.000Z",
      "lead": {
          "email": "alice@example.com",
          "firstName": "alice",
          "lastName": "smith",
      },
      "attendees": [
          {
              "email": "alice@example.com",
              "name": "alice",
              "type": "required",
              "response": "accepted"
          },
          {
              "email": "bob@example.com",
              "type": "required",
              "response": "accepted"
          }
      ],
      "createdAt": "2023-07-19T13:23:39.910Z"
  },
]

```

`GET http://api.lemcal.com/api/lemcal/meetings`

### Query Parameters

| Parameter     | Type   | Required  | Description                                           |
| ------------- | ------ | --------- | ----------------------------------------------------- |
| `meetingTypeId` | string | No | Filter meetings by a specific meeting type.            |


### Response

Parameter       | Description
--------------- | --------------------------------------------------------------------------------------------
_id             | Unique identifier for the meeting.
userId          | Identifier for the user associated with the meeting.
meetingTypeId   | Identifier for the type of meeting.
providedInfos   | Additional text information about the meeting.
eventId         | Unique identifier for the related event.
start           | Start time of the meeting in ISO 8601 format.
end             | End time of the meeting in ISO 8601 format.
lead.email      | Lead's email address.
lead.firstName  | Lead's first name.
lead.lastName   | Lead's last name.
attendees       | List of attendees for the meeting (includes email, name, type, response).
createdAt       | Creation date and time of the meeting in ISO 8601 format.

## Create a Hook

This endpoint allows you to create a hook to a specified target URL. Hooks can be associated with a specific meeting type or applied to any meeting type.

### HTTP Request

`POST http://api.lemcal.com/api/lemcal/hooks/`

```shell
curl -X POST "http://api.lemcal.com/api/lemcal/hooks" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)" \
     -H "Content-Type: application/json" \
     -d '{
         "targetUrl": "http://example.com/callback",
         "meetingTypeId": "met_4HdebtnSiwFpFb6BF",
         "anyMeetingType": true
     }'
```

> The above command returns JSON structured like this:

```json

{
    "_id": "hoo_NSXBft76yJoMh5Bik",
    "targetUrl": "http://example.com/callback",
    "meetingTypeId": "met_4HdebtnSiwFpFb6BF",
    "anyMeetingType": true,
    "createdAt": "2022-10-17T07:43:50.740Z"
}

```

### Request Body

| Parameter        | Type    | Required | Description                                                                        |
| ---------------- | ------- | -------- | ---------------------------------------------------------------------------------- |
| `targetUrl`      | string  | Yes      | The target URL for the hook. Must be a valid URL starting with `http://` or `https://`.|
| `meetingTypeId`  | string  | No | The ID of a specific meeting type to associate with the hook. Cannot be used with `anyMeetingType`. |
| `anyMeetingType` | boolean | No | If set to `true`, the hook applies to any meeting type. Is prior to `meetingTypeId`. |

*Note*: You must provide either `meetingTypeId` or `anyMeetingType`.

## Delete a Hook

This endpoint allows you to delete an existing hook by its `id`.

```shell
curl -X DELETE "http://api.lemcal.com/api/lemcal/hooks/:id" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)" \
     
```

> The above command deletes the specified hook and returns a `204 No Content` status code.

### HTTP Request

`DELETE http://api.lemcal.com/api/lemcal/hooks/:id`

Replace `:id` with the actual ID of the hook you want to delete.

### URL Parameters

| Parameter | Type   | Required | Description                  |
| --------- | ------ | -------- | ---------------------------- |
| `id`      | string | true     | The ID of the hook to delete.|
