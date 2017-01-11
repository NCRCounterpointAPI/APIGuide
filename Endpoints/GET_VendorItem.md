
# GET /VendorItem/{VendorNo}/Item/{ItemNo}

#### Description
Retrieves information about Vendor Item.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

`GET https://localhost:81/VendorItem/{VendorNo}/Item/{ItemNo}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : `
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
VendorNo | path | string | true | The VEND_NO  to retrieve item information for.
ItemNo | path | string | true | The ITEM_NO of the item to retrieve Vendor information for.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>404 Not Found</code>** The item provided does not exist in the IM_ITEM table.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the workgroup information is present under the `IM_ITEM` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested Vendor Item was not found in the company data.

#### Response Body

**Item object**

Element | ParameterType | Description
------- | -------- | -----------
PO_VEND_ITEM | body | Data from PO_VEND_ITEM for the given UserId

