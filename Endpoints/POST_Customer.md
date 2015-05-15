# POST /Customer

#### Description
Adds a new customer to the database

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`POST https://localhost:81/Customer`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : vpmk0tqApzFu5EesAMQgstBtQAEwK1ySwMZ4zwiC`
- `Accept : application/json`
- `Content-Type : application/json`

**Request Body (Sample)**
```
{
  "AR_CUST": {
    "NAM": "Superman",
    "FST_NAM": "Clark",
    "LST_NAM": "Kent",
    "STR_ID": "100",
    "AR_CUST_NOTE": [
      {
        "Note_ID": "ADDED_85",
        "NOTE_TXT": "Be careful, Clark Kent is Superman."
      }
    ],
    "AR_SHIP_ADRS": [
      {
        "SHIP_ADRS_ID": "ADDRESS_1",
        "NAM": "HOME",
        "SHIP_NAM_TYP": "B"
      },
      {
        "SHIP_ADRS_ID": "ADDRESS_2",
        "NAM": "WORK",
        "SHIP_NAM_TYP": "B"
      }
    ]
  }
}
```

#### Parameters
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
AR_CUST | body | string | true | A JSON structure containing the customer data to add.

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


