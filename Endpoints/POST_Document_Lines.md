
# POST /Document/{DocId}/Lines

#### Description


- Requires API Key: Yes
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request body
````
{
  "PS_DOC_LIN": [
    {
      "LIN_TYP": "O",
      "ITEM_NO": "{{ITEM_NO}}",
      "QTY_SOLD": "3.0",
      "UNIT_COST": "1.1953",
      "PRESUMED_COST": "1.1953"
    }
  ]
}
```

**URI**

`GET https://localhost:81/Document/{DocId}/Lines`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
ITEM_NO | body | string | true | The name of the item to be added.
DocId | path | string | true | The DOC_ID of the document to add a line to.
PS_DOC_LIN | body | PS_DOC_LIN_POST | true | An array of document lines (PS_DOC_LIN) to add.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "Documents": [
    {
      "DOC_ID": 735137152807488,
      "reference": "Order",
      "Link": {
        "uri": "https://localhost:81/Document/735137152807488/Lines",
        "method": "get"
      }
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



