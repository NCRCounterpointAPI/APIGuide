
# GET /Store/{StoreID}/Station/{StationID}

#### Description
Gets information about a station.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Store/MAIN/Station/1`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
StoreID | path | string | true | The STR_ID of the store at which the station exists.
StationID | path | string | true | The STA_ID of the station to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The station does not exist at the given store.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `PS_STA` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested station does not exist.

#### Sample Response Body

```
{
  "PS_STA": {
    "STR_ID": "MAIN",
    "STA_ID": "1",
    "DESCR": "Station 1",
    "DESCR_UPR": "STATION 1",
    "LST_MAINT_DT": "2012-04-26T13:09:15.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "USE_OE": "N",
    "STA_NO": 1,
    "RS_UTC_DT": "2012-04-26T17:09:15.0000000",
    "RS_STAT": 0,
    "PS_STA_CFG_PS": {
      "STR_ID": "MAIN",
      "STA_ID": "1",
      "USE_DFLT_CUST": "Y",
      "DFLT_LIN_MOD": "S",
      "BEG_TKT_AT": "L",
      "BEG_LIN_AT": "I",
      "DFLT_ENT_MOD": "N",
      "DFLT_TND_PAY_COD": "CASH",
      "DFLT_CHNG_PAY_COD": "CASH",
      "DFLT_RFND_PAY_COD": "CASH",
      "TOUCH_SCRN_COD": "COMBO",
      "NXT_TKT_NO_AUTO": "N",
      "NXT_HOLD_NO_AUTO": "N",
      "NXT_QUOT_NO_AUTO": "N",
      "NXT_ORD_NO_AUTO": "N",
      "FRM_TYP": "B",
      "USE_ALL_FRM_GRPS": "Y",
      "SHOW_ITEM_IMG": "Y",
      "SHOW_CUST_IMG": "Y",
      "USE_CONSOL_LINS": "Y",
      "SIG_CAP_AFTER_PRT": "N",
      "OFFLINE_NXT_TKT_NO": "M-100000",
      "OFFLINE_NXT_HOLD_NO": "M-500000",
      "OFFLINE_NXT_QUOT_NO": "M-600000",
      "OFFLINE_NXT_ORD_NO": "M-700000",
      "OFFLINE_NXT_TKT_NO_AUTO": "Y",
      "OFFLINE_NXT_HOLD_NO_AUTO": "Y",
      "OFFLINE_NXT_QUOT_NO_AUTO": "Y",
      "OFFLINE_NXT_ORD_NO_AUTO": "Y",
      "OFFLINE_NXT_GFC_NO": "M-200000",
      "OFFLINE_NXT_STC_NO": "M-400000",
      "OFFLINE_NXT_GFC_NO_AUTO": "Y",
      "OFFLINE_NXT_STC_NO_AUTO": "Y",
      "OFFLINE_NXT_CUST_NO": "M-100000",
      "OFFLINE_NXT_CUST_NO_AUTO": "Y",
      "NXT_LWY_NO_AUTO": "N",
      "OFFLINE_NXT_LWY_NO": "M-800000",
      "OFFLINE_NXT_LWY_NO_AUTO": "Y",
      "SHOW_RDM_LOY_PTS_MSG": "N",
      "USE_TND_PAY_COD_FOR_CHNG": "N",
      "LST_MAINT_DT": "2012-04-26T13:09:15.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "RS_UTC_DT": "2012-04-26T17:09:15.0000000",
      "RS_STAT": 0
    }
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**PS_STA object**

Element | Datatype | Description
------- | -------- | -----------



