
# PUT /Document/{DocId}/Note

#### Description
Updates an existing customer note..

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`PUT https://localhost:81/Document/{DocId}/Note`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
DocId | path | string | true | The DOC_ID of the document the note is attached to.
PS_DOC_NOTE | body | PS_DOC_NOTE_PATCH | true | The document note (PS_DOC_NOTE) to update. Include only fields to update.

PS_DOC_NOTE | Required | Field Description
NOTE_ID | * | The note Id specified by the user.
NOTE_SEQ_NO | |
NOTE_DAT | |
USR_ID | |
NOTE | |
NOTE_TXT | |
LIN_GUID | |
        
#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>404 Not Found</code>** The requested resource could not be found but may be available again in the future.  Subsequent requests by the client are permissible.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.
- `ERROR_RECORD_NOT_FOUND`: Record does not exist for the DocId given in parameter.
