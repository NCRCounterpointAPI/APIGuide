
# GET /ItemCategory/{CategoryCode}

#### Description
Gets information about a category and it's child subcategories

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/ItemCategory/APPAREL`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
CategoryCode | path | string | true | The CATEG_COD of the category to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The category code provided does not exist.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `Category` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested category code was not present.

#### Sample Response Body

```
{
  "Category": {
    "CATEG_COD": "APPAREL",
    "DESCR": "Apparel items",
    "DESCR_UPR": "APPAREL ITEMS",
    "LST_MAINT_DT": "2009-07-29T16:56:00.0000000",
    "LST_MAINT_USR_ID": "MGR",
    "MIN_PFT_PCT": 50,
    "RS_UTC_DT": "2015-03-13T19:11:33.2470000",
    "TRGT_PFT_PCT": 70,
    "RS_STAT": 1,
    "IM_SUBCAT_COD": [
      {
        "SUBCAT_COD": "MENS",
        "CATEG_COD": "APPAREL",
        "DESCR": "Apparel - Mens",
        "DESCR_UPR": "APPAREL - MENS",
        "LST_MAINT_DT": "2001-11-14T09:23:05.0000000",
        "LST_MAINT_USR_ID": "Z",
        "RS_STAT": 0
      },
      {
        "SUBCAT_COD": "WOMENS",
        "CATEG_COD": "APPAREL",
        "DESCR": "Apparel - Womens",
        "DESCR_UPR": "APPAREL - WOMENS",
        "LST_MAINT_DT": "2001-11-14T09:23:13.0000000",
        "LST_MAINT_USR_ID": "Z",
        "RS_STAT": 0
      }
    ]
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Category object**

Element | Datatype | Description
------- | -------- | -----------



