
# GET /Customers

#### Description
Gets a list of customers

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:52000/Customers`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
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
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "Customers": [
    {
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
      "UNPSTD_BAL": -40,
      "BAL_METH": "O",
      "AR_ACCT_NO": "1210",
      "BAL": 1007,
      "ORD_BAL": 770.06,
      "NO_OF_ORDS": 2,
      "USE_ORD_SHIP_TO": "S",
      "ALLOW_ORDS": "Y",
      "LST_AGE_DAT": "2003-01-04T00:00:00.0000000",
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
      "LST_AGE_AS_OF_DAT": "2003-01-04T00:00:00.0000000",
      "LST_AGE_CUTOFF_DAT": "2003-01-04T00:00:00.0000000",
      "LST_AGE_MAX_PRD_1": 30,
      "LST_AGE_MAX_PRD_2": 60,
      "LST_AGE_MAX_PRD_3": 90,
      "LST_AGE_MAX_PRD_4": 120,
      "LST_AGE_NO_OF_PRDS": 4,
      "LST_AGE_NO_CUTOFF": "Y",
      "LST_AGE_PAST_CUTOFF": 0,
      "LST_AGE_NON_STD": "N",
      "LST_STMNT_DAT": "2001-02-15T00:00:00.0000000",
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
      "LST_STMNT_BEG_DAT": "2001-02-15T00:00:00.0000000",
      "LST_STMNT_END_DAT": "2001-03-14T00:00:00.0000000",
      "LST_STMNT_MAX_PRD_1": 30,
      "LST_STMNT_MAX_PRD_2": 60,
      "LST_STMNT_MAX_PRD_3": 90,
      "LST_STMNT_MAX_PRD_4": 120,
      "LST_STMNT_NO_OF_PRDS": 4,
      "FST_SAL_DAT": "2001-02-15T00:00:00.0000000",
      "LST_SAL_DAT": "2016-07-14T00:00:00.0000000",
      "LST_SAL_AMT": 0.99,
      "LST_PMT_DAT": "2016-07-14T00:00:00.0000000",
      "LST_PMT_AMT": 10,
      "LST_MAINT_DT": "2016-10-17T09:53:04.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "LST_LCK_DT": "2016-03-09T15:42:54.0170000",
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
      "LOY_PTS_BAL": 19701,
      "TOT_LOY_PTS_EARND": 9862,
      "TOT_LOY_PTS_RDM": 162,
      "TOT_LOY_PTS_ADJ": 10001,
      "LST_LOY_EARN_TKT_DAT": "2016-10-17T00:00:00.0000000",
      "LST_LOY_EARN_TKT_TIM": "1899-12-30T09:55:18.0000000",
      "LST_LOY_PTS_EARN": 315,
      "LST_LOY_EARN_TKT_NO": "102370",
      "LST_LOY_RDM_TKT_DAT": "2016-07-13T00:00:00.0000000",
      "LST_LOY_RDM_TKT_TIM": "1899-12-30T10:41:00.0000000",
      "LST_LOY_PTS_RDM": 162,
      "LST_LOY_RDM_TKT_NO": "102249",
      "LST_LOY_ADJ_DAT": "2016-07-13T00:00:00.0000000",
      "LST_LOY_PTS_ADJ": 1,
      "LOY_CARD_NO": "321-455-1836",
      "FCH_COD": "2%",
      "REQ_PO_NO": "N",
      "RS_UTC_DT": "2016-10-17T13:55:17.8700000",
      "CUST_NAM_TYP": "B",
      "CUST_FST_LST_NAM": "Bill Baker",
      "LST_LOY_EARN_TKT_DT": "2016-10-17T09:55:18.0000000",
      "LST_LOY_RDM_TKT_DT": "2016-07-13T10:41:00.0000000",
      "EMAIL_STATEMENT": "N",
      "RS_STAT": 1,
      "INCLUDE_IN_MARKETING_MAILOUTS": "N",
      "RPT_EMAIL": "1",
      "AR_CUST_NOTE": [],
      "AR_SHIP_ADRS": [],
      "AR_CUST_CARDS": []
    },
    {
      "CUST_NO": "100001",
      "NAM": "Jenna Watkins",
      "NAM_UPR": "JENNA WATKINS",
      "FST_NAM": "Jenna",
      "FST_NAM_UPR": "JENNA",
      "LST_NAM": "Watkins",
      "LST_NAM_UPR": "WATKINS",
      "CUST_TYP": "C",
      "ADRS_1": "873 Houston Branch Road",
      "CITY": "Memphis",
      "STATE": "TN",
      "ZIP_COD": "38109",
      "PHONE_1": "321-455-3668",
      "PROMPT_NAM_ADRS": "S",
      "SLS_REP": "MGR",
      "CATEG_COD": "CASH",
      "STR_ID": "MAIN",
      "ALLOW_AR_CHRG": "Y",
      "ALLOW_TKTS": "Y",
      "NO_CR_LIM": "Y",
      "NO_MAX_CHK_AMT": "Y",
      "UNPSTD_BAL": 0,
      "BAL_METH": "O",
      "BAL": 0,
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
      "LST_SAL_AMT": 1144.47,
      "LST_MAINT_DT": "2012-03-16T14:53:29.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "WRK_STMNT_ACTIV": "N",
      "LWY_BAL": 0,
      "NO_OF_LWYS": 0,
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
      "LOY_PTS_BAL": 9050,
      "TOT_LOY_PTS_EARND": 1050,
      "TOT_LOY_PTS_RDM": 0,
      "TOT_LOY_PTS_ADJ": 8000,
      "LST_LOY_EARN_TKT_DAT": "2016-04-25T00:00:00.0000000",
      "LST_LOY_EARN_TKT_TIM": "1899-12-30T09:46:03.0000000",
      "LST_LOY_PTS_EARN": 1050,
      "LST_LOY_EARN_TKT_NO": "200022",
      "LST_LOY_ADJ_DAT": "2012-03-16T00:00:00.0000000",
      "LST_LOY_PTS_ADJ": 8000,
      "LOY_CARD_NO": "321-455-3668",
      "REQ_PO_NO": "N",
      "RS_UTC_DT": "2016-07-14T18:57:05.1270000",
      "CUST_NAM_TYP": "P",
      "CUST_FST_LST_NAM": "Watkins, Jenna",
      "LST_LOY_EARN_TKT_DT": "2016-04-25T09:46:03.0000000",
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



