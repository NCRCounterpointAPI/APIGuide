
# GET /User/{UserID}

#### Description
Gets information about a user.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/User/MGR`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
UserID | path | string | true | The USR_ID of the user to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The user id provided does not exist in the SY_USR table.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the user information is present under the `SY_USR` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested user id was not present.

#### Sample Response Body

```
{
  "SY_USR": {
    "USR_ID": "MGR",
    "NAM": "Manager",
    "NAM_UPR": "MANAGER",
    "INITIALS": "MGR",
    "ADRS_1": "123 Tournament Lane",
    "CITY": "Memphis",
    "STATE": "TN",
    "ZIP_COD": "38138",
    "CNTRY": "USA",
    "PHONE_1": "901-555-1234",
    "WRKGRP_ID": "1",
    "ALLOW_OTHR_WRKGRPS": "Y",
    "DEPT": "Admin",
    "EMP_NO": "251",
    "SEC_COD": "MGR",
    "IS_PS_USR": "Y",
    "IS_PS_MGR": "Y",
    "PS_SEC_COD": "MGR",
    "IS_SLS_REP": "Y",
    "IS_BUYER": "Y",
    "LOGIN_DISABLED": "N",
    "CHNG_PWD_NXT_LOGIN": "N",
    "LST_PWD_CHNG_DAT": "2015-05-20T00:00:00.0000000-04:00",
    "LST_LOGIN_DT": "2015-05-28T11:14:29.0000000-04:00",
    "LST_STR_ID": "MAIN",
    "LST_STA_ID": "1",
    "LST_DRW_ID": "1",
    "COMMIS_COD": "5-PCT",
    "LST_MAINT_DT": "2012-11-30T10:08:40.0000000-05:00",
    "LST_MAINT_USR_ID": "MGR",
    "LST_WRKGRP_ID": "1",
    "LOGIN_FAIL_CNT": 0,
    "BIO_ID_DATA": "",
    "LST_LOGIN_WKSTN_NAM": "ATLMRITCHIE2",
    "LST_TE_LOGIN_DT": "2015-03-27T11:32:50.0000000-04:00",
    "LST_TE_WRKGRP_ID": "1",
    "LST_TE_LOGIN_WKSTN_NAM": "ATLMRITCHIE2",
    "RS_UTC_DT": "2015-05-28T15:14:29.2870000-04:00",
    "IS_MAIL_MGR": "Y",
    "ALLOW_SEND_POPUPMAIL": "Y",
    "IS_OM_USR": "Y",
    "RS_STAT": 1,
    "RPT_EMAIL": "1",
    "MSR_LOGIN_ID_1": "00000010",
    "MSR_LOGIN_ID_2": "u4HS+6UXPeZulj4MKZXUqKAaXfMlQWZG"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SY_USR object**

Element | Datatype | Description
------- | -------- | -----------



