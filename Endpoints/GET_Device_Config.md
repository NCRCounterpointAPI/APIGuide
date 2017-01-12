# GET /DeviceConfig/{WorkstationID}

#### Description
Get the device config for the workstation

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`GET https://localhost:81/DeviceConfig/{WorkstationID}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
WorkstationID | path | string | true | The Workstation ID.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the roles data was returned.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The request could not be fulfilled.  The role name provided was not found.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the role data was returned.
- `ERROR_RECORD_NOT_FOUND`: The role name provided was not found.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the role. See the Message field for more details.

**Sample Response Body**
```
{
  "DeviceConfig": {
    "DEV_CFG_ID": 100000000000159,
    "ASSEM_NAM": "NCR.Counterpoint.Devices.Controllers.dll",
    "CLASS_NAM": "NCR.Counterpoint.Devices.LineDisplay.DCBSimulator.SimulatorLineDisplay",
    "WORKSTATION_ID": "100000000000101",
    "DISABLED": "N",
    "FST_MAINT_DT": "2012-03-21T13:42:06.6500000",
    "FST_MAINT_USR_ID": "MGR2",
    "LST_MAINT_DT": "2012-03-21T13:42:06.6530000",
    "LST_MAINT_USR_ID": "MGR2",
    "RS_UTC_DT": "2016-05-11T15:18:57.9970000",
    "RS_STAT": 1,
    "PS_DEV_ATTR": [
      {
        "DEV_CFG_ID": 100000000000159,
        "ATTR_KEY": "Connection",
        "ATTR_VAL": ""
      },
      {
        "DEV_CFG_ID": 100000000000159,
        "ATTR_KEY": "Description",
        "ATTR_VAL": ""
      },
      {
        "DEV_CFG_ID": 100000000000159,
        "ATTR_KEY": "MessageSet",
        "ATTR_VAL": "1"
      },
      {
        "DEV_CFG_ID": 100000000000159,
        "ATTR_KEY": "SubscribedLineDisplayEvents",
        "ATTR_VAL": "32767"
      }
    ]
  },
  "ErrorCode": "SUCCESS"
}
```
