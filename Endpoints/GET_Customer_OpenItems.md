
# GET /Customer/{CustNo}/OpenItems

#### Description
Retrieves AR_OPN_ITEM records for the given customer

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81//Customer/1000/OpenItems`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
CustNo | path | string | true | The CUST_NO of the customer to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.

#### Sample Response Body

```
 "AR_OPN_ITEM": [
    {
      "CUST_NO": "1000",
      "DOC_DAT": "2001-02-15T00:00:00.0000000",
      "DOC_NO": "100105",
      "DOC_TYP": "T",
      "AMT": 1138.59,
      "ENTD_AMT": 1138.59,
      "TOT_WRTOFF_AMT": 0,
      "DISC_TAKEN": 0,
      "TERMS_COD": "NET30",
      "DUE_DAT": "2001-03-17T00:00:00.0000000",
      "DISC_DAT": "2001-02-15T00:00:00.0000000",
      "DISC_PCT": 0,
      "SLS_REP": "MGR",
      "STR_ID": "MAIN",
      "SELF_APPLIED": "Y",
      "LST_MAINT_DT": "2016-03-23T11:16:29.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "WRK_STMNT_ACTIV": "N",
      "WRK_STMNT_BEG_BAL": 0,
      "WRK_STMNT_END_BAL": 0,
      "STA_ID": "1",
      "EVENT_NO": "12",
      "STMNT_DOC_TYP_ORDER": 1,
      "DOC_ID": 201346426533
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

