
# GET /Item/{ItemNo}/Serials/Location/{LocId}

#### Description
Gets serials that are active for the given item at the given location.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Items/MAIN/Item/{ItemNo}/Serial/{SerialNo}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters

Name | Parameter Type | Data Type | Description | Required
---- | -------------- | --------- | -------- | -----------
- ItemNo | path | string | The ITEM_NO of the item serial to retrieve | true
- LocId | path | string | The LOC_ID of the item serial to retrieve | true

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.

#### Sample Response Body

```
{
  "ItemSerials": [
 {
      "ITEM_NO": "ADM-LASER",
      "SER_NO": "1129",
      "LOC_ID": "SECURE PAY",
      "STAT": "A",
      "PREV_STAT": "!",
      "MAN_ENTD": "N",
      "LST_MAINT_DT": "2012-07-18T12:53:00.0000000",
      "LST_MAINT_USR_ID": "MGR"
    },
    {
      "ITEM_NO": "ADM-LASER",
      "SER_NO": "1130",a
      "LOC_ID": "SECURE PAY",
      "STAT": "A",
      "PREV_STAT": "!",
      "MAN_ENTD": "N",
      "LST_MAINT_DT": "2012-07-18T12:53:00.0000000",
      "LST_MAINT_USR_ID": "MGR"
    },
    {
      "ITEM_NO": "ADM-LASER",
      "SER_NO": "2",
      "LOC_ID": "SECURE PAY",
      "STAT": "A",
      "PREV_STAT": "!",
      "SER_COST": 173.32,
      "MAN_ENTD": "N",
      "RECV_DAT": "2015-12-22T00:00:00.0000000",
      "VEND_NO": "AMAGOLF",
      "LST_MAINT_DT": "2015-12-22T13:39:42.7430000",
      "LST_MAINT_USR_ID": "MGR"
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Item object**

Element | Datatype | Description
------- | -------- | -----------
