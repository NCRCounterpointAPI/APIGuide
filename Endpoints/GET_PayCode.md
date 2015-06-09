
# GET /PayCode/{Paycode}

#### Description
Gets information about a paycode

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Paycode/CASH`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
Paycode | path | string | true | The PAY_COD of the paycode to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The paycode provided does not exist in the SY_PAY_COD table.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `SY_WRKGRP` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested workgroup id was not present.

#### Sample Response Body

```
{
  "SY_PAY_COD": {
    "PAY_COD": "CASH",
    "PAY_TYP": "B",
    "DESCR": "Cash",
    "DESCR_UPR": "CASH",
    "BTN_LBL": "Ca&sh",
    "BTN_IMAGE_FIL": "Paycode-Cash-LargeButton.bmp",
    "OPN_DRW": "Y",
    "PAY_COD_ACCT_NO": "1010",
    "PAY_COD_METH": "!",
    "USE_RDR": "N",
    "BANK_ACCT_COD": "FIRST",
    "PROMPT_1_REQ": "N",
    "PROMPT_2_REQ": "N",
    "PROMPT_3_REQ": "N",
    "NO_MAX_CHNG_AMT": "Y",
    "VAL_FOR_AR": "Y",
    "DFLT_TND_AMT": "N",
    "MIN_TND_AMT": 0,
    "NO_MAX_TND_AMT": "Y",
    "NO_MAX_RFND_AMT": "Y",
    "NO_MAX_OVTND": "Y",
    "USE_CARD_MOD10": "N",
    "TRANSIT_NO_FLG": "R",
    "ACCT_NO_FLG": "R",
    "CHK_NO_FLG": "R",
    "DRIV_LIC_FLG": "R",
    "DRIV_LIC_MICR": "R",
    "DRIV_LIC_STATE_FLG": "R",
    "DRIV_LIC_STATE_MICR": "R",
    "BIRTH_DAT_FLG": "R",
    "BIRTH_DAT_MICR": "R",
    "EDC_AUTH_FLG": "O",
    "LST_MAINT_DT": "2002-05-24T16:14:23.0000000",
    "LST_MAINT_USR_ID": "Z",
    "DIST_OVR_SHORT": "N",
    "OVR_SHORT_METH": "!",
    "USE_SIG_CAP_TND": "N",
    "USE_SIG_CAP_RFND": "N",
    "CURNCY_COD": "HOME",
    "ALLOW_FOR_ORDS": "Y",
    "ALLOW_FOR_LWYS": "Y",
    "DFLT_DOC_TND_AMT": "N",
    "DFLT_DOC_FINAL_PMT": "N",
    "PROMPT_FOR_CNT_AMT": "Y",
    "PROMPT_FOR_ACTIV_AMT": "Y",
    "IS_FOREIGN": "N",
    "PROMPT_FOR_CUSTOM_FLDS": "N",
    "PRT_DECLINE_RCPT": "N",
    "ALLOW_TND_BELOW_CURNCY_MIN": "Y",
    "ALLOW_CHNG_BELOW_CURNCY_MIN": "Y",
    "DIST_OFF_FAILURE": "N",
    "OFF_FAILURE_METH": "!"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Paycode object**

Element | Datatype | Description
------- | -------- | -----------



