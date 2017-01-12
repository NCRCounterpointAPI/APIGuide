
# POST /Document/{DocId}/Payments

#### Description
Adds a line to an existing document.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`GET https://localhost:81/Document/{DocId}/Payments`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
DocId | path | string | true | The DOC_ID of the document to add a payment to.
PS_DOC_PMT | body | PS_DOC_PMT_POST | true | An array of document payments (PS_DOC_PMT) to add.

**Request Body**

PS_DOC_PMT | Required | Field Description
--------------- | -------- | -----------------
CARD_NO | | Card number if payment is made by credit card
AMT | * | The amount to by applied with payment
FINAL_PMT | * | indicates if this is a final payment
CARD_IS_NEW | * | indicates if card is new.
SECURE_ECOMM_TRX | * | indicates if secure eccomerce transaction
PAY_COD | |
DEP_LIN_COPIED_TO_REL_DOC | * | 
EXCH_LOSS | * |
SIG_IMG | |
SIG_IMG_VECTOR | |
EDC_AUTH_COD | |
EBT_BAL_REMAIN | |
LOY_PTS_RDM | |
SVC_BAL_REMAIN | |
SVC_REF_NO | |
EDC_AUTH_RESP  | |
ROUND_GAIN_LOSS | |
HOME_CURNCY_ROUND_GAIN_LOSS | |
   

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information
