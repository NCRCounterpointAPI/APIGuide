# POST /Role

#### Description
Adds a new customer to the database

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`POST https://localhost:81/Role`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

**Request Body**
```
{
  "Role": {
    "Name": "Role1",
    "EndpointList": [
      {
        "Path": "/Customer",
        "CanPost": "false",
        "CanGet": "true"
      }
    ]
  }
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
EndpointList | body | List<Endpoint> | true | The list of endpoints.
Name | body | string | true | The name of the role.

Endpoint | Required | Field Description
------- | -------- | -----------------
PATH | | The path for this endpoint.
CanGet | | The user can do GET requests on this endpoint.  Defaults to false.
CanPost | | The user can do POST requests on this endpoint.  Defaults to false.
CanPut | | The user can do PUT requests on this endpoint.  Defaults to false.
CanPatch | | The user can do PATCH requests on this endpoint.  Defaults to false.
CanDelete | | The user can do DELETE requests on this endpoint.  Defaults to false.

#### Response Codes
- **<code>201 Created</code>** The request was successful, the customer was added to the Counterpoint database.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer was added to the Counterpoint database.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the customer. See the Message field for more details.

#### Response Body


#### Sample Response Body
```
{
  "ErrorCode": "SUCCESS"
}
```

Field | Description
----- | -----------
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.

