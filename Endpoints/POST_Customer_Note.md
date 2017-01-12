# POST /Customer/{CustNo}/Note

#### Description
Adds a note to an existing customer.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`POST https://localhost:81/Customer/{CustNo}/Note`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : vpmk0tqApzFu5EesAMQgstBtQAEwK1ySwMZ4zwiC`
- `Accept : application/json`
- `Content-Type : application/json`

**Request Body**
```
{
 "AR_CUST_NOTE": [
   {
     "Note_ID": "ADDED_85",
     "NOTE_TXT": "Be careful, Clark Kent is Superman."
    }
  ]
} 
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
CustNo | path | string | True | The CUST_NO of the customer to add a note to.
AR_CUST_NOTE | body | AR_CUST_NOTE_POST | true | The customer note (AR_CUST_NOTE) to add.

AR_CUST_NOTE | Required | Field Description
------- | -------- | -----------------
NOTE_ID | * | The note id provided by user
USR_ID | |
NOTE | |
NOTE_TXT | |
LST_MAINT_USR_ID | |
LST_LCK_DT | |

#### Response Codes
- **<code>201 Created</code>** The request was successful, the customer was added to the Counterpoint database.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>403 Forbidden</code>** The request could not be fulfilled. Likely due to a missing, invalid, or expired APIKey, or a missing API option in the company's registration.ini 
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer was added to the Counterpoint database.
- `ERROR_UNKNOWN`: An unexpected error occurred adding the customer. See the Message field for more details.

#### Response Body
This endpoint returns data related the customer just added:

#### Sample Response Body
```
{
  "CUST_NO": "100024",
  "reference": "Customer",
  "Link": {
    "uri": "http://localhost:81/CUSTOMER/100024",
    "method": "get"
  },
  "ErrorCode": "SUCCESS"
}
```

Field | Description
----- | -----------
CUST_NO | The CUST_NO of the customer record just adeed to the system.
reference | The type of object just added.
Link  | Contains the URI and http verb that can be used to retrieve the object that was just added.
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.

