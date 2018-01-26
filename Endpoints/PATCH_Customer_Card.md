# PATCH /Customer/{CustNo}/Card

#### Description
Add or update a credit card's expiration date.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes
- Requires Company Administrator: Yes

#### Sample Request

**URI**

`PATCH https://localhost:81/Customer/{CustNo}/CARD?CardSeqNo={CardSeqNo}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`
- `Content-Type : application/json`

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
custNo | path | string | true | The CUST_NO of the customer to update.
CardSeqNo | query | string | true | The AR_CUST_CARD.CARD_SEQ_NO of the card to update.
AR_CUST_CARD | body | AR_CUST_CARDS_PATCH | true | The customer card on file to update. CARD_SEQ_NO of the card to update must be included, along with any other fields to update.

AR_CUST_CARD | Required | Field Description
------------ | -------- | -----------------
DEFAULT_CARD | * | Indicates whether the card is a default card
CARD_DESCR | |
PAY_COD | * | Indicates the type of paycode of the card. 
CARD_NO | |
CARD_EXP_DAT | * | The expiration date of credit card.
CARD_NAM | |

**Sample Request Body**
```
{"AR_CUST_CARD":{ 
  
  "CARD_DESCR": "Edit Exp Date",
  "DEFAULT_CARD": "N",
  "PAY_COD": "VISA",
  "CARD_EXP_DAT": "1/1/2020",
  "CARD_NO": "4275330012345675",
  "CARD_NAM": "{{CardName}}"
}}
```

#### Response Codes
- **<code>201 Created</code>** The request was successful, the customer was added to the Counterpoint database.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful.
- `ERROR_UNKNOWN`: An error occurred during Customer Update.

#### Sample Response Body
```
{
  "CUST_NO": "1000",
  "reference": "Customer",
  "Link": {
    "uri": "https://wusmj185111-t75:52000/customer/1000/CARD?CardSeqNo=1",
    "method": "get"
  },
  "ErrorCode": "SUCCESS"
}
```

Field | Description
------ | -----------
ErrorCode | "SUCCESS" if the call was succesful, otherwise, an error code describing the cause for failure.
Message | When the ErrorCode is not "SUCCESS", Message will contain a human readable description of the error. Otherwise, this field will not be present in the response.
