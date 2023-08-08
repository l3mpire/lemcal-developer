# Errors

## General Errors

| Code | Message                  | Description                                                   |
|------|--------------------------|---------------------------------------------------------------|
| 400  | Bad Request              | The request was invalid or cannot be served.                  |
| 401  | Unauthorized             | The request requires user authentication.                     |
| 404  | Not Found                | The requested resource could not be found.                    |
| 405  | Method Not Allowed       | The request method is known by the server but is not supported by the target resource. |

## Specific Errors

### `/api/lemcal/hooks`

| Code | Message                  | Description                                      |
|------|--------------------------|--------------------------------------------------|
| 400  | You must provide a targetUrl | The `targetUrl` parameter is missing in the request body. |
| 400  | Invalid targetUrl        | The `targetUrl` provided is not a valid URL.     |
| 400  | You must provide either a meetingTypeId or anyMeetingType | The request must include either a `meetingTypeId` or `anyMeetingType`. |
| 404  | meeting type not found   | The provided `meetingTypeId` was not found in the system. |
| 409  | Duplicate hook           | A hook with the same details already exists.                  |

### `/api/lemcal/hooks/:id`

| Code | Message       | Description                           |
|------|---------------|---------------------------------------|
| 404  | hook not found | The specified hook could not be found in the system. |
