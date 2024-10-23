# Meeting Types

## List meeting types

  This endpoint retrieves your meeting types.

### HTTP Request

```shell
curl -X GET "http://api.lemcal.com/api/lemcal/meeting-types" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)"
```

> The above command returns JSON structured like this:

```json

[
  {
    "_id": "met_RLejS4uWmhpqi694q",
    "userId": "usr_3k8N8agFoYCPcyivH",
    "name": "Meeting Type 1",
    "description": "A description",
    "meetingLink": "meeting-link-1",
    "type": "default",
    "color": "#EC6181",
    "duration": 30,
    "status": "enabled",
    "privacy": "public",
    "meetingLocations": [
      { "id": "LY5Q8Y6ciZNkgo8Sr", "provider": "googlemeet" }
    ],
    "questions": [
      {
        "id": "8retcc9tCAmuds7Q7",
        "answerType": "text",
        "enabled": false,
        "question": "A question"
      }
    ],
    "roundRobin": {
      "enabled": true,
      "users": [
        { "id": "usr_3k8N8agFoYCPcyivH", "enabled": true, "weight": 1 }
      ],
      "lastCycle": []
    }
  },
]

```

`GET http://api.lemcal.com/api/lemcal/meetingTypes`


### Response
List of meeting types

## Get a meeting type

This endpoint allows you to retrieve a specific meeting type by its `id`.

### HTTP Request

`GET http://api.lemcal.com/api/lemcal/meetingTypes/:_id`

```shell
curl -X GET "http://api.lemcal.com/api/lemcal/meetingTypes/:_id" \
     -H "Authorization: Basic $(echo -n 'userId:apiKey' | base64)" \

```

> The above command returns JSON structured like this:

```json

{
    "_id": "met_RLejS4uWmhpqi694q",
    "userId": "usr_3k8N8agFoYCPcyivH",
    "name": "Meeting Type 1",
    "description": "A description",
    "meetingLink": "meeting-link-1",
    "type": "default",
    "color": "#EC6181",
    "duration": 30,
    "status": "enabled",
    "privacy": "public",
    "meetingLocations": [
        { "id": "LY5Q8Y6ciZNkgo8Sr", "provider": "googlemeet" }
    ],
    "questions": [
        {
        "id": "8retcc9tCAmuds7Q7",
        "answerType": "text",
        "enabled": false,
        "question": "A question"
        }
    ],
    "roundRobin": {
        "enabled": true,
        "users": [
        { "id": "usr_3k8N8agFoYCPcyivH", "enabled": true, "weight": 1 }
        ],
        "lastCycle": []
    }
}

```

### Parameters

| Parameter        | Type    | Required | Description                                                                        |
| ---------------- | ------- | -------- | ---------------------------------------------------------------------------------- |
| `_id`            | string  | Yes      | The ID of the meeting type to retrieve. |


## Structure of a meeting type

| Property | Type | Description |
|----------|------|-------------|
| id | string | Unique identifier for the meeting type |
| userId | string | Identifier of the user who created this meeting type |
| name | string | Name of the meeting type |
| description | string | Brief description of the meeting type |
| meetingLink | string | Custom link for scheduling this meeting type |
| type | string | Type of the meeting (e.g., "default") |
| color | string | Hex color code associated with this meeting type |
| duration | number | Duration of the meeting in minutes |
| status | string | Current status of the meeting type ("enabled", "disabled") |
| privacy | string | Privacy setting for the meeting type ("public", "private") |
| meetingLocations | array | List of possible meeting locations/platforms |
| meetingLocations[].id | string | Unique identifier for the meeting location |
| meetingLocations[].provider | string | Provider of the meeting platform (e.g., "googlemeet") |
| questions | array | List of questions to be asked when scheduling |
| questions[].id | string | Unique identifier for the question |
| questions[].answerType | string | Type of answer expected (e.g., "text") |
| questions[].enabled | boolean | Whether the question is currently enabled |
| questions[].question | string | The actual question text |
| roundRobin | object | Settings for round-robin scheduling |
| roundRobin.enabled | boolean | Whether round-robin scheduling is enabled |
| roundRobin.users | array | List of users participating in round-robin |
| roundRobin.users[].id | string | Unique identifier of the user |
| roundRobin.users[].enabled | boolean | Whether the user is active in round-robin |
| roundRobin.users[].weight | number | Weight assigned to the user in round-robin selection |
| roundRobin.lastCycle | array | (Not used) |