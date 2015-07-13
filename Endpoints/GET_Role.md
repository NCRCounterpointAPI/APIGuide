# GET /Role

#### Description
Gets a role.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Role/{RoleName}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
RoleName | path | string | true | The name of the role to add or update.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the roles data was returned.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The request could not be fulfilled.  The role name provided was not found.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role data was returned.
- `ERROR_RECORD_NOT_FOUND`: The role name provided was not found.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the role. See the Message field for more details.

**Response Body**
```
{
  "role": {
    "name": "Test8",
    "endpoints": [
      {
        "path": "/Document",
        "verbsAllowed": [
          "POST"
        ]
      },
      {
        "path": "/Document/{DocId}/Contact",
        "verbsAllowed": [
          "PATCH",
          "DELETE"
        ]
      }
    ]
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Role object**

Element | Datatype | Description
------- | -------- | -----------
name | string | The name of the role.
endpoints | List<Endpoint> | The list of endpoints available to this role.

**Endpoint object**

Element | Datatype | Description
------- | -------- | -----------
path | string | The path of this endpoint.
verbsAllowed | List<string> | The list of verbs allowed for this endpoint path.
