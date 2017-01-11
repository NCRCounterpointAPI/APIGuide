
# GET /Store/{StoreId}/Tokenize

#### Description
Gets tokenization information for the store.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Store/MAIN/Tokenize`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
StoreId | path | string | true | The STR_ID to retrieve configuration information for.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The store does not exist.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the store information is present under the `PS_STR` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested store does not exist.

#### Sample Response Body

```
{
  "StoreId": "100",
  "NonTokenizedCount": 0,
  "TokenizedCount": 1,
  "BlankCount": 9,
  "ErrorCode": "SUCCESS"
}
```

#### Response Body
