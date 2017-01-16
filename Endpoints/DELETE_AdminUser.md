
# DELETE AdminUser/{UserId}
Deletes the provided administrator

#### Description

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`DELETE https://localhost:81/AdminUser/{UserId}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
- **UserId**: The API Admin User ID to delete.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The requested resource could not be found but may be available again in the future.  Subsequent requests by the client are permissible.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.
- `ERROR_RECORD_NOT_FOUND`: User record does not exist for the UserId given in parameter.
- `ERROR_CANNOT_DELETE_SYS_ADMIN`: Not allowed to delete USR_ID: admin

#### Sample Response Body

```
{
  "ErrorCode": "SUCCESS",
  "Message": "Admin User sucessfully Deleted"
}
```

#### Response Body

**Message**
