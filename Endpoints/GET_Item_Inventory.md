
# GET /Item/{ItemNo}/Inventory/{LocId}

#### Description
Gets inventory information for item at a location.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Item/ADM-SCD/Inventory/MAIN`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
- ItemNo | Path | The ITEM_NO to retrieve inventory data for | Required
- LocId | Path | The LOC_ID to retrieve inventory data for | Required

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
  "IM_INV": {
    "ITEM_NO": "ADM-SCD",
    "LOC_ID": "EAST",
    "MIN_QTY": 0,
    "MAX_QTY": 0,
    "QTY_COMMIT": -1,
    "QTY_ON_HND": 3,
    "QTY_ON_PO": 0,
    "QTY_ON_BO": 0,
    "QTY_ON_XFER_OUT": 0,
    "QTY_ON_XFER_IN": 0,
    "LST_COST": 0,
    "COST_OF_SLS_PCT": 0,
    "GL_VAL": 811.79,
    "LST_LCK_DT": "2008-07-30T07:48:32.7500000",
    "QTY_ON_ORD": 0,
    "QTY_ON_LWY": 0,
    "QTY_ON_SO": 0,
    "RS_UTC_DT": "2012-07-16T16:53:42.0100000",
    "NET_QTY": 4,
    "QTY_AVAIL": 4,
    "STK_STAT_PER_QTY_ON_HND": "?",
    "STK_STAT_PER_QTY_AVAIL": "?",
    "STK_STAT_PER_NET_QTY": "?",
    "RS_STAT": 0,
    "DROPSHIP_QTY_ON_CUST_ORD": 0,
    "DROPSHIP_QTY_ON_PO": 0,
    "IM_INV_CELL": []
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Inventory object**

Element | Datatype | Description
------- | -------- | -----------
