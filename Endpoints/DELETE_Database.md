

# DELETE /Database/{Id}

#### Description
Deletes a database record from the **API Server**. Once deleted, the database/company is no longer recognized by the API server, and any company level calls made against the database/company will fail. Deleting a database only removes the API server's ability to work with the database/company, it does not delete the actual SQL database, nor does it modify companies.ini or anything else that would prevent Counterpoint from being used with the database/company. 

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`DELETE https://localhost:81/Database/1`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`

#### Parameters
Id: The Id of the Database to update information for.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "ErrorCode": "SUCCESS"
}
```




