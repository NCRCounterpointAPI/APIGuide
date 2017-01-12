
# POST /Document/{DocId}/Note

#### Description
Adds a note to an existing document.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/Document/{DocId}/Note`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
DocId | path | string | true | The DOC_ID of the document to add a note to.
PS_DOC_NOTE | body | true | The document note (PS_DOC_NOTE) to add.

PS_DOC_NOTE | Required | Field Description
----------- | -------- | -----------------
NOTE_ID | * | The note id specified by user.
NOTE_SEQ_NO | |
NOTE_DAT | |
USR_ID | |
NOTE | |
NOTE_TXT | |
LIN_GUID | |

**Sample Request Body**
````
{
    "PS_DOC_NOTE":
      {
        "NOTE_ID" : "Test",
        "NOTE": "{\\rtf1\\ansi\\deff0{\\fonttbl{\\f0\\fnil\\fcharset0 Arial;}}\n\\viewkind4\\uc1\\pard\\lang1033\\fs16 Adding a note to an existing customer!\\par\n\\par\\par\n}"
      }
}
```

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.

#### Sample Response Body

```
{
  "SystemInfo": {
    "SystemDBCreatedDateTime": "2015-05-19T13:36:51.3570000-04:00",
    "ServerLastStartedDateTime": "2015-05-20T09:36:58.8644532-04:00",
    "ServerCodeVersion": "1.0.0.0",
    "ServerOS": "Microsoft Windows NT 6.1.7601 Service Pack 1",
    "Is64bitOS": true,
    "ServerUser": "CORP\\mr185122"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------



