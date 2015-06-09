
# GET /Workgroup/{WorkgroupID}

#### Description
Gets information about a workgroup

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Workgroup/1`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
WorkgroupID | path | string | true | The WRKGRP_ID of the workgroup to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The workgroup id provided does not exist in the SY_WRKGRP table.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `SY_WRKGRP` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested workgroup id was not present.

#### Sample Response Body

```
{
  "SY_WRKGRP": {
    "WRKGRP_ID": "1",
    "DESCR": "Main Store Workgroup",
    "DESCR_UPR": "MAIN STORE WORKGROUP",
    "THIS_LOC_ID": "MAIN",
    "THIS_STR_ID": "MAIN",
    "USR_DFLT_METH": "S",
    "NXT_CUST_NO": "100027",
    "NXT_CUST_NO_AUTO": "N",
    "NXT_ITEM_NO": "100001",
    "NXT_ITEM_NO_AUTO": "N",
    "NXT_VEND_NO": "100001",
    "NXT_VEND_NO_AUTO": "N",
    "NXT_BARCOD": "800003",
    "NXT_XFER_NO": "100043",
    "NXT_XFER_NO_AUTO": "N",
    "NXT_RECVR_NO": "100054",
    "NXT_RECVR_NO_AUTO": "N",
    "NXT_PO_NO": "100137",
    "NXT_PREQ_NO": "100077",
    "NXT_PREQ_NO_AUTO": "N",
    "NXT_EVENT_NO": "700330",
    "NXT_GFC_NO": "100077",
    "NXT_GFC_NO_AUTO": "N",
    "NXT_STC_NO": "100006",
    "NXT_STC_NO_AUTO": "N",
    "USE_PREQ_NO_AS_PO_NO": "N",
    "LST_MAINT_DT": "2013-03-22T13:24:15.2030000",
    "LST_MAINT_USR_ID": "MGR",
    "LST_LCK_DT": "2013-03-22T13:24:15.0570000",
    "LOC_GRP_ID": "1",
    "TMPLT_ITEM_NO": "TEMPLATE",
    "TMPLT_CUST_NO": "TEMPLATE",
    "NXT_RTV_NO": "100009",
    "NXT_RTV_NO_AUTO": "N",
    "ITEM_LKUP_TABLE": "VI_IM_ITEM_WITH_INV",
    "THIS_SITE_ID": 0,
    "RESTRICT_THIS_SITE_ID": "Y",
    "RS_UTC_DT": "2015-05-15T18:43:25.1000000",
    "NXT_AR_DOC_NO": "AR1-00005",
    "ITEM_LKUP_CHKS_VEND_ITEM_NO": "Y",
    "BTN_MENU_STYLE": "7",
    "BTN_MENU_SIZE": 80,
    "BTN_MENU_ROUND_CRNRS": "Y",
    "BTN_MENU_TXT_POS": "T",
    "BTN_MENU_FONT": "\\\"Arial\\\", 8, [Bold], [clWindowText]",
    "DFLT_ZOOM_LVL": "H",
    "RS_STAT": 1,
    "USE_AUTO_STA_LCK": "N",
    "AUTO_STA_LCK_MINS": 15
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



