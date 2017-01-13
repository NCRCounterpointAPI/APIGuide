
# GET /Customers/EC

#### Description


- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/Customers/EC`

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
  "AR_CUST": [
    {
      "CUST_NO": "100002",
      "NAM": "Kenneth Davis",
      "NAM_UPR": "KENNETH DAVIS",
      "FST_NAM": "Ken",
      "FST_NAM_UPR": "KEN",
      "LST_NAM": "Davis",
      "LST_NAM_UPR": "DAVIS",
      "SALUTATION": "Mr.",
      "CUST_TYP": "A",
      "ADRS_1": "18543 Salinger Way",
      "CITY": "Memphis",
      "STATE": "TN",
      "ZIP_COD": "38109",
      "PHONE_1": "321-455-9833",
      "PROMPT_NAM_ADRS": "S",
      "SLS_REP": "MGR",
      "CATEG_COD": "CASH",
      "SHIP_VIA_COD": "UPS GROUND",
      "SHIP_ZONE_COD": "UPS ZONE 1",
      "STR_ID": "MAIN",
      "STMNT_COD": "EOM",
      "TAX_COD": "MEMTN",
      "TERMS_COD": "NET30",
      "ALLOW_AR_CHRG": "Y",
      "ALLOW_TKTS": "Y",
      "NO_CR_LIM": "Y",
      "NO_MAX_CHK_AMT": "Y",
      "UNPSTD_BAL": 0,
      "BAL_METH": "O",
      "AR_ACCT_NO": "1210",
      "BAL": 70,
      "ORD_BAL": 0,
      "NO_OF_ORDS": 0,
      "USE_ORD_SHIP_TO": "S",
      "ALLOW_ORDS": "Y",
      "LST_AGE_FUTR_DOCS": "N",
      "LST_AGE_METH": "!",
      "LST_AGE_NO_CUTOFF": "N",
      "LST_AGE_NON_STD": "N",
      "LST_STMNT_METH": "!",
      "FST_SAL_DAT": "2016-04-25T00:00:00.0000000",
      "LST_SAL_DAT": "2016-04-25T00:00:00.0000000",
      "LST_SAL_AMT": 762.98,
      "LST_PMT_DAT": "2016-03-08T00:00:00.0000000",
      "LST_PMT_AMT": 10,
      "LST_MAINT_DT": "2012-04-26T12:55:20.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "LST_LCK_DT": "2016-03-08T09:18:47.7270000",
      "WRK_STMNT_ACTIV": "N",
      "LWY_BAL": 0,
      "NO_OF_LWYS": 0,
      "USE_LWY_SHIP_TO": "S",
      "ALLOW_LWYS": "Y",
      "IS_ECOMM_CUST": "Y",
      "DISC_PCT": 0,
      "ECOMM_NXT_PUB_UPDT": "Y",
      "ECOMM_NXT_PUB_FULL": "Y",
      "ECOMM_LST_PUB_TYP": "!",
      "ECOMM_CREATED_CUST": "N",
      "ECOMM_LST_IMP_TYP": "!",
      "PROMPT_FOR_CUSTOM_FLDS": "N",
      "LOY_PGM_COD": "LOYAL-1",
      "LOY_PTS_BAL": 0,
      "TOT_LOY_PTS_EARND": 1894,
      "TOT_LOY_PTS_RDM": 7894,
      "TOT_LOY_PTS_ADJ": 6000,
      "LST_LOY_EARN_TKT_DAT": "2016-04-25T00:00:00.0000000",
      "LST_LOY_EARN_TKT_TIM": "1899-12-30T09:58:16.0000000",
      "LST_LOY_PTS_EARN": 494,
      "LST_LOY_EARN_TKT_NO": "101421",
      "LST_LOY_RDM_TKT_DAT": "2016-04-25T00:00:00.0000000",
      "LST_LOY_RDM_TKT_TIM": "1899-12-30T10:33:43.0000000",
      "LST_LOY_PTS_RDM": 7894,
      "LST_LOY_RDM_TKT_NO": "101422",
      "LST_LOY_ADJ_DAT": "2012-03-16T00:00:00.0000000",
      "LST_LOY_PTS_ADJ": 6000,
      "LOY_CARD_NO": "321-455-9833",
      "FCH_COD": "2%",
      "REQ_PO_NO": "N",
      "RS_UTC_DT": "2016-07-14T18:57:05.2600000",
      "CUST_NAM_TYP": "B",
      "CUST_FST_LST_NAM": "Kenneth Davis",
      "LST_LOY_EARN_TKT_DT": "2016-04-25T09:58:16.0000000",
      "LST_LOY_RDM_TKT_DT": "2016-04-25T10:33:43.0000000",
      "EMAIL_STATEMENT": "N",
      "RS_STAT": 1,
      "INCLUDE_IN_MARKETING_MAILOUTS": "N",
      "MARKETING_MAILOUT_OPT_IN_DAT": "2012-03-16T00:00:00.0000000",
      "RPT_EMAIL": "1",
      "AR_CUST_NOTE": [],
      "AR_SHIP_ADRS": [],
      "AR_CUST_CARDS": []
    },
    {
      "CUST_NO": "100003",
      "NAM": "Dupey Instruction",
      "NAM_UPR": "DUPEY INSTRUCTION",
      "FST_NAM": "Mike",
      "FST_NAM_UPR": "MIKE",
      "LST_NAM": "Dupey",
      "LST_NAM_UPR": "DUPEY",
      "SALUTATION": "Mr.",
      "CUST_TYP": "A",
      "ADRS_1": "4873 Military Trail",
      "CITY": "West Palm Beach",
      "STATE": "FL",
      "ZIP_COD": "33406",
      "PHONE_1": "561-223-4395",
      "PROMPT_NAM_ADRS": "S",
      "SLS_REP": "MGR",
      "CATEG_COD": "BUSINESS",
      "STR_ID": "MAIN",
      "TERMS_COD": "210/NET30",
      "ALLOW_AR_CHRG": "Y",
      "ALLOW_TKTS": "Y",
      "NO_CR_LIM": "Y",
      "NO_MAX_CHK_AMT": "Y",
      "UNPSTD_BAL": 0,
      "BAL_METH": "O",
      "AR_ACCT_NO": "1210",
      "BAL": 352.86,
      "ORD_BAL": 638.95,
      "NO_OF_ORDS": 5,
      "USE_ORD_SHIP_TO": "S",
      "ALLOW_ORDS": "Y",
      "LST_AGE_FUTR_DOCS": "N",
      "LST_AGE_METH": "!",
      "LST_AGE_NO_CUTOFF": "N",
      "LST_AGE_NON_STD": "N",
      "LST_STMNT_METH": "!",
      "FST_SAL_DAT": "2012-03-20T00:00:00.0000000",
      "LST_SAL_DAT": "2016-04-25T00:00:00.0000000",
      "LST_SAL_AMT": 752.09,
      "LST_PMT_DAT": "2016-07-14T00:00:00.0000000",
      "LST_PMT_AMT": 10,
      "LST_MAINT_DT": "2012-03-16T14:59:46.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "WRK_STMNT_ACTIV": "N",
      "LWY_BAL": 0,
      "NO_OF_LWYS": 0,
      "USE_LWY_SHIP_TO": "S",
      "ALLOW_LWYS": "Y",
      "IS_ECOMM_CUST": "Y",
      "DISC_PCT": 0,
      "ECOMM_NXT_PUB_UPDT": "Y",
      "ECOMM_NXT_PUB_FULL": "Y",
      "ECOMM_LST_PUB_TYP": "!",
      "ECOMM_CREATED_CUST": "N",
      "ECOMM_LST_IMP_TYP": "!",
      "PROMPT_FOR_CUSTOM_FLDS": "N",
      "LOY_PTS_BAL": 0,
      "TOT_LOY_PTS_EARND": 0,
      "TOT_LOY_PTS_RDM": 0,
      "TOT_LOY_PTS_ADJ": 0,
      "REQ_PO_NO": "N",
      "RS_UTC_DT": "2016-07-14T18:57:05.9300000",
      "CUST_NAM_TYP": "B",
      "CUST_FST_LST_NAM": "Dupey Instruction",
      "EMAIL_STATEMENT": "N",
      "RS_STAT": 1,
      "INCLUDE_IN_MARKETING_MAILOUTS": "N",
      "MARKETING_MAILOUT_OPT_IN_DAT": "2012-03-16T00:00:00.0000000",
      "RPT_EMAIL": "1",
      "AR_CUST_NOTE": [],
      "AR_SHIP_ADRS": [],
      "AR_CUST_CARDS": []
    }
      ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



