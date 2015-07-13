# GET /Users/Roles

#### Description
Gets a list of users and their assigned roles.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Users/Roles`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Response Codes
- **<code>200 OK</code>** The request was successful, the user data was returned.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the user data was returned.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the role. See the Message field for more details.

**Response Body**
```
{
  "UserList": [
    {
      "UserId": "MGR",
      "RoleList": [
        "Role1",
        "Role2"
      ]
    },
    {
      "UserId": "POS1",
      "RoleList": [
        "Role2"
      ]
    },
    {
      "UserId": "Z",
      "RoleList": [
        "Role3"
      ]
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**UserList**

Element | Datatype | Description
------- | -------- | -----------
UserList | List | The list of UserRoles data.

**UserRoles object**

Element | Datatype | Description
------- | -------- | -----------
UserId | string | The users counterpoint id.
RoleList | List | The string list of roles this user is assigned.
