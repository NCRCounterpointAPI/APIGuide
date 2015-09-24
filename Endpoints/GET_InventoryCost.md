
# GET /Item/{ItemNo}/InventoryCost/{LocId}

#### Description
Gets inventory cost information for an item at a location.

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
- ItemNo | Path | The ITEM_NO to retrieve inventory cost data for | Required
- LocId | Path | The LOC_ID to retrieve inventory cost data for | Required

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
  "IM_INV_LOC": {
    "ITEM_NO": "ADM-SCD",
    "LOC_ID": "MAIN",
    "LST_AVG_COST": 166.32,
    "STD_COST": 0,
    "AVG_COST": 166.32
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Inventory Cost object**

Element | Datatype | Description
------- | -------- | -----------
