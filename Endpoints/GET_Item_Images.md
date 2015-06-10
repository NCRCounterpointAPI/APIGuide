
# GET /Item/{ItemNo}/Images

#### Description
Gets a list of available item image filenames for a given item. Note this does not get the images themselves, just a list of the available image filenames. To get a specific image, use the [/Item/Images/{filename}](GET_Item_ImageFilename.md) endpoint.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Item/ADM-SCD/Images`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
ItemNo | path | string | true | The ITEM_NO of the item to retrieve image filenames for.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The item provided does not exist. Note that if the item exists, but no images exist, a 200 will be returned with an empty image list.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `IM_ITEM` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested item was not present.

#### Sample Response Body

```
{
  "IMAGE_FILENAMES": [
    "ADM-SCD.jpg"
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Item object**

Element | Datatype | Description
------- | -------- | -----------



