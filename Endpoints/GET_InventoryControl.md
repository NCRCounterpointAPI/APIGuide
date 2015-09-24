
# GET /InventoryControl

#### Description
Gets Inventory Control information for a Company.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`GET https://localhost:81/InventoryControl`

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
  "IM_CTL": {
    "KEY_ID": 1,
    "BS_INV_METH": "!",
    "COST_METH": "A",
    "USE_MULTI_LOC_PRCS": "Y",
    "PRC_ROUND_METH": "N",
    "PRC_LVLS": 6,
    "USE_ATTR_1": "Y",
    "USE_ATTR_2": "Y",
    "USE_ATTR_3": "Y",
    "USE_ATTR_4": "Y",
    "USE_ATTR_5": "Y",
    "USE_ATTR_6": "Y",
    "ITEM_BARCOD_ID": "ITEM",
    "USE_SER_COST": "N",
    "CNT_POST_COST_FLG": "C",
    "PHYS_CNT_JRNL_METH": "P",
    "PHYS_CNT_WRKSHT_METH": "P",
    "IM_ADJ_JRNL_PRT_METH": "P",
    "USE_QXFER_MISC_CHRG": "N",
    "QXFER_MISC_METH": "!",
    "QXFER_JRNL_PRT_METH": "P",
    "ITEM_PROF_ALPHA_1": "Y",
    "ITEM_PROF_ALPHA_2": "Y",
    "ITEM_PROF_ALPHA_3": "Y",
    "ITEM_PROF_ALPHA_4": "Y",
    "ITEM_PROF_ALPHA_5": "Y",
    "ITEM_PROF_COD_1": "Y",
    "ITEM_PROF_COD_2": "Y",
    "ITEM_PROF_COD_3": "Y",
    "ITEM_PROF_COD_4": "Y",
    "ITEM_PROF_COD_5": "Y",
    "ITEM_PROF_DAT_1": "Y",
    "ITEM_PROF_DAT_2": "Y",
    "ITEM_PROF_DAT_3": "Y",
    "ITEM_PROF_DAT_4": "Y",
    "ITEM_PROF_DAT_5": "Y",
    "ITEM_PROF_NO_1": "Y",
    "ITEM_PROF_NO_2": "Y",
    "ITEM_PROF_NO_3": "Y",
    "ITEM_PROF_NO_4": "Y",
    "ITEM_PROF_NO_5": "Y",
    "IM_ADJ_JRNL_DIST": "N",
    "PHYS_CNT_JRNL_DIST": "N",
    "QXFER_JRNL_DIST": "N",
    "LST_MAINT_DT": "2012-03-21T10:02:26.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "XFER_CLR_METH": "!",
    "USE_XFER_OUT_MISC_CHRG": "N",
    "XFER_OUT_MISC_METH": "!",
    "USE_XFER_IN_MISC_CHRG": "N",
    "XFER_IN_MISC_METH": "!",
    "DFLT_XFER_RECON_METH": "!",
    "XFER_PRMPT_FOR_LIN_INFO": "N",
    "XFER_OUT_JRNL_PRT_METH": "P",
    "XFER_FRM_PRT_METH": "P",
    "XFER_IN_JRNL_PRT_METH": "P",
    "XFER_IN_FRM_PRT_METH": "P",
    "XFER_RECON_JRNL_PRT_METH": "P",
    "XFER_RECON_FRM_PRT_METH": "P",
    "XFER_CONSOL_METH": "!",
    "XFER_IN_ALLOW_ADD_LINS": "N",
    "XFER_OUT_JRNL_DIST": "N",
    "XFER_IN_JRNL_DIST": "N",
    "XFER_RECON_JRNL_DIST": "N",
    "AUTO_ADD_INV_METH": "!",
    "SHOW_INV_SETUP_DLG": "N",
    "SHOW_GRID_SETUP_DLG": "N",
    "SHOW_INV_FRM": "Y",
    "SHOW_GRID_DEF_FRM": "Y",
    "GEN_CELL_BARCOD": "N",
    "GEN_CELL_BARCOD_PREFIX": "!",
    "USE_SIMPLE_ITEM_AOF": "N",
    "DFLT_ITEM_LBL_JOB": "ITEM-INV",
    "XFER_IN_TAGS_METH": "C",
    "XFER_OUT_TAGS_METH": "C",
    "QXFER_TAGS_METH": "C",
    "DFLT_XFER_IN_LBL_JOB": "ITEM-TRANI",
    "DFLT_XFER_OUT_LBL_JOB": "ITEM-TRANO",
    "DFLT_QXFER_LBL_JOB": "ITEM-QTRAN",
    "USE_CELL_PRCS": "Y",
    "USE_LOC_CELL_PRCS": "Y",
    "RS_UTC_DT": "2013-03-25T15:28:41.0700000",
    "QASSEM_JRNL_METH": "P",
    "QASSEM_JRNL_DIST": "N",
    "DFLT_QASSEM_LBL_JOB": "ITEM-QASMB",
    "QASSEM_TAGS_METH": "C",
    "COPY_ITEM_COPY_INV": "Y",
    "COPY_ITEM_PROMPT_INV": "Y",
    "COPY_ITEM_COPY_PRC": "Y",
    "COPY_ITEM_PROMPT_PRC": "Y",
    "COPY_ITEM_COPY_ITEM_NOTE": "Y",
    "COPY_ITEM_PROMPT_ITEM_NOTE": "Y",
    "COPY_ITEM_COPY_SUBST_ITEM": "Y",
    "COPY_ITEM_COPY_VEND_ITEM": "Y",
    "COPY_ITEM_PROMPT_VEND_ITEM": "Y",
    "COPY_ITEM_COPY_EC_ITEM_CATEG": "Y",
    "COPY_ITEM_PROMPT_EC_ITEM_CATEG": "Y",
    "COPY_ITEM_COPY_BOM": "Y",
    "COPY_ITEM_PROMPT_BOM": "Y",
    "COPY_ITEM_COPY_SALES_KIT": "Y",
    "COPY_ITEM_PROMPT_SALES_KIT": "Y",
    "MRGN_LESS_THAN_MIN_MRGN_COLOR": 7760116,
    "MRGN_BTW_MIN_AND_TRGT_MRGN_COLOR": 12648447,
    "MRGN_MEET_EXCEED_TRGT_MRGN_COLOR": 12648384,
    "IM_CNT_TRX_FRZ_QTY_METH": "O",
    "MRGN_COST_TO_USE": "I",
    "DFLT_PRICE_SHEET_LBL_JOB": "ITEM-PRICE",
    "PRICE_SHEET_TAGS_METH": "C",
    "RS_STAT": 1,
    "DROPSHIP_INV_METH": "!"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**InventoryControl object**

Element | Datatype | Description
------- | -------- | -----------




```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



