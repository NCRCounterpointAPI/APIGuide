
# GET /GiftCardCodes

#### Description
Gets a list of Gift Card Codes.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/GiftCardCodes`

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
  "GiftCardCodes": [
    {
      "GFC_COD": "CG100",
      "DESCR": "$100 Gift Card",
      "DESCR_UPR": "$100 GIFT CARD",
      "SELL_DESCR": "$100 Gift Card",
      "DFLT_AMT": 100,
      "ALLOW_AMT_CHNG": "Y",
      "LIAB_ACCT_NO": "2090",
      "LIAB_METH": "!",
      "RDM_ACCT_NO": "2090",
      "RDM_METH": "!",
      "FORF_ACCT_NO": "8510",
      "FORF_METH": "!",
      "CREATE_AS_STC": "Y",
      "USE_RDR": "Y",
      "LST_MAINT_DT": "2016-04-06T09:24:53.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "RS_UTC_DT": "2016-04-06T13:24:53.2430000",
      "RS_STAT": 1
    },
    {
      "GFC_COD": "GC",
      "DESCR": "Gift Card",
      "DESCR_UPR": "GIFT CARD",
      "SELL_DESCR": "Gift Card",
      "DFLT_AMT": 20,
      "ALLOW_AMT_CHNG": "Y",
      "LIAB_ACCT_NO": "2090",
      "LIAB_METH": "!",
      "RDM_ACCT_NO": "2090",
      "RDM_METH": "!",
      "FORF_ACCT_NO": "8510",
      "FORF_METH": "!",
      "CREATE_AS_STC": "N",
      "USE_RDR": "N",
      "LST_MAINT_DT": "2011-03-11T17:09:39.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "RS_UTC_DT": "2011-03-11T22:09:39.0000000",
      "RS_STAT": 0
    }
   }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



