
# PUT /Document/{DocId}/Contact

#### Description
Adds a contact to an existing document.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`PUT https://localhost:81/Document/{DocId}/Contact`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
DocId | path | string | true | The DOC_ID of the document to add a contact to.
PS_DOC_CONTACT | body | PS_DOC_CONTACT_PATCH | true | The document contact (PS_DOC_CONTACT) to update. Include only fields to update..

PS_DOC_CONTACT | Required | Field Description
-------------- | -------- | -----------------
NAM | |
FST_NAM | |
LST_NAM | |
SALUTATION | |
ADRS_1 | |
ADRS_2 | |
ADRS_3 | |
CITY | |
STATE | |
ZIP_COD | |
CNTRY | |
PHONE_1 | |
PHONE_2 | |
ADRS_ID | |
NAM_TYP | * | The name type for the contact.
EMAIL_ADRS_1 | |
EMAIL_ADRS_2 | |
CONTCT_1 | |
CONTCT_2 | |
FAX_1 | |
FAX_2 | |

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information
