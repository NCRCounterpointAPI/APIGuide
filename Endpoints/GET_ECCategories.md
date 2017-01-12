
# GET /ECCategories

#### Description
Gets eCommerce category information.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/ECCategories`

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
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "EC_CATEG": [
    {
      "CATEG_ID": "2002092510211378",
      "DESCR": "Apparel",
      "DESCR_UPR": "APPAREL",
      "IMG_FILE": "Category-Apparel.jpg",
      "HTML_DESCR": "",
      "DISP_SEQ_NO": 0,
      "LST_MAINT_DT": "2002-09-25T19:45:01.0000000",
      "LST_MAINT_USR_ID": "Z",
      "EC_CATEG_ITEM": []
    },
    {
      "CATEG_ID": "2002092510224995",
      "DESCR": "Golf",
      "DESCR_UPR": "GOLF",
      "IMG_FILE": "Category-Golf.jpg",
      "HTML_DESCR": "",
      "DISP_SEQ_NO": 1,
      "LST_MAINT_DT": "2002-09-25T19:45:01.0000000",
      "LST_MAINT_USR_ID": "Z",
      "EC_CATEG_ITEM": []
    },
    {
      "CATEG_ID": "2002092510233822",
      "DESCR": "Misc Items",
      "DESCR_UPR": "MISC ITEMS",
      "IMG_FILE": "Category-Misc.jpg",
      "HTML_DESCR": "\r\n",
      "DISP_SEQ_NO": 2,
      "LST_MAINT_DT": "2002-09-25T19:45:01.0000000",
      "LST_MAINT_USR_ID": "Z",
      "EC_CATEG_ITEM": [
        {
          "ITEM_NO": "APL-UMB",
          "CATEG_ID": "2002092510233822",
          "ENTRY_SEQ_NO": 1,
          "LST_MAINT_DT": "2002-09-25T10:59:26.0000000",
          "LST_MAINT_USR_ID": "Z"
        },
        {
          "ITEM_NO": "BALL-RET-PRO",
          "CATEG_ID": "2002092510233822",
          "ENTRY_SEQ_NO": 1,
          "LST_MAINT_DT": "2002-09-25T11:00:24.0000000",
          "LST_MAINT_USR_ID": "Z"
        }
      ]
    },
    "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



