
# GET /Items

#### Description
Gets information about all items in the company

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Items`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
- CategCod | Query | The IM_CATEG_COD of the items to retrieve | Optional
- SubcatCod | Query | The IM_SUBCAT_COD of the items to retrieve | Optional

##### Paging
The paging parameters are optional for the request, but both are required together for the call to apply the paging logic.
- Page | Query | The data page number to retrieve | Optional
- Rows | Query | The number of rows to return per page | Optional

##### Filters
The StartDate and EndDate fields can be used in any combination - none, either one, or both.  StartDate must be earlier than EndDate.  See this page for [Supported Date Formats](../Basics/DateFormats.md).
- StartDate | Query | The start date filter for the RS_UTC_DT field | Optional
- EndDate | Query | The end date filter for the RS_UTC_DT field | Optional

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and an array of item information is present under the `Items` section of the response body.

#### Sample Response Body

```
{
  "Items": [
    {
      "ITEM_NO": "18HOLES",
      "DESCR": "Green fee - 18 holes",
      "DESCR_UPR": "GREEN FEE - 18 HOLES",
      "LONG_DESCR": "Green fee - 18 holes",
      "LONG_DESCR_UPR": "GREEN FEE - 18 HOLES",
      "SHORT_DESCR": "Green fee - 18",
      "ADDL_DESCR_1": "Green fee includes rain guarantee",
      "ADDL_DESCR_2": "If 16 holes of round cannot be finished before",
      "ADDL_DESCR_3": "rain, issue a raincheck for free 18 Holes",
      "ITEM_TYP": "N",
      "CATEG_COD": "GOLF",
      "SUBCAT_COD": "FEES",
      "ACCT_COD": "1",
      "TRK_METH": "N",
      "STAT": "A",
      "IS_TXBL": "Y",
      "QTY_DECS": 0,
      "PRC_DECS": 2,
      "STK_UNIT": "EACH",
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
      "PRC_1": 36,
      "BARCOD": "18",
      "IS_ECOMM_ITEM": "N",
      "ECOMM_LST_PUB_STAT": "I",
      "ECOMM_TXBL_1": "N",
      "ECOMM_TXBL_2": "N",
      "ECOMM_TXBL_3": "N",
      "ECOMM_NEW": "N",
      "ECOMM_ON_SPECL": "C",
      "ECOMM_CHRG_FRT": "N",
      "LST_MAINT_DT": "2005-09-18T14:45:46.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "LST_LCK_DT": "2001-11-12T15:02:52.0000000",
      "DFLT_COST_OF_SLS_PCT": 0,
      "REG_PRC": 36,
      "LST_COST": 0,
      "IS_FOOD_STMP_ITEM": "N",
      "PROMPT_FOR_UNIT": "N",
      "PROMPT_FOR_CUSTOM_FLDS": "N",
      "IS_ADM_TKT": "N",
      "IS_BOM_PAR": "N",
      "IS_KIT_PAR": "N",
      "CATEG_SUBCAT": "GOLF/FEES",
      "DIM_COUNT": 0,
      "PREF_UNIT_DENOM": 1,
      "PREF_UNIT_NAM": "EACH",
      "PREF_UNIT_NUMER": 1,
      "PREF_UNIT_PRC_1": 36,
      "PREF_UNIT_REG_PRC": 36,
      "ITEM_IS_MISC": "Y",
      "BARCOD_3_OF_9": "*18*",
      "IS_DISCNTBL": "Y",
      "ECOMM_DISC_ON_SAL": "Y",
      "ECOMM_ITEM_IS_DISCNTBL": "Y",
      "RS_STAT": 0,
      "IM_ITEM_NOTE": []
    },
    {
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
      "IM_ITEM_NOTE": [],
      "EC_ITEM_DESCR": {
        "ITEM_NO": "ADM-SCD",
        "HTML_DESCR": "<B>Adams</B> exclusive <B>Spin Control Technology</B>.\r\nUses a proprietary stainless steel casting process.\r\nKeeps ball on target and produces greater distance.\r\n\r\n",
        "LST_MAINT_DT": "2002-09-24T19:11:45.0000000",
        "LST_MAINT_USR_ID": "Z"
      }
    },
    {
      "ITEM_NO": "WEDGE",
      "DESCR": "ATV CC Wedge",
      "DESCR_UPR": "ATV CC WEDGE",
      "SHORT_DESCR": "ATV CC Wedge",
      "ITEM_TYP": "I",
      "CATEG_COD": "GOLF",
      "SUBCAT_COD": "ACCES",
      "ACCT_COD": "1",
      "TRK_METH": "N",
      "STAT": "A",
      "IS_TXBL": "Y",
      "QTY_DECS": 0,
      "PRC_DECS": 2,
      "STK_UNIT": "EACH",
      "ITEM_VEND_NO": "TAYLORMADE",
      "IS_WEIGHED": "N",
      "PREF_UNIT": "0",
      "PROMPT_FOR_PRC": "N",
      "PROMPT_FOR_COST": "N",
      "PROMPT_FOR_DESCR": "N",
      "WARR_UNIT_1": "D",
      "WARR_UNIT_2": "D",
      "SER_NO_REQ_FOR_SAL": "N",
      "PRC_1": 119,
      "IS_ECOMM_ITEM": "N",
      "ECOMM_LST_PUB_STAT": "!",
      "ECOMM_TXBL_1": "N",
      "ECOMM_TXBL_2": "N",
      "ECOMM_TXBL_3": "N",
      "ECOMM_NEW": "N",
      "ECOMM_ON_SPECL": "N",
      "ECOMM_CHRG_FRT": "Y",
      "LST_MAINT_DT": "2012-10-04T10:42:02.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "LST_COST": 0,
      "IS_FOOD_STMP_ITEM": "N",
      "PROMPT_FOR_UNIT": "N",
      "PROMPT_FOR_CUSTOM_FLDS": "N",
      "IS_ADM_TKT": "N",
      "RS_UTC_DT": "2012-10-04T14:42:02.4330000",
      "IS_BOM_PAR": "N",
      "IS_KIT_PAR": "N",
      "CATEG_SUBCAT": "GOLF/ACCES",
      "DIM_COUNT": 0,
      "PREF_UNIT_DENOM": 1,
      "PREF_UNIT_NAM": "EACH",
      "PREF_UNIT_NUMER": 1,
      "PREF_UNIT_PRC_1": 119,
      "ITEM_IS_MISC": "N",
      "IS_DISCNTBL": "Y",
      "ECOMM_DISC_ON_SAL": "Y",
      "ECOMM_ITEM_IS_DISCNTBL": "Y",
      "RS_STAT": 0,
      "IM_ITEM_NOTE": []
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Item object**

Element | Datatype | Description
------- | -------- | -----------

