# DELETE /User/{UserId}/Roles

#### Description
Deletes a user's assigned roles.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`DELETE https://localhost:81/User/{UserId}/Roles`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
UserId | path | string | true | The Counterpoint User Id.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the user's roles were deleted.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The user was not found or does not have any roles currently set.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role was added to the Counterpoint database.
- `ERROR_RECORD_NOT_FOUND`: The user was not found or does not have any roles currently set.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the role. See the Message field for more details.

#### Sample Response Body
```
{
  "ErrorCode": "SUCCESS",
  "Message": "User roles for user Z successfully deleted."
}
```

Field | Description
------ | -----------
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.
