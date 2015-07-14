# PUT /Role/{RoleName}/Users

#### Description
Add or update the users list belonging to the role.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`PUT https://localhost:81/Role/{RoleName}/Users`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
RoleName | path | string | true | The name of the role to update.
UserList | body | List | true | The list of Counterpoint users for the role.

**Request Body**
```
{
    "UserList": [
        "MGR",
        "POS1",
        "POS2"
    ]
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
----- | -------------- | --------- | -------- | -----------
UserList | body | List | true | The list of Counterpoint users for the role.

#### Response Codes
- **<code>201 Created</code>** The request was successful, the users for the role were set.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The role name or one or more users provided do not exist.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role was added to the Counterpoint database.
- `ERROR_RECORD_NOT_FOUND`: The role name or one or more users provided do not exist.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the users. See the Message field for more details.

#### Response Body


#### Sample Response Body
```
{
  "ErrorCode": "SUCCESS",
  "Message": "Users successfully added for role: Test1"
}
```

Field | Description
------ | -----------
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.
