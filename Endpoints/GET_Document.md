
# GET /Document/{DocId}

#### Description
Gets information about the specified document.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/Document/{DocId}`

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
- `SUCCESS`: The request was successful and the document information is present in the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "PS_DOC_HDR": {
    "DOC_ID": 701315942121,
    "STR_ID": "20",
    "STA_ID": "20-1",
    "TKT_NO": "20-100238",
    "DOC_TYP": "T",
    "SAL_LINS": 1,
    "ORD_LINS": 0,
    "SAL_LIN_TOT": 349.99,
    "GFC_LINS": 0,
    "BO_LINS": 0,
    "SO_LINS": 0,
    "DRW_ID": "20-1",
    "DRW_SESSION_ID": 100000000000616,
    "CUST_NO": "CASH",
    "RET_LINS": 0,
    "RET_LIN_TOT": 0,
    "TAX_COD": "MEMTN",
    "TKT_TYP": "T",
    "USR_ID": "MGR",
    "SLS_REP": "MGR",
    "STK_LOC_ID": "MAIN",
    "PRC_LOC_ID": "MAIN",
    "SVC_LINS": 0,
    "DOC_GUID": "da0f35296a804ceabffe7e6f52b22a9e",
    "REQ_REPRICE": "N",
    "RS_UTC_DT": "2016-04-25T02:38:45.0000000",
    "IS_DOC_COMMITTED": "N",
    "FOOD_STMP_AMT": 0,
    "FOOD_STMP_LINS": 0,
    "FOOD_STMP_TAX_AMT": 0,
    "TIMES_PRTD": 0,
    "TKT_DT": "2016-04-24T22:38:45.0000000",
    "IS_REL_TKT": "N",
    "FOOD_STMP_NORM_TAX_AMT": 0,
    "NORM_TAX_COD": "MEMTN",
    "HAS_ENTD_LINS": "N",
    "HAS_PCKD_LINS": "N",
    "HAS_PCKVRFD_LINS": "N",
    "HAS_INVCD_LINS": "N",
    "HAS_RLSD_LINS": "N",
    "TO_REL_LINS": 1,
    "TO_LEAVE_LINS": 0,
    "LST_MAINT_DT": "2016-04-24T22:38:45.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "IS_OFFLINE": false,
    "RS_STAT": 1,
    "DS_LINS": 0,
    "PS_DOC_LIN": [
      {
        "DOC_ID": 701315942121,
        "LIN_SEQ_NO": 1,
        "STR_ID": "20",
        "STA_ID": "20-1",
        "TKT_NO": "20-100238",
        "LIN_TYP": "S",
        "PRC": 349.99,
        "ITEM_NO": "ADM-TL9",
        "UNIT_RETL_VAL": 349.99,
        "CALC_PRC": 349.99,
        "EXT_COST": 196.45,
        "STK_LOC_ID": "MAIN",
        "REG_PRC": 349.99,
        "PRC_LOC_ID": "MAIN",
        "DESCR": "Adams Tight Lies 9 Wood",
        "CATEG_COD": "GOLF",
        "SUBCAT_COD": "CLUBS",
        "ITEM_VEND_NO": "ADAMS",
        "QTY_SOLD": 1,
        "QTY_NUMER": 1,
        "QTY_DENOM": 1,
        "QTY_UNIT": "EACH",
        "SELL_UNIT": "0",
        "EXT_PRC": 349.99,
        "IS_TXBL": "Y",
        "SLS_REP": "MGR",
        "ITEM_TYP": "I",
        "PRC_1": 349.99,
        "QTY_DECS": 0,
        "PRC_DECS": 2,
        "BARCOD": "6",
        "IS_SINGLE_CELL": "N",
        "NORM_IS_TXBL": "Y",
        "TRK_METH": "N",
        "ORIG_QTY": 1,
        "QTY_SHIPPED": 0,
        "IS_FOOD_STMP_ELIG": "N",
        "UNIT_WEIGHT": 0,
        "UNIT_CUBE": 0,
        "LIN_GUID": "17791542a41f47dcb53121b19b6af7b8",
        "DIM_1_UPR": "*",
        "DIM_2_UPR": "*",
        "DIM_3_UPR": "*",
        "UNIT_COST": 196.45,
        "QTY_RET": 0,
        "IS_VAL_RET": "N",
        "GROSS_EXT_PRC": 349.99,
        "DISP_EXT_PRC": 349.99,
        "IS_KIT_PAR": "N",
        "HAS_PRC_OVRD": "N",
        "PRESUMED_COST": 196.45,
        "COST_OF_SLS_PCT": 0,
        "MIX_MATCH_COD": "CLUBDEAL",
        "MIX_MATCH_CONTRIB": 1,
        "MIX_MATCH_PRC_BASED_ON": "Q",
        "USR_ENTD_PRC": "N",
        "GROSS_DISP_EXT_PRC": 349.99,
        "IS_DISCNTBL": "Y",
        "CALC_EXT_PRC": 349.99,
        "QTY_ENTD": 0,
        "QTY_PCKD": 0,
        "QTY_PCKVRFD": 0,
        "QTY_INVCD": 0,
        "QTY_TO_FILL": 0,
        "QTY_TO_REL": 1,
        "QTY_TO_LEAVE": 0,
        "IS_MAN_ENTD_WGHT": "N",
        "IS_WEIGHED": "N",
        "TAX_AMT_ALLOC": 31.5,
        "NORM_TAX_AMT_ALLOC": 31.5,
        "PS_DOC_LIN_CELL": [],
        "PS_DOC_LIN_SER": [],
        "PS_DOC_LIN_PRICE": [
          {
            "DOC_ID": 701315942121,
            "LIN_SEQ_NO": 1,
            "PRC_JUST_STR": "Price-1",
            "PRC_GRP_TYP": "!",
            "PRC_RUL_SEQ_NO": -1,
            "PRC_BRK_DESCR": "I",
            "PRC_SEQ_NO": 1,
            "QTY_PRCD": 1,
            "UNIT_PRC": 349.99,
            "DIM_1_UPR": "*",
            "DIM_2_UPR": "*",
            "DIM_3_UPR": "*"
          }
        ],
        "PS_DOC_LIN_PROMPT": []
      }
    ],
    "PS_DOC_PMT": [
      {
        "DOC_ID": 701315942121,
        "PMT_SEQ_NO": 1,
        "PAY_COD_TYP": "B",
        "AMT": 381.49,
        "STR_ID": "20",
        "FINAL_PMT": "N",
        "STA_ID": "20-1",
        "CARD_IS_NEW": "N",
        "TKT_NO": "20-100238",
        "SECURE_ECOMM_TRX": "N",
        "PMT_LIN_TYP": "T",
        "PAY_COD": "CASH",
        "PAY_DAT": "2016-04-24T00:00:00.0000000",
        "DEP_LIN_COPIED_TO_REL_DOC": "N",
        "HOME_CURNCY_AMT": 381.49,
        "EXCH_LOSS": 0,
        "SIG_IMG": "",
        "SWIPED": "N",
        "SIG_IMG_VECTOR": "",
        "DESCR": "Cash",
        "EDC_AUTH_FLG": "O",
        "CURNCY_COD": "HOME",
        "EXCH_RATE_NUMER": 1,
        "EXCH_RATE_DENOM": 1,
        "ROUND_GAIN_LOSS": 0,
        "HOME_CURNCY_ROUND_GAIN_LOSS": 0,
        "PS_DOC_PMT_APPLY": [
          {
            "DOC_ID": 701315942121,
            "PMT_SEQ_NO": 1,
            "APPL_TYP": "S",
            "AMT": 381.49,
            "HOME_CURNCY_AMT": 381.49,
            "EXCH_LOSS": 0
          }
        ],
        "PS_DOC_PMT_PROMPT": []
      }
    ],
    "PS_DOC_NOTE": [],
    "PS_DOC_PKG_TRK_NO": [],
    "PS_DOC_HDR_TOT": [
      {
        "DOC_ID": 701315942121,
        "TOT_TYP": "S",
        "INITIAL_MIN_DUE": 0,
        "HAS_TAX_OVRD": "!",
        "TAX_AMT_SHIPPED": 0,
        "LINS": 1,
        "TOT_GFC_AMT": 0,
        "TOT_SVC_AMT": 0,
        "SUB_TOT": 349.99,
        "TAX_OVRD_LINS": 0,
        "TOT_EXT_COST": 196.45,
        "TOT_MISC": 0,
        "TAX_AMT": 31.5,
        "NORM_TAX_AMT": 31.5,
        "TOT_TND": 381.49,
        "TOT_CHNG": 0,
        "TOT_WEIGHT": 0,
        "TOT_CUBE": 0,
        "TOT": 381.49,
        "AMT_DUE": 0,
        "TOT_HDR_DISC": 0,
        "TOT_LIN_DISC": 0,
        "TOT_HDR_DISCNTBL_AMT": 349.99
      }
    ],
    "PS_DOC_TAX": [
      {
        "DOC_ID": 701315942121,
        "AUTH_COD": "MEMPHIS",
        "RUL_COD": "TAX",
        "TAX_DOC_PART": "S",
        "LIN_AMT": 349.99,
        "TXBL_LIN_AMT": 349.99,
        "TXBL_MISC_CHG_AMT_1": 0,
        "TXBL_MISC_CHG_AMT_2": 0,
        "TXBL_MISC_CHG_AMT_3": 0,
        "TXBL_MISC_CHG_AMT_4": 0,
        "TXBL_MISC_CHG_AMT_5": 0,
        "TXBL_GFC_AMT": 0,
        "TXBL_SVC_AMT": 0,
        "TXBL_TAX_AMT": 0,
        "TXBL_QTY": 1,
        "TAX_AMT": 7,
        "NORM_TAX_AMT": 7,
        "TAX_AMT_EXACT": 7,
        "NORM_TAX_AMT_EXACT": 7,
        "TOT_TXBL_AMT": 349.99
      },
      {
        "DOC_ID": 701315942121,
        "AUTH_COD": "SHELBY",
        "RUL_COD": "TAX",
        "TAX_DOC_PART": "S",
        "LIN_AMT": 349.99,
        "TXBL_LIN_AMT": 349.99,
        "TXBL_MISC_CHG_AMT_1": 0,
        "TXBL_MISC_CHG_AMT_2": 0,
        "TXBL_MISC_CHG_AMT_3": 0,
        "TXBL_MISC_CHG_AMT_4": 0,
        "TXBL_MISC_CHG_AMT_5": 0,
        "TXBL_GFC_AMT": 0,
        "TXBL_SVC_AMT": 0,
        "TXBL_TAX_AMT": 0,
        "TXBL_QTY": 1,
        "TAX_AMT": 10.5,
        "NORM_TAX_AMT": 10.5,
        "TAX_AMT_EXACT": 10.5,
        "NORM_TAX_AMT_EXACT": 10.5,
        "TOT_TXBL_AMT": 349.99
      },
      {
        "DOC_ID": 701315942121,
        "AUTH_COD": "TN",
        "RUL_COD": "TAX",
        "TAX_DOC_PART": "S",
        "LIN_AMT": 349.99,
        "TXBL_LIN_AMT": 349.99,
        "TXBL_MISC_CHG_AMT_1": 0,
        "TXBL_MISC_CHG_AMT_2": 0,
        "TXBL_MISC_CHG_AMT_3": 0,
        "TXBL_MISC_CHG_AMT_4": 0,
        "TXBL_MISC_CHG_AMT_5": 0,
        "TXBL_GFC_AMT": 0,
        "TXBL_SVC_AMT": 0,
        "TXBL_TAX_AMT": 0,
        "TXBL_QTY": 1,
        "TAX_AMT": 14,
        "NORM_TAX_AMT": 14,
        "TAX_AMT_EXACT": 14,
        "NORM_TAX_AMT_EXACT": 14,
        "TOT_TXBL_AMT": 349.99
      }
    ],
    "PS_DOC_HDR_MISC_CHRG": [
      {
        "DOC_ID": 701315942121,
        "TOT_TYP": "S",
        "MISC_CHRG_NO": 1,
        "MISC_TYP": "A",
        "MISC_AMT": 0,
        "MISC_PCT": 0,
        "MISC_AMT_SHIPPED": 0,
        "MISC_TAX_AMT_ALLOC": 0,
        "MISC_NORM_TAX_AMT_ALLOC": 0
      }
    ],
    "PS_DOC_HDR_ORIG_DOC": [],
    "PS_DOC_AUDIT_LOG": [
      {
        "DOC_ID": 701315942121,
        "LOG_SEQ_NO": 1,
        "DOC_TYP": "T",
        "DOC_GUID": "da0f35296a804ceabffe7e6f52b22a9e",
        "CURR_DT": "2016-04-24T22:38:44.0000000",
        "CURR_STR_ID": "20",
        "CURR_STA_ID": "20-1",
        "CURR_DRW_ID": "20-1",
        "CURR_USR_ID": "MGR",
        "CURR_WKSTN_NAM": "WUSMJ185111-T75",
        "CURR_SERV_NAM": "WUSMJ185111-T75",
        "CURR_DB_NAM": "QATestGolf",
        "ACTIV": "N",
        "LOG_ENTRY": "Entered a new ticket",
        "PS_DOC_AUDIT_LOG_TOT": [
          {
            "DOC_ID": 701315942121,
            "LOG_SEQ_NO": 1,
            "TOT_TYP": "S",
            "TOT_GFC_AMT": 0,
            "LINS": 1,
            "SUB_TOT": 349.99,
            "TOT_MISC": 0,
            "NORM_TAX_AMT": 31.5,
            "TAX_AMT": 31.5,
            "TOT_EXT_COST": 196.45,
            "TOT_TND": 381.49,
            "TOT_CHNG": 0,
            "AMT_DUE": 0,
            "TOT_SVC_AMT": 0,
            "DEP_NET_CHANGE": 0,
            "TOT": 381.49
          }
        ]
      }
    ],
    "PS_DOC_GFC": []
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



