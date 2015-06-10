
# GET /Item/{ItemNo}

#### Description
Gets information about an item.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Item/ADM-SCD`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
ItemNo | path | string | true | The ITEM_NO of the item to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The item provided does not exist in the IM_ITEM table.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `IM_ITEM` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested item was not present.

#### Sample Response Body

```
{
  "IM_ITEM": {
    "ITEM_NO": "ADM-SCD",
    "DESCR": "Adams SC Driver, RH",
    "DESCR_UPR": "ADAMS SC DRIVER, RH",
    "LONG_DESCR": "Adams SC Driver, RH",
    "LONG_DESCR_UPR": "ADAMS SC DRIVER, RH",
    "SHORT_DESCR": "Adams SC Driver",
    "ADDL_DESCR_1": "Adams exclusive Spin Control Technology",
    "ADDL_DESCR_2": "Uses a proprietary stainless steel casting process",
    "ADDL_DESCR_3": "Keeps ball on target and produces greater distance",
    "ITEM_TYP": "I",
    "CATEG_COD": "GOLF",
    "SUBCAT_COD": "CLUBS",
    "ACCT_COD": "1",
    "ATTR_COD_1": "RIGHTHAND",
    "ATTR_COD_2": "STSTEEL",
    "TRK_METH": "N",
    "STAT": "A",
    "STAT_DAT": "2000-02-02T00:00:00.0000000",
    "IS_TXBL": "Y",
    "QTY_DECS": 0,
    "PRC_DECS": 2,
    "STK_UNIT": "EACH",
    "ITEM_VEND_NO": "ADAMS",
    "IS_WEIGHED": "N",
    "PREF_UNIT": "0",
    "PROMPT_FOR_PRC": "N",
    "PROMPT_FOR_COST": "N",
    "PROMPT_FOR_DESCR": "N",
    "WARR_UNIT_1": "D",
    "WARR_UNIT_2": "D",
    "SER_NO_REQ_FOR_SAL": "N",
    "GRID_ENT_1": 1,
    "GRID_ENT_2": 2,
    "GRID_ENT_3": 3,
    "PRC_1": 399.99,
    "BARCOD": "1",
    "IS_ECOMM_ITEM": "Y",
    "ECOMM_LST_PUB_STAT": "I",
    "ECOMM_TXBL_1": "N",
    "ECOMM_TXBL_2": "N",
    "ECOMM_TXBL_3": "N",
    "ECOMM_NEW": "N",
    "ECOMM_ON_SPECL": "C",
    "ECOMM_CHRG_FRT": "N",
    "LST_MAINT_DT": "2012-07-16T14:56:16.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "LST_LCK_DT": "2000-07-27T20:10:35.0000000",
    "DFLT_COST_OF_SLS_PCT": 0,
    "REG_PRC": 399.99,
    "LST_COST": 159.996,
    "LST_RECV_DAT": "2007-10-27T00:00:00.0000000",
    "IS_FOOD_STMP_ITEM": "N",
    "PROMPT_FOR_UNIT": "N",
    "PROMPT_FOR_CUSTOM_FLDS": "N",
    "MIX_MATCH_COD": "CLUBDEAL",
    "IS_ADM_TKT": "N",
    "RS_UTC_DT": "2012-07-16T18:56:16.5300000",
    "IS_BOM_PAR": "N",
    "IS_KIT_PAR": "N",
    "CATEG_SUBCAT": "GOLF/CLUBS",
    "DIM_COUNT": 0,
    "PREF_UNIT_DENOM": 1,
    "PREF_UNIT_NAM": "EACH",
    "PREF_UNIT_NUMER": 1,
    "PREF_UNIT_PRC_1": 399.99,
    "PREF_UNIT_REG_PRC": 399.99,
    "ITEM_IS_MISC": "N",
    "BARCOD_3_OF_9": "*1*",
    "IS_DISCNTBL": "Y",
    "ECOMM_DISC_ON_SAL": "Y",
    "ECOMM_ITEM_IS_DISCNTBL": "Y",
    "RS_STAT": 0,
    "IM_ITEM_NOTE": []
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Item object**

Element | Datatype | Description
------- | -------- | -----------



