# POST /Customer

#### Description
Adds a new customer to the database

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`POST https://localhost:81/Customer`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : vpmk0tqApzFu5EesAMQgstBtQAEwK1ySwMZ4zwiC`
- `Accept : application/json`
- `Content-Type : application/json`

**Request Body**
```
{
  "AR_CUST": {
    "NAM": "Superman",
    "FST_NAM": "Clark",
    "LST_NAM": "Kent",
    "STR_ID": "100",
    "AR_CUST_NOTE": [
      {
        "Note_ID": "ADDED_85",
        "NOTE_TXT": "Be careful, Clark Kent is Superman."
      }
    ],
    "AR_SHIP_ADRS": [
      {
        "SHIP_ADRS_ID": "ADDRESS_1",
        "NAM": "HOME",
        "SHIP_NAM_TYP": "B"
      },
      {
        "SHIP_ADRS_ID": "ADDRESS_2",
        "NAM": "WORK",
        "SHIP_NAM_TYP": "B"
      }
    ]
  }
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
Workgroup | body | string | false | The WRKGRP_ID of the workgroup settings used to determine the template customer and next CUST_NO. If not provided, the default workgroup of the logged in user is used. All explicitly provided values will override workgroup driven values.
AR_CUST | body | string | true | A JSON structure containing the customer data to add.
**NOTE:** Whenever possible, the template customer is used to determine defaults for fields that aren't provided explicitly. The template customer is obtained from the record of the provided workgroup (WRKGRP_ID). If a WKRGRP_ID isn't provided, the default workgroup for the logged in user is used.

AR_CUST | Required | Field Description
------- | -------- | -----------------
CUST_NO | | The CUST_NO for the customer. If not provided, the CUST_NO will be determined by the provided settings in the WRKGRP_ID. if that is not provided, the workgroup settings from the user will be used.
NAM | | The full name of the customer. If not provided, NAM will be automatically filled in as `"FST_NAM" + " " + "LST_NAME"`
FST_NAM | * | The first name of the customer.
LST_NAM | * | The last name of the customer.
SALUTATION | | The salutation for the customer.
CUST_TYP | | Defaults to "C" if not provided explicitly or copied from the template customer.
ADRS_1 | |
ADRS_2 | |
ADRS_3 | |
CITY | |
STATE | |
ZIP_COD | |
CNTRY | |
PHONE_1 | |
PHONE_2 | |
FAX_1 | |
FAX_2 | |
CONTCT_1 | |
CONTCT_2 | |
EMAIL_ADRS_1 | |
EMAIL_ADRS_2 | |
URL_1 | |
URL_2 | |
PROMPT_NAM_ADRS | |
SLS_REP | |
CATEG_COD | |
SHIP_VIA_COD | |
SHIP_ZONE_COD | |
STR_ID | |
STMNT_COD | |
TAX_COD | |
TERMS_COD | |
COMMNT | |
TAX_EXEMPT_NO | |
TAX_EXEMPT_DAT | |
ALLOW_AR_CHRG | |
ALLOW_TKTS | |
NO_CR_LIM | |
CR_LIM | |
CR_RATE | |
NO_MAX_CHK_AMT | |
MAX_CHK_AMT | |
CR_CARD_PAY_COD_1 | |
CR_CARD_NO_1 | |
CR_CARD_EXP_DAT_1 | |
CR_CARD_NAM_1 | |
UNPSTD_BAL | |
BAL_METH | |
AR_ACCT_NO | |
USE_ORD_SHIP_TO | |
ALLOW_ORDS | |
LST_AGE_DAT | |
LST_AGE_BAL | |
LST_AGE_BAL_1 | |
LST_AGE_BAL_2 | |
LST_AGE_BAL_3 | |
LST_AGE_BAL_4 | |
LST_AGE_BAL_5 | |
LST_AGE_BAL_2_5 | |
LST_AGE_BAL_3_5 | |
LST_AGE_BAL_4_5 | |
LST_AGE_BAL_OPN | |
LST_AGE_FUTR_DOCS | |
LST_AGE_METH | |
LST_AGE_AS_OF_DAT | |
LST_AGE_CUTOFF_DAT | |
LST_AGE_MAX_PRD_1 | |
LST_AGE_MAX_PRD_2 | |
LST_AGE_MAX_PRD_3 | |
LST_AGE_MAX_PRD_4 | |
LST_AGE_NO_OF_PRDS | |
LST_AGE_EVENT_NO | |
LST_AGE_NO_CUTOFF | |
LST_AGE_PAST_CUTOFF | |
LST_AGE_NON_STD | |
LST_STMNT_DAT | |
LST_STMNT_BAL | |
LST_STMNT_BAL_1 | |
LST_STMNT_BAL_2 | |
LST_STMNT_BAL_3 | |
LST_STMNT_BAL_4 | |
LST_STMNT_BAL_5 | |
LST_STMNT_BAL_2_5 | |
LST_STMNT_BAL_3_5 | |
LST_STMNT_BAL_4_5 | |
LST_STMNT_BAL_OPN | |
LST_STMNT_METH | |
LST_STMNT_BEG_DAT | |
LST_STMNT_END_DAT | |
LST_STMNT_MAX_PRD_1 | |
LST_STMNT_MAX_PRD_2 | |
LST_STMNT_MAX_PRD_3 | |
LST_STMNT_MAX_PRD_4 | |
LST_STMNT_NO_OF_PRDS | |
LST_STMNT_PAST_CTOFF | |
FST_SAL_DAT | |
LST_SAL_DAT | |
LST_SAL_AMT | |
LST_PMT_DAT | |
LST_PMT_AMT | |
PROF_ALPHA_1 | |
PROF_ALPHA_2 | |
PROF_ALPHA_3 | |
PROF_ALPHA_4 | |
PROF_ALPHA_5 | |
PROF_COD_1 | |
PROF_COD_2 | |
PROF_COD_3 | |
PROF_COD_4 | |
PROF_COD_5 | |
PROF_DAT_1 | |
PROF_DAT_2 | |
PROF_DAT_3 | |
PROF_DAT_4 | |
PROF_DAT_5 | |
PROF_NO_1 | |
PROF_NO_2 | |
PROF_NO_3 | |
PROF_NO_4 | |
PROF_NO_5 | |
LST_MAINT_DT | |
LST_MAINT_USR_ID | |
LST_LCK_DT | |
WRK_STMNT_ACTIV | |
USE_LWY_SHIP_TO | |
ALLOW_LWYS | |
IS_ECOMM_CUST | |
ECOMM_CUST_NO | |
ECOMM_AFFIL_COD | |
DISC_PCT | |
ECOMM_INIT_PWD | |
ECOMM_NXT_PUB_UPDT | |
ECOMM_NXT_PUB_FULL | |
ECOMM_LST_PUB_DT | |
ECOMM_LST_PUB_TYP | |
ECOMM_LST_IMP_DT | |
ECOMM_CREATED_CUST | |
ECOMM_LST_ORD_NO | |
ECOMM_LST_ORD_DT | |
ECOMM_LST_IMP_TYP | |
ECOMM_LST_IMP_EVENT_NO | |
PROMPT_FOR_CUSTOM_FLDS | |
LOY_PGM_COD | |
LOY_PTS_BAL | |
TOT_LOY_PTS_EARND | |
TOT_LOY_PTS_RDM | |
TOT_LOY_PTS_ADJ | |
LST_LOY_EARN_TKT_DAT | |
LST_LOY_EARN_TKT_TIM | |
LST_LOY_PTS_EARN | |
LST_LOY_EARN_TKT_NO | |
LST_LOY_RDM_TKT_DAT | |
LST_LOY_RDM_TKT_TIM | |
LST_LOY_PTS_RDM | |
LST_LOY_RDM_TKT_NO | |
LST_LOY_ADJ_DAT | |
LST_LOY_PTS_ADJ | |
LST_LOY_ADJ_DOC_NO | |
LOY_CARD_NO | |
FCH_COD | |
LST_FCH_DAT | |
LST_FCH_AMT | |
LST_FCH_PAST_DUE_AMT | |
LST_FCH_DOC_NO | |
REQ_PO_NO | |
RS_UTC_DT | |
CUST_NAM_TYP | |
CUST_FST_LST_NAM | |
LST_LOY_EARN_TKT_DT | |
LST_LOY_RDM_TKT_DT | |
PS_HDR_CUST_FLD_FRM_ID | |
EMAIL_STATEMENT | |
INCLUDE_IN_MARKETING_MAILOUTS | |
MARKETING_MAILOUT_OPT_IN_DAT | |
RPT_EMAIL | |
MBL_PHONE_1 | |
MBL_PHONE_2 | |
List[AR_CUST_NOTE_POST] AR_CUST_NOTE | |
List[AR_SHIP_ADRS_POST] AR_SHIP_ADRS | |
List[AR_CUST_CARDS_POST] AR_CUST_CARDS | |

#### Response Codes
- **<code>201 Created</code>** The request was successful, the customer was added to the Counterpoint database.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer was added to the Counterpoint database.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the customer. See the Message field for more details.

#### Response Body
This endpoint returns data related the customer just added:

#### Sample Response Body
```
{
  "CUST_NO": "100024",
  "reference": "Customer",
  "Link": {
    "uri": "http://localhost:81/CUSTOMER/100024",
    "method": "get"
  },
  "ErrorCode": "SUCCESS"
}
```

Field | Description
----- | -----------
CUST_NO | The CUST_NO of the customer record just adeed to the system.
reference | The type of object just added.
Link  | Contains the URI and http verb that can be used to retrieve the object that was just added.
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.


