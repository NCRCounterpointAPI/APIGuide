
# GET /Company

#### Description
Gets information about a Company.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Company`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : vpmk0tqApzFu5EesAMQgstBtQLEwK1ySwMZ4zwiC`
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


#### Sample Response Body

```
{
  "SY_COMP": {
    "KEY_ID": 1,
    "NAM": "Quality Golf Academy",
    "ADRS_1": "645 Tournament Lane",
    "CITY": "Memphis",
    "STATE": "TN",
    "ZIP_COD": "38138",
    "CNTRY": "USA",
    "PHONE_1": "800-I-LUV-GOLF",
    "CONTCT_1": "Pro Golfer",
    "EMAIL_ADRS_1": "progolfer@progolfer.com",
    "CURR_CALNDR_ID": "2014",
    "CENTURY_OFFSET": 80,
    "USE_PWDS": "Y",
    "MIN_PWD_LEN": 7,
    "PWD_CHNG_DAYS": 60,
    "MAIN_ACCT_START": 1,
    "MAIN_ACCT_LEN": 4,
    "PFT_CTR_START": 5,
    "PFT_CTR_LEN": 0,
    "AR_CASH_DETL_DIST": "Y",
    "AR_CASH_DIST_REF": "1",
    "AR_ADJ_DETL_DIST": "Y",
    "AR_ADJ_DIST_REF": "1",
    "PS_SLS_DETL_DIST": "Y",
    "PS_SLS_DIST_REF": "S",
    "PS_PMT_DETL_DIST": "Y",
    "PS_PMT_DIST_REF": "S",
    "PS_MISC_DETL_DIST": "Y",
    "PS_MISC_DIST_REF": "S",
    "PS_TAX_DETL_DIST": "Y",
    "PS_TAX_DIST_REF": "S",
    "IM_RECV_DETL_DIST": "Y",
    "IM_RECV_DIST_REF": "1",
    "IM_SLS_DETL_DIST": "Y",
    "IM_SLS_DIST_REF": "S",
    "IM_ADJ_DETL_DIST": "Y",
    "IM_ADJ_DIST_REF": "A",
    "IM_CNT_DETL_DIST": "Y",
    "IM_CNT_DIST_REF": "I",
    "IM_XFER_DETL_DIST": "Y",
    "IM_XFER_DIST_REF": "1",
    "PS_GFC_DETL_DIST": "Y",
    "PS_GFC_DIST_REF": "1",
    "USE_GFC": "Y",
    "NO_GFC_EXP": "Y",
    "ROUND_GFC_EXP_TO_EOM": "Y",
    "ALLOW_OTHR_STR_GFCS": "N",
    "CLSD_GFC_JRNL_METH": "P",
    "MIN_GFC_RDM_PCT": 50,
    "PS_STC_DETL_DIST": "Y",
    "PS_STC_DIST_REF": "1",
    "USE_STC": "Y",
    "NO_STC_EXP": "Y",
    "ROUND_STC_EXP_TO_EOM": "N",
    "ALLOW_OTHR_STR_STCS": "Y",
    "CLSD_STC_JRNL_METH": "P",
    "STC_LIAB_ACCT_NO": "2080",
    "STC_LIAB_METH": "!",
    "STC_RDM_ACCT_NO": "2080",
    "STC_RDM_METH": "!",
    "STC_FORF_ACCT_NO": "8510",
    "STC_FORF_METH": "!",
    "MAX_LKUP_ROWS": 200,
    "USE_FAST_OPN": "Y",
    "CLSD_GFC_JRNL_DIST": "N",
    "CLSD_STC_JRNL_DIST": "N",
    "LST_MAINT_DT": "2014-02-25T15:07:50.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "IM_RTV_DETL_DIST": "Y",
    "IM_RTV_DIST_REF": "1",
    "PS_PAY_IN_OUT_DETL_DIST": "Y",
    "PS_PAY_IN_OUT_DIST_REF": "T",
    "PS_PAY_ON_ACCT_DETL_DIST": "Y",
    "PS_PAY_ON_ACCT_DIST_REF": "C",
    "MAX_TBL_VIEW_ROWS": 400,
    "PO_ADJ_DETL_DIST": "Y",
    "PO_ADJ_DIST_REF": "1",
    "REQ_COMPLEX_PWD": "Y",
    "PREV_UNIQUE_PWDS": 4,
    "LOGIN_ATTEMPTS": 6,
    "USE_TIMCRDS": "Y",
    "STALE_CLCK_IN_HRS": 12,
    "ALLOW_RE_CLCK_IN": "N",
    "RE_CLCK_IN_MINS": 1,
    "ALLOW_ORPHAN_CLCK_OUT": "N",
    "TIMCRD_DFLT_USR_ID": "N",
    "AR_FCH_DETL_DIST": "Y",
    "AR_FCH_DIST_REF": "1",
    "PS_SVC_DETL_DIST": "Y",
    "PS_SVC_DIST_REF": "1",
    "USE_SVC": "N",
    "SVC_PROCESSOR": "G",
    "SVC_MIN_ACTIV_AMT": 30,
    "SVC_MIN_RECHRG_AMT": 30,
    "SVC_MAX_RFND_AMT": 20,
    "SVC_MAX_CASH_BACK_AMT": 20,
    "NO_SVC_MAX_CASH_BACK_AMT": "N",
    "REQ_SVC_PIN": "N",
    "USE_WINDOWS_AUTH": "N",
    "OE_SLS_DETL_DIST": "Y",
    "OE_SLS_DIST_REF": "S",
    "OE_PMT_DETL_DIST": "Y",
    "OE_PMT_DIST_REF": "S",
    "OE_MISC_DETL_DIST": "Y",
    "OE_MISC_DIST_REF": "S",
    "OE_TAX_DETL_DIST": "Y",
    "OE_TAX_DIST_REF": "S",
    "OE_GFC_DETL_DIST": "Y",
    "OE_GFC_DIST_REF": "1",
    "OE_STC_DETL_DIST": "Y",
    "OE_STC_DIST_REF": "1",
    "OE_SVC_DETL_DIST": "Y",
    "OE_SVC_DIST_REF": "1",
    "COPY_USR_BAT": "Y",
    "PROMPT_FOR_USR_BAT": "Y",
    "COPY_USR_DRW": "Y",
    "PROMPT_FOR_USR_DRW": "Y",
    "COPY_USR_PREF": "Y",
    "PROMPT_FOR_USR_PREF": "Y",
    "RS_UTC_DT": "2014-02-25T20:07:54.3030000",
    "IM_BOM_ASSEM_DETL_DIST": "Y",
    "IM_BOM_ASSEM_DIST_REF": "1",
    "USE_GFT_RGSTRY": "Y",
    "ALLOW_OTHR_STR_GFT_RGSTRY": "Y",
    "GFT_RGSTRY_VAL_MONS": 0,
    "MAIL_REFRSH_SECS": 30,
    "MAIL_AUTO_PURGE_DAYS": 30,
    "RESTRICT_TO_REGISTERED_WORKSTATIONS": "N",
    "USE_EXT_EDC": "Y",
    "RPT_EMAIL_BODY": "See attached report",
    "RS_STAT": 1,
    "USE_DROPSHIP": "Y",
    "SECURE_PAYMENT_DATA_MODE": "N",
    "DB_CTL": {
      "KEY_ID": 1,
      "DB_VER": "29.35",
      "DB_TYP": "MSSQL2012",
      "FULLTXT_SRCH": "N",
      "SHARED_DIR": "C:\\Program Files (x86)\\Radiant Systems\\CounterPoint\\CPSQL.85\\Toplevel\\",
      "AUTO_UPR": "Y",
      "DB_KIND": "C"
    }
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



