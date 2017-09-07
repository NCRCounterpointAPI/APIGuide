
# GET /Inventory/{LocId}

#### Description
Gets inventory information for all items at a location.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:52000/Inventory/MAIN`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
- LocId | Path | The LOC_ID to retrieve inventory data for | Required

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
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and an array of item information is present under the `Items` section of the response body.

#### Sample Response Body

```
{
  "IM_INV": [
    {
      "ITEM_NO": "ADM-TL2",
      "LOC_ID": "MAIN",
      "MIN_QTY": 3,
      "MAX_QTY": 12,
      "QTY_COMMIT": 0,
      "QTY_ON_HND": -5,
      "QTY_ON_PO": 8,
      "QTY_ON_BO": 0,
      "QTY_ON_XFER_OUT": 0,
      "QTY_ON_XFER_IN": 0,
      "LST_COST": 174.995,
      "COST_OF_SLS_PCT": 0,
      "FST_RECV_DAT": "2000-06-29T00:00:00.0000000",
      "LST_RECV_DAT": "2000-06-29T00:00:00.0000000",
      "FST_SAL_DAT": "2000-04-27T00:00:00.0000000",
      "LST_SAL_DAT": "2014-04-09T00:00:00.0000000",
      "LST_CNT_DAT": "2000-07-27T00:00:00.0000000",
      "LST_ORD_DAT": "2012-10-03T00:00:00.0000000",
      "NXT_EXPECTD_PO": "100064",
      "GL_VAL": -1338.45,
      "LST_MAINT_DT": "2014-04-25T10:14:49.7670000",
      "LST_MAINT_USR_ID": "MGR",
      "LST_LCK_DT": "2014-04-25T10:14:49.8900000",
      "QTY_ON_ORD": 0,
      "QTY_ON_LWY": 0,
      "QTY_ON_SO": 3,
      "RS_UTC_DT": "2014-04-25T14:14:49.8970000",
      "NET_QTY": 3,
      "QTY_AVAIL": -5,
      "STK_STAT_PER_QTY_ON_HND": "O",
      "STK_STAT_PER_QTY_AVAIL": "O",
      "STK_STAT_PER_NET_QTY": "K",
      "RS_STAT": 1,
      "DROPSHIP_QTY_ON_CUST_ORD": 0,
      "DROPSHIP_QTY_ON_PO": 0,
      "IM_INV_CELL": []
    },
    {
      "ITEM_NO": "ADM-TL3",
      "LOC_ID": "MAIN",
      "MIN_QTY": 3,
      "MAX_QTY": 12,
      "QTY_COMMIT": 0,
      "QTY_ON_HND": -3,
      "QTY_ON_PO": 0,
      "QTY_ON_BO": 0,
      "QTY_ON_XFER_OUT": 0,
      "QTY_ON_XFER_IN": 0,
      "LST_COST": 174.995,
      "COST_OF_SLS_PCT": 0,
      "FST_RECV_DAT": "2000-06-29T00:00:00.0000000",
      "LST_RECV_DAT": "2007-06-23T00:00:00.0000000",
      "FST_SAL_DAT": "2000-04-27T00:00:00.0000000",
      "LST_SAL_DAT": "2012-02-02T00:00:00.0000000",
      "LST_CNT_DAT": "2000-07-27T00:00:00.0000000",
      "LST_ORD_DAT": "2006-03-18T00:00:00.0000000",
      "GL_VAL": -747.45,
      "LST_MAINT_DT": "2012-02-02T14:15:39.4200000",
      "LST_MAINT_USR_ID": "MGR",
      "LST_LCK_DT": "2012-02-02T14:15:39.4670000",
      "QTY_ON_ORD": 0,
      "QTY_ON_LWY": 0,
      "QTY_ON_SO": 0,
      "RS_UTC_DT": "2012-02-02T19:15:39.4630000",
      "NET_QTY": -3,
      "QTY_AVAIL": -3,
      "STK_STAT_PER_QTY_ON_HND": "O",
      "STK_STAT_PER_QTY_AVAIL": "O",
      "STK_STAT_PER_NET_QTY": "O",
      "RS_STAT": 0,
      "DROPSHIP_QTY_ON_CUST_ORD": 0,
      "DROPSHIP_QTY_ON_PO": 0,
      "IM_INV_CELL": []
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Inventory object**

Element | Datatype | Description
------- | -------- | -----------
