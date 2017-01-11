# PUT /PayCode/{Paycode}

#### Description
Updates an existing paycode.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`PUT https://localhost:81/PayCode/{Paycode}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
Paycode | path | string | true | The PAY_COD to update configuration information.
SY_PAY_COD | body | true | Paycode (SY_PAY_COD) to update. Include only fields to update.

- **<code>201 Created</code>** The request was successful, the user's roles were set.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The user or one or more roles in the role list do not exist.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role was added to the Counterpoint database.
- `NOT_FOUND`: The requested item was not found in the company data.

#### Sample Response Body
```
{
  "ErrorCode": "SUCCESS"
}
```
