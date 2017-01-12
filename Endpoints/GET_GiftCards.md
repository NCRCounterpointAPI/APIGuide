
# GET /GiftCards

#### Description
Gets a list of Gift Cards

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/GiftCards`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
None

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
  "GiftCards": [
    {
      "GFC_NO": "100001",
      "DESCR": "Gift Certificate",
      "DESCR_UPR": "GIFT CERTIFICATE",
      "ORIG_DAT": "2002-01-25T00:00:00.0000000",
      "ORIG_STR_ID": "MAIN",
      "ORIG_STA_ID": "1",
      "ORIG_DOC_NO": "100116",
      "ORIG_CUST_NO": "CASH",
      "GFC_COD": "GC",
      "NO_EXP_DAT": "Y",
      "ORIG_AMT": 50,
      "CURR_AMT": 0,
      "CREATE_METH": "G",
      "LIAB_ACCT_NO": "2090",
      "RDM_ACCT_NO": "2090",
      "RDM_METH": "!",
      "FORF_ACCT_NO": "8510",
      "IS_VOID": "N",
      "LST_ACTIV_DAT": "2002-01-25T00:00:00.0000000",
      "LST_MAINT_DT": "2002-09-24T11:38:15.0000000",
      "LST_MAINT_USR_ID": "Z",
      "LST_LCK_DT": "2002-01-25T15:37:42.2100000",
      "ORIG_DOC_ID": 201325549094,
      "ORIG_BUS_DAT": "2002-01-25T00:00:00.0000000",
      "RS_STAT": 0,
      "SY_GFC_ACTIV": []
    }
    ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



