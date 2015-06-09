
# GET /TaxCodes

#### Description
Gets information about all Tax Codes configured in the system.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/TaxCodes`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
None

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the TaxCode information is present under the `TaxCodes` section of the response body.

#### Sample Response Body

```
{
  "TaxCodes": [
    {
      "TAX_COD": "MEMTN",
      "DESCR": "Memphis, TN",
      "DESCR_UPR": "MEMPHIS, TN",
      "LST_MAINT_DT": "1999-07-26T16:39:47.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "RS_STAT": 0
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**TaxCode object**

Element | Datatype | Description
------- | -------- | -----------



