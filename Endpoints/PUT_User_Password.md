# PUT /User/Password

#### Description
Updates the authenticated user's password.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`PUT https://localhost:81/User/Password`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
UserId | path | string | true | The Counterpoint User Id.
RoleList | body | List | true | The list of roles to assign to the user.

**Request Body**
```
{
  "newPassword": "testpsswd2",
  "oldPassword": "testpsswd1",
  "UserId": "MGR2",
  "Company": "QATestGolf852"
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
----- | -------------- | --------- | -------- | -----------
Company | body | string | true | The company.
UserID | body | string | true | The user to update.
oldPassword | body | string | true | The value of old password.
newPassword | body | string | true | The value of new password.


#### Response Codes
- **<code>201 Created</code>** The request was successful, the user's roles were set.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The user or one or more roles in the role list do not exist.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: Password successfully changed.

#### Sample Response Body
```
{
  "ErrorCode": "SUCCESS",
  "Message": "Password successfully changed."
}

Field | Description
------ | -----------
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.
