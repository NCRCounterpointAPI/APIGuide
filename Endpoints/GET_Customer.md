# GET /Customer/{CustNo}

#### Description
The endpoint gets information about the specified customer

Requires API Key: Yes
Requires System Administrator: No

#### Sample
https://localhost:81/Customer/100010

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
CustNo | path | string | true | The CUST_NO of the customer to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>404 Not Found</code>** The CUST_NO provided was not a valid CUST_NO in the AR_CUST table.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.

#### Sample Response Body
```
{
  "AR_CUST": {
    "CUST_NO": "1000",
    "NAM": "Bill Baker",
    "NAM_UPR": "BILL BAKER",
    "FST_NAM": "Bill",
    "FST_NAM_UPR": "BILL",
    "LST_NAM": "Baker",
    "LST_NAM_UPR": "BAKER",
    "SALUTATION": "Mr.",
    "CUST_TYP": "A",
    "ADRS_1": "1426 Millstream Parkway",
    "CITY": "Memphis",
    "STATE": "TN",
    "ZIP_COD": "38120",
    "PHONE_1": "321-455-1836",
    "PROMPT_NAM_ADRS": "S",
    "SLS_REP": "MGR",
    "CATEG_COD": "MEMBERS",
    "SHIP_VIA_COD": "UPS GROUND",
    "SHIP_ZONE_COD": "UPS ZONE 1",
    "STR_ID": "MAIN",
    "STMNT_COD": "EOM",
    "TAX_COD": "MEMTN",
    "TERMS_COD": "NET30",
    "ALLOW_AR_CHRG": "Y",
    "ALLOW_TKTS": "Y",
    "NO_CR_LIM": "Y",
    "CR_RATE": "AAA",
    "NO_MAX_CHK_AMT": "Y",
    "UNPSTD_BAL": 0,
    "BAL_METH": "O",
    "AR_ACCT_NO": "1210",
    "BAL": 238.25,
    "ORD_BAL": 770.06,
    "NO_OF_ORDS": 2,
    "USE_ORD_SHIP_TO": "S",
    "ALLOW_ORDS": "Y",
    "LST_AGE_DAT": "/Date(1041656400000-0000)/",
    "LST_AGE_BAL": 759.09,
    "LST_AGE_BAL_1": 0,
    "LST_AGE_BAL_2": 0,
    "LST_AGE_BAL_3": 0,
    "LST_AGE_BAL_4": 759.09,
    "LST_AGE_BAL_5": 0,
    "LST_AGE_BAL_2_5": 759.09,
    "LST_AGE_BAL_3_5": 759.09,
    "LST_AGE_BAL_4_5": 759.09,
    "LST_AGE_BAL_OPN": 0,
    "LST_AGE_FUTR_DOCS": "N",
    "LST_AGE_METH": "I",
    "LST_AGE_AS_OF_DAT": "/Date(1041656400000-0000)/",
    "LST_AGE_CUTOFF_DAT": "/Date(1041656400000-0000)/",
    "LST_AGE_MAX_PRD_1": 30,
    "LST_AGE_MAX_PRD_2": 60,
    "LST_AGE_MAX_PRD_3": 90,
    "LST_AGE_MAX_PRD_4": 120,
    "LST_AGE_NO_OF_PRDS": 4,
    "LST_AGE_NO_CUTOFF": "Y",
    "LST_AGE_PAST_CUTOFF": 0,
    "LST_AGE_NON_STD": "N",
    "LST_STMNT_DAT": "/Date(982213200000-0000)/",
    "LST_STMNT_BAL": 936.59,
    "LST_STMNT_BAL_1": 936.59,
    "LST_STMNT_BAL_2": 0,
    "LST_STMNT_BAL_3": 0,
    "LST_STMNT_BAL_4": 0,
    "LST_STMNT_BAL_5": 0,
    "LST_STMNT_BAL_2_5": 0,
    "LST_STMNT_BAL_3_5": 0,
    "LST_STMNT_BAL_4_5": 0,
    "LST_STMNT_BAL_OPN": 0,
    "LST_STMNT_METH": "I",
    "LST_STMNT_BEG_DAT": "/Date(982213200000-0000)/",
    "LST_STMNT_END_DAT": "/Date(984546000000-0000)/",
    "LST_STMNT_MAX_PRD_1": 30,
    "LST_STMNT_MAX_PRD_2": 60,
    "LST_STMNT_MAX_PRD_3": 90,
    "LST_STMNT_MAX_PRD_4": 120,
    "LST_STMNT_NO_OF_PRDS": 4,
    "FST_SAL_DAT": "/Date(982213200000-0000)/",
    "LST_SAL_DAT": "/Date(1342497600000-0000)/",
    "LST_SAL_AMT": 2589.49,
    "LST_PMT_DAT": "/Date(1193457600000-0000)/",
    "LST_PMT_AMT": 100,
    "LST_MAINT_DT": "/Date(1335459310000-0000)/",
    "LST_MAINT_USR_ID": "MGR",
    "LST_LCK_DT": "/Date(1217418986013-0000)/",
    "WRK_STMNT_ACTIV": "N",
    "LWY_BAL": 2359.36,
    "NO_OF_LWYS": 2,
    "USE_LWY_SHIP_TO": "S",
    "ALLOW_LWYS": "Y",
    "IS_ECOMM_CUST": "N",
    "DISC_PCT": 0,
    "ECOMM_NXT_PUB_UPDT": "N",
    "ECOMM_NXT_PUB_FULL": "Y",
    "ECOMM_LST_PUB_TYP": "!",
    "ECOMM_CREATED_CUST": "N",
    "ECOMM_LST_IMP_TYP": "!",
    "PROMPT_FOR_CUSTOM_FLDS": "N",
    "LOY_PGM_COD": "LOYAL-1",
    "LOY_PTS_BAL": 12456,
    "TOT_LOY_PTS_EARND": 2456,
    "TOT_LOY_PTS_RDM": 0,
    "TOT_LOY_PTS_ADJ": 10000,
    "LST_LOY_EARN_TKT_DAT": "/Date(1342497600000-0000)/",
    "LST_LOY_EARN_TKT_TIM": "/Date(-2209094023000-0000)/",
    "LST_LOY_PTS_EARN": 2376,
    "LST_LOY_EARN_TKT_NO": "70027-01",
    "LST_LOY_PTS_RDM": 0,
    "LST_LOY_ADJ_DAT": "/Date(1142744400000-0000)/",
    "LST_LOY_PTS_ADJ": 10000,
    "LOY_CARD_NO": "321-455-1836",
    "FCH_COD": "2%",
    "REQ_PO_NO": "N",
    "RS_UTC_DT": "/Date(1363979865540-0000)/",
    "CUST_NAM_TYP": "B",
    "CUST_FST_LST_NAM": "Bill Baker",
    "LST_LOY_EARN_TKT_DT": "/Date(1342547177000-0000)/",
    "EMAIL_STATEMENT": "N",
    "RS_STAT": 1,
    "INCLUDE_IN_MARKETING_MAILOUTS": "N",
    "RPT_EMAIL": "1",
    "AR_CUST_NOTE": [
      {
        "CUST_NO": "1000",
        "NOTE_ID": "ACCOUNT",
        "NOTE_DAT": "/Date(1193831807000-0000)/",
        "USR_ID": "MGR",
        "NOTE": "{\\rtf1\\ansi\\deff0{\\fonttbl{\\f0\\fnil\\fcharset0 Arial;}}\r\n\\viewkind4\\uc1\\pard\\lang1033\\fs16 This is an Auto-display note used for Account Management. This note is also one that can be printed using a Preview function and Crystal will do word-wrap on the notes column.\\par\r\n}\r\n",
        "NOTE_TXT": "This is an Auto-display note used for Account Management. This note is also one that can be printed using a Preview \r\nfunction and Crystal will do word-wrap on the notes column.\r\r\n"
      },
      {
        "CUST_NO": "1000",
        "NOTE_ID": "AUTO",
        "NOTE_DAT": "/Date(1300110432000-0000)/",
        "USR_ID": "MGR",
        "NOTE": "{\\rtf1\\ansi\\deff0{\\fonttbl{\\f0\\fnil\\fcharset0 Arial;}}\r\n\\viewkind4\\uc1\\pard\\lang1033\\fs16 Have Bill verify his current phone number.  (we could not reach him last week)\\par\r\n\\par\r\nAH\\par\r\n}\r\n",
        "NOTE_TXT": "Have Bill verify his current phone number.  (we could not reach him last week)\r\r\n\r\r\nAH\r\r\n"
      }
    ],
    "AR_SHIP_ADRS": [
      {
        "CUST_NO": "1000",
        "SHIP_ADRS_ID": "(DEFAULT)",
        "NAM": "Baker International",
        "NAM_UPR": "BAKER INTERNATIONAL",
        "ADRS_1": "17821 West Jefferson Ave",
        "CITY": "Memphis",
        "STATE": "TN",
        "ZIP_COD": "38121"
      }
    ],
    "AR_CUST_CARDS": []
  },
  "IsSuccessful": true,
  "ResultCode": 0
}
```

