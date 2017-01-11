# POST /NSPTransaction

#### Description
POSTs a list of secure pay transactions from Monetra to the db

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`POST https://localhost:81//NSPTransaction`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
StoreList | body | string | false | List of secure pay store IDs.
StartDate | body | string | false | The secure pay store ID.
EndDate | body | string | false | The secure pay store ID.

#### Response Codes
- **<code>201 Created</code>** The request was successful, the customer was added to the Counterpoint database.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The requested resource could not be found but may be available again in the future.  Subsequent requests by the client are permissible.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the admin was added to the Counterpoint database.
- `ERROR_RECORD_NOT_FOUND`: No matching SY_USR record was found for the admin.

#### Response Body
Name | Parameter Type | Data Type | Description
---- | -------------- | --------- | -----------
NSPTransactions | body | NSP_Transaction | A list of settled and unsettled transactions from Monetra.
