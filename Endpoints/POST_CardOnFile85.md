# POST /CardOnFile85

#### Description
Adds a new credit card to customer in the database

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`POST https://localhost:81/customer/{custNo}/CARD`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : vpmk0tqApzFu5EesAMQgstBtQAEwK1ySwMZ4zwiC`
- `Accept : application/json`
- `Content-Type : application/json`

**Request Body**
```
{"AR_CUST_CARD":{ 
  
  "CARD_DESCR": "Test1",
  "DEFAULT_CARD": "N",
  "PAY_COD": "VISA",
  "CARD_EXP_DAT": "1/1/2018",
  "CARD_NO": "4275330012345675",
  "CARD_NAM": "{{CardName}}"
  }
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
AR_CUST_CARD | body | string | true | A JSON structure containing the customer card data to add.
CardName | body | string | false | the card name description of the card being added.
**NOTE:** Whenever possible, the template customer is used to determine defaults for fields that aren't provided explicitly. The template customer is obtained from the record of the provided workgroup (WRKGRP_ID). If a WKRGRP_ID isn't provided, the default workgroup for the logged in user is used.

AR_CUST_CARD | Required | Field Description
------------ | -------- | -----------------
CUST_NO | * | The CUST_NO for the customer. If not provided, the CUST_NO will be determined by the provided settings in the WRKGRP_ID. if that is not provided, the workgroup settings from the user will be used.
CARD_SEQ_NO | * | The Sequece number related to the credit card.
DEFAULT_CARD | * | Specifies if the card is the default card.
CARD_DESCR | |
PAY_COD | * | The pay code of the card. ie Visa.
CARD_NO | |
CARD_NO_MSK | |
CARD_EXP_DAT | * | The expiration date of the card.
CARD_NAM | |
CARD_NO_ENC | |
CARD_NO_KID | * | Value auto-calculated when card has been added.

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
