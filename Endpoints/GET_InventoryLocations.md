
# GET /Inventory/Locations

#### Description
Gets information about an item.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:52000/Inventory/Locations`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
None

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `IM_LOC` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested item was not present.

#### Sample Response Body

```
{
    "IM_LOC": [
        {
            "LOC_ID": "10",
            "DESCR": "FDMS North Retail Store",
            "DESCR_UPR": "FDMS NORTH RETAIL STORE",
            "LST_MAINT_DT": "2015-02-16T14:33:23.0000000",
            "LST_MAINT_USR_ID": "MGR",
            "RS_UTC_DT": "2015-02-16T19:33:23.0000000",
            "ANNL_HLD_COST_PERC": 25,
            "FORC_USE_XFER_IN": "N",
            "RS_STAT": 0
        },
        {
            "LOC_ID": "11",
            "DESCR": "FDMS North Retail/EBT",
            "DESCR_UPR": "FDMS NORTH RETAIL/EBT",
            "LST_MAINT_DT": "2015-02-16T14:38:13.0000000",
            "LST_MAINT_USR_ID": "MGR",
            "RS_UTC_DT": "2015-02-16T19:38:13.0000000",
            "ANNL_HLD_COST_PERC": 25,
            "FORC_USE_XFER_IN": "N",
            "RS_STAT": 0
        },
        {
            "LOC_ID": "12",
            "DESCR": "FDMS North MOTO",
            "DESCR_UPR": "FDMS NORTH MOTO",
            "LST_MAINT_DT": "2015-02-16T14:39:43.0000000",
            "LST_MAINT_USR_ID": "MGR",
            "RS_UTC_DT": "2015-02-16T19:39:43.0000000",
            "ANNL_HLD_COST_PERC": 25,
            "FORC_USE_XFER_IN": "N",
            "RS_STAT": 0
        },
        {
            "LOC_ID": "13",
            "DESCR": "FDMS North Ecommerce",
            "DESCR_UPR": "FDMS NORTH ECOMMERCE",
            "LST_MAINT_DT": "2015-02-16T14:40:30.0000000",
            "LST_MAINT_USR_ID": "MGR",
            "RS_UTC_DT": "2015-02-16T19:40:30.0000000",
            "ANNL_HLD_COST_PERC": 25,
            "FORC_USE_XFER_IN": "N",
            "RS_STAT": 0
        },
        {
            "LOC_ID": "20",
            "DESCR": "FDMS South Retail",
            "DESCR_UPR": "FDMS SOUTH RETAIL",
            "LST_MAINT_DT": "2015-02-16T14:41:42.0000000",
            "LST_MAINT_USR_ID": "MGR",
            "RS_UTC_DT": "2015-02-16T19:41:42.0000000",
            "ANNL_HLD_COST_PERC": 25,
            "FORC_USE_XFER_IN": "N",
            "RS_STAT": 0
        },
        ...
    ],
    "ErrorCode": "SUCCESS"
}
```

#### Response Body

**IM_LOC object**

Element | Datatype | Description
------- | -------- | -----------
