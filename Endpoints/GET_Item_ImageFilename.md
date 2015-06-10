
# GET /Item/Images/{filename}

#### Description
Gets the image for the given filename. Note this returns the actual image. To get a list of available image filenames for a given item, use the [/Item/{ItemNo}/Images](GET_Item_Images.md) endpoint.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/Item/Images/ADM-SCD.jpg`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
filename | path | string | true | The filename of the item image to retrieve.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The filename provided does not exist. Note that if the item exists, but no images exist, a 200 will be returned with an empty image list.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `IM_ITEM` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested filename was not present.

#### Sample Response Body
The image itself will be returned, with a `CONTENT-TYPE` of `image/jpg`.



