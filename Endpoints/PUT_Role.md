# PUT /Role

#### Description
Add or update a role.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`PUT https://localhost:81/Role/{RoleName}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
RoleName | path | string | true | The name of the role to add or update.
Role | body | Object | true | The role contains a list of endpoints available.

**Request Body**
```
{
    "Role": {
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
        ]
    }
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
----- | -------------- | --------- | -------- | -----------
endpoints | body | List<Endpoint> | true | A list of endpoints available for this role.

Endpoint | Required | Field Description
-------- | -------- | -----------------
Path | true | The path for this endpoint.
VerbsAllowed | true | The verbs allowed for this path.

#### Response Codes
- **<code>201 Created</code>** The request was successful, the customer was added to the Counterpoint database.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role was added to the Counterpoint database.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the role. See the Message field for more details.

#### Response Body


#### Sample Response Body
```
{
  "ErrorCode": "SUCCESS"
}
```

Field | Description
------ | -----------
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.
