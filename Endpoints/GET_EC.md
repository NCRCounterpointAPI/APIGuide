
# GET /EC

#### Description
Gets eCommerce control information for the current company

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/EC`

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
  "EC_CTL": {
    "KEY_ID": 1,
    "USE_ECOMM": "Y",
    "DFLT_PUB_ID": "ALL",
    "ITEM_UNIT_METH": "P",
    "STR_ID": "101",
    "ITEM_PRC_CUST_NO": "CASH",
    "ITEM_NAM_METH": "D",
    "ITEM_IMG_METH": "J",
    "ITEM_SELL_PRC_METH": "1",
    "ITEM_SELL_PRC_ADJ": "!",
    "ITEM_SELL_PRC_ADJ_PCT": 0,
    "ITEM_LIST_PRC_METH": "1",
    "ITEM_LIST_PRC_ADJ": "!",
    "ITEM_LIST_PRC_ADJ_PCT": 0,
    "ITEM_QTY_METH": "1",
    "ITEM_TXBL_1_METH": "Y",
    "ITEM_TXBL_2_METH": "N",
    "ITEM_TXBL_3_METH": "N",
    "ITEM_REF_METH": "1",
    "CATEG_IMG_METH": "J",
    "ORD_STA_ID": "101-1",
    "ORD_DRW_ID": "1",
    "ORD_CUST_NO": "CASH",
    "ORD_PRC_METH": "I",
    "ORD_TAX_METH": "I",
    "ORD_SLS_REP_METH": "C",
    "ORD_IMP_PRT_METH": "P",
    "ORD_SHIP_DOM_STD": "UPS GROUND",
    "ORD_SHIP_DOM_OVN": "UPS RED",
    "ORD_SHIP_UPS_NXT_DAY": "UPS RED",
    "ORD_SHIP_UPS_2ND_DAY": "UPS BLUE",
    "ORD_SHIP_DOM_2ND_DAY": "UPS BLUE",
    "ORD_PAY_COD_VISA": "VISA",
    "ORD_PAY_COD_MC": "MASTERCARD",
    "ORD_PAY_COD_AMEX": "AMEX",
    "ORD_PAY_COD_DISC": "DISCOVER",
    "LST_MAINT_DT": "2016-08-09T13:14:43.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "NXT_PUB_FILE_NO": 1,
    "TMPLT_CUST_NO": "TEMPLATE",
    "AFFIL_METH": "!!",
    "INIT_PWD_METH": "R",
    "CUST_NAM_SRC": "N",
    "EXEMPT_TAX_COD_FILT_TMPLT": "Checked=0\rIndentLev=0\rDataField=TAX_COD\rTemplate=is (exactly)\rValue=\rValue1=\rValue2=\rOperation=or\rChecked=0\rIndentLev=0\rDataField=TAX_COD\rTemplate=is (exactly)\rValue=\rValue1=\rValue2=\rOperation=or\rChecked=0\rIndentLev=0\rDataField=TAX_COD\rTemplate=is (exactly)\rValue=\rValue1=\rValue2=\rOperation=or\rChecked=0\rIndentLev=0\rDataField=TAX_COD\rTemplate=is (exactly)\rValue=\rValue1=\rValue2=\rOperation=and\r",
    "EXEMPT_TAX_COD_FILT_TEXT": "*** All ***",
    "ORD_CUST_NO_METH": "A",
    "NXT_CUST_NO": "OL-100001",
    "TMPLT_CUST_NO_METH": "!",
    "ORD_BASE_TAX_COD": "MEMTN",
    "ORD_TAX_COD_BY_SHIP_TO": "N",
    "CUST_TAX_COD_BY_SHIP_TO": "N",
    "ORD_MISC_CHRG_NO": "1",
    "CUST_IMP_PRT_METH": "P",
    "ORD_INSUFF_QTY_METH": "O",
    "ITEM_VEND_SRC": "_VEND_NAM",
    "ITEM_USR_DEF_ALPHA_1_SRC": "!",
    "ITEM_USR_DEF_ALPHA_2_SRC": "!",
    "ITEM_USR_DEF_ALPHA_3_SRC": "!",
    "ITEM_USR_DEF_NO_1_SRC": "!",
    "ITEM_USR_DEF_NO_2_SRC": "!",
    "ITEM_USR_DEF_NO_3_SRC": "!",
    "ORD_USR_DEF_1_DEST": "!",
    "ORD_USR_DEF_2_DEST": "!",
    "ORD_USR_DEF_3_DEST": "!",
    "ORD_USR_DEF_4_DEST": "!",
    "ORD_USR_DEF_5_DEST": "!",
    "USE_ADT": "N",
    "ADT_FTP_SITE": "ftp://adt.cpostores.com",
    "ADT_PUB_TIMES_UPDTD": 0,
    "ORD_REDUCE_INIT_DEP_FOR_BO": "N",
    "ORD_INCL_ALL_MISC_CHRG_ON_INIT_DEP": "N",
    "ITEM_SEND_EXT_DATA": "N"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



