
# GET /ItemCategories

#### Description
Gets a list of all Categories and subcategories in the system. This will return a hierarchical list, with subcategory records structured as children of their parent category.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/ItemCategories`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
None

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.

#### Sample Response Body

```
{
  "ItemCategories": [
    {
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
    {
      "CATEG_COD": "FOOD",
      "DESCR": "Food items",
      "DESCR_UPR": "FOOD ITEMS",
      "LST_MAINT_DT": "2009-07-29T15:17:51.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "MIN_PFT_PCT": 30,
      "RS_UTC_DT": "2015-03-13T19:11:33.2470000",
      "TRGT_PFT_PCT": 50,
      "RS_STAT": 1,
      "IM_SUBCAT_COD": [
        {
          "SUBCAT_COD": "DRINKS",
          "CATEG_COD": "FOOD",
          "DESCR": "Food - Drinks",
          "DESCR_UPR": "FOOD - DRINKS",
          "LST_MAINT_DT": "2001-11-14T09:23:00.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        },
        {
          "SUBCAT_COD": "SNACKS",
          "CATEG_COD": "FOOD",
          "DESCR": "Food - Snacks",
          "DESCR_UPR": "FOOD - SNACKS",
          "LST_MAINT_DT": "2001-11-14T09:23:09.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        }
      ]
    },
    {
      "CATEG_COD": "FORECAST",
      "DESCR": "Demo forecasting data",
      "DESCR_UPR": "DEMO FORECASTING DATA",
      "LST_MAINT_DT": "2009-07-29T15:17:57.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "MIN_PFT_PCT": 30,
      "RS_UTC_DT": "2015-03-13T19:11:33.2470000",
      "TRGT_PFT_PCT": 50,
      "RS_STAT": 1,
      "IM_SUBCAT_COD": []
    },
    {
      "CATEG_COD": "GOLF",
      "DESCR": "Golf items",
      "DESCR_UPR": "GOLF ITEMS",
      "LST_MAINT_DT": "2009-07-29T16:57:27.0000000",
      "LST_MAINT_USR_ID": "MGR",
      "MIN_PFT_PCT": 50,
      "RS_UTC_DT": "2015-03-13T19:11:33.2470000",
      "TRGT_PFT_PCT": 65,
      "RS_STAT": 1,
      "IM_SUBCAT_COD": [
        {
          "SUBCAT_COD": "ACCES",
          "CATEG_COD": "GOLF",
          "DESCR": "Golf - Accessories",
          "DESCR_UPR": "GOLF - ACCESSORIES",
          "LST_MAINT_DT": "2001-11-14T09:22:54.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        },
        {
          "SUBCAT_COD": "BALLS",
          "CATEG_COD": "GOLF",
          "DESCR": "Golf - Balls",
          "DESCR_UPR": "GOLF - BALLS",
          "LST_MAINT_DT": "2001-11-14T09:22:56.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        },
        {
          "SUBCAT_COD": "CLUBS",
          "CATEG_COD": "GOLF",
          "DESCR": "Golf - Clubs",
          "DESCR_UPR": "GOLF - CLUBS",
          "LST_MAINT_DT": "2001-11-14T09:22:58.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        },
        {
          "SUBCAT_COD": "FEES",
          "CATEG_COD": "GOLF",
          "DESCR": "Golf - Fees",
          "DESCR_UPR": "GOLF - FEES",
          "LST_MAINT_DT": "2001-11-14T09:23:02.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        },
        {
          "SUBCAT_COD": "MISC",
          "CATEG_COD": "GOLF",
          "DESCR": "Golf - Misc items",
          "DESCR_UPR": "GOLF - MISC ITEMS",
          "LST_MAINT_DT": "2001-11-14T09:23:06.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        },
        {
          "SUBCAT_COD": "SPECIAL",
          "CATEG_COD": "GOLF",
          "DESCR": "Special order items for Golf",
          "DESCR_UPR": "SPECIAL ORDER ITEMS FOR GOLF",
          "LST_MAINT_DT": "2001-11-14T09:23:10.0000000",
          "LST_MAINT_USR_ID": "Z",
          "RS_STAT": 0
        }
      ]
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**ItemCategory object**

Element | Datatype | Description
------- | -------- | -----------



