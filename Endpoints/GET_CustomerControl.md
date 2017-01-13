
# GET /CustomerControl

#### Description


- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/(endpoint)`

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
  "AR_CTL": {
    "KEY_ID": 1,
    "AGE_METH": "I",
    "NO_OF_AGE_PRDS": 4,
    "MAX_AGE_PRD_1": 30,
    "AGE_PRD_1_MSG_1": "Thank you for your business.",
    "AGE_PRD_1_MSG_2": "We appreciate prompt payments.",
    "MAX_AGE_PRD_2": 60,
    "AGE_PRD_2_MSG_1": "Account is 30 days past due.",
    "AGE_PRD_2_MSG_2": "Please pay promptly.",
    "MAX_AGE_PRD_3": 90,
    "AGE_PRD_3_MSG_1": "Account is 60 days past due.",
    "AGE_PRD_3_MSG_2": "Please pay promptly.",
    "MAX_AGE_PRD_4": 120,
    "AGE_PRD_4_MSG_1": "Account is 90 days past due.",
    "AGE_PRD_4_MSG_2": "Please pay promptly.",
    "ADJ_JRNL_PRT_METH": "P",
    "CR_JRNL_PRT_METH": "P",
    "NO_MAX_WRTOFF_AMT": "Y",
    "WRTOFF_ACCT_NO": "8030",
    "WRTOFF_METH": "!",
    "CR_AVAIL_INCL_ORDS": "Y",
    "LST_STMNT_BEG_DAT": "2001-02-15T00:00:00.0000000",
    "LST_STMNT_END_DAT": "2001-03-14T00:00:00.0000000",
    "CUST_PROF_ALPHA_1": "Y",
    "CUST_PROF_ALPHA_2": "Y",
    "CUST_PROF_ALPHA_3": "Y",
    "CUST_PROF_ALPHA_4": "Y",
    "CUST_PROF_ALPHA_5": "Y",
    "CUST_PROF_COD_1": "Y",
    "CUST_PROF_COD_2": "Y",
    "CUST_PROF_COD_3": "Y",
    "CUST_PROF_COD_4": "Y",
    "CUST_PROF_COD_5": "Y",
    "CUST_PROF_DAT_1": "Y",
    "CUST_PROF_DAT_2": "Y",
    "CUST_PROF_DAT_3": "Y",
    "CUST_PROF_DAT_4": "Y",
    "CUST_PROF_DAT_5": "Y",
    "CUST_PROF_NO_1": "Y",
    "CUST_PROF_NO_2": "Y",
    "CUST_PROF_NO_3": "Y",
    "CUST_PROF_NO_4": "Y",
    "CUST_PROF_NO_5": "Y",
    "ADJ_JRNL_DIST": "Y",
    "CR_JRNL_DIST": "Y",
    "LST_MAINT_DT": "2011-04-01T08:22:48.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "USE_SIMPLE_CUST_AOF": "N",
    "CR_AVAIL_INCL_LWYS": "N",
    "USE_LOY_PGMS": "Y",
    "PT_ADJ_JRNL_PRT_METH": "P",
    "FCH_JRNL_PRT_METH": "P",
    "FCH_JRNL_DIST": "Y",
    "ACCT_MGMT_NOTE_ID": "ACCOUNT",
    "SAV_STMNTS_TO_DISK": "N",
    "RS_UTC_DT": "2011-04-01T12:22:48.0000000",
    "EMAIL_STATEMENTS": "Y",
    "RS_STAT": 0
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



