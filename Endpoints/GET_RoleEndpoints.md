# GET /Role/Endpoints

#### Description
Gets a list of endpoints that can be made available to any role.

- Requires API Key: No
- Requires System Administrator: No
- Requires Counterpoint Registration option: No
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Role/Endpoints`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Response Codes
- **<code>200 OK</code>** The request was successful, the endpoint data was returned.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the endpoint data was returned.
- `ERROR_UNKNOWN`: An unexpected error occurred. See the Message field for more details.

**Response Body**
```
{
  "EndpointList": [
    {
      "Path": "/Company",
      "HasGet": true,
      "HasPost": false,
      "HasPatch": false,
      "HasPut": false,
      "HasDelete": false
    },
    {
      "Path": "/Customer",
      "HasGet": false,
      "HasPost": true,
      "HasPatch": false,
      "HasPut": false,
      "HasDelete": false
    },
    {
      "Path": "/TaxCodes",
      "HasGet": true,
      "HasPost": false,
      "HasPatch": false,
      "HasPut": false,
      "HasDelete": false
    },
    {
      "Path": "/Workgroup/{WorkgroupId}",
      "HasGet": true,
      "HasPost": false,
      "HasPatch": false,
      "HasPut": false,
      "HasDelete": false
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**EndpointList**

Element | Datatype | Description
------- | -------- | -----------
EndpointList | List | A list of endpoints.


**Endpoint object**

Element | Datatype | Description
------- | -------- | -----------
Path | string | The path of this endpoint.
HasGet | bool | This endpoint supports Get.
HasPost | bool | This endpoint supports Post.
HasPatch | bool | This endpoint supports Patch.
HasPut | bool | This endpoint supports Put.
HasDelete | bool | This endpoint supports Delete.
