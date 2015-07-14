# GET /Roles/Users

#### Description
Gets a list of all roles with permissions and assigned users.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Roles/Users`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Response Codes
- **<code>200 OK</code>** The request was successful, the roles data was returned.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role data was returned.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the role. See the Message field for more details.

**Response Body**
```
{
  "roleList": [
    {
      "Name": "Role1",
      "Users": [
        "MGR",
        "POS1",
        "Z2"
      ],
      "endpointList": [
        {
          "Path": "/Company",
          "HasGet": true,
          "HasPost": false,
          "HasPatch": false,
          "HasPut": false,
          "HasDelete": false,
          "CanGet": false,
          "CanPost": false,
          "CanPatch": false,
          "CanPut": false,
          "CanDelete": false
        },
        {
          "Path": "/Customer",
          "HasGet": false,
          "HasPost": true,
          "HasPatch": false,
          "HasPut": false,
          "HasDelete": false,
          "CanGet": false,
          "CanPost": true,
          "CanPatch": false,
          "CanPut": false,
          "CanDelete": false
        },
        {
          "Path": "/Store/{StoreId}",
          "HasGet": true,
          "HasPost": false,
          "HasPatch": false,
          "HasPut": false,
          "HasDelete": false,
          "CanGet": false,
          "CanPost": false,
          "CanPatch": false,
          "CanPut": false,
          "CanDelete": false
        }
      ]
    },
    {
      "Name": "Role2",
      "Users": [
        "MGR",
        "POS1"
      ],
      "endpointList": [
        {
          "Path": "/Company",
          "HasGet": true,
          "HasPost": false,
          "HasPatch": false,
          "HasPut": false,
          "HasDelete": false,
          "CanGet": true,
          "CanPost": false,
          "CanPatch": false,
          "CanPut": false,
          "CanDelete": false
        },
        {
          "Path": "/Customer",
          "HasGet": false,
          "HasPost": true,
          "HasPatch": false,
          "HasPut": false,
          "HasDelete": false,
          "CanGet": false,
          "CanPost": false,
          "CanPatch": false,
          "CanPut": false,
          "CanDelete": false
        },
        {
          "Path": "/Store/{StoreId}",
          "HasGet": true,
          "HasPost": false,
          "HasPatch": false,
          "HasPut": false,
          "HasDelete": false,
          "CanGet": true,
          "CanPost": false,
          "CanPatch": false,
          "CanPut": false,
          "CanDelete": false
        }
      ]
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**roleList**

Element | Datatype | Description
------- | -------- | -----------
roleList | List | A list of roles.

**Role object**

Element | Datatype | Description
------- | -------- | -----------
Name | string | The name of the role.
Users | List | The list of users assigned to this role.
endpointList | List | The full list of endpoints containing permissions set for this role.

**Endpoint object**

Element | Datatype | Description
------- | -------- | -----------
Path | string | The path of this endpoint.
HasGet | bool | There is an API call for this path that supports the GET verb.
HasPost | bool | There is an API call for this path that supports the POST verb.
HasPatch | bool | There is an API call for this path that supports the PATCH verb.
HasPut | bool | There is an API call for this path that supports the PUT verb.
HasDelete | bool | There is an API call for this path that supports the DELETE verb.
CanGet | bool | This role has GET permission on this path.
CanPost | bool | This role has POST permission on this path.
CanPatch | bool | This role has PATCH permission on this path.
CanPut | bool | This role has PUT permission on this path.
CanDelete | bool | This role has DELETE permission on this path.
