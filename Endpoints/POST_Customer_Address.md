# POST /Customer/{CustNo}/Address

#### Description
Adds a note to an existing customer.

- Requires API Key: Yes
- Requires System Administrator: No
- Requires Counterpoint Registration option: Yes

#### Sample Request

**URI**

`POST https://localhost:81/Customer/{CustNo}/Address`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `APIKey : vpmk0tqApzFu5EesAMQgstBtQAEwK1ySwMZ4zwiC`
- `Accept : application/json`
- `Content-Type : application/json`

**Request Body**
```
{
 "AR_SHIP_ADRS": [
      {
        "NAM": "Home address",
        "SHIP_ADRS_ID": "HOME",
        "SHIP_NAM_TYP": "P",
        "FST_NAM": "Grandma",
        "LST_NAM": "Gilmore",
        "SALUTATION": "Mrs.",
        "ADRS_1": "1 Waterford Way",
        "CITY": "Topeka",
        "STATE": "KA",
        "ZIP_COD": 10101
      }
} 
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
CustNo | path | string | True | The CUST_NO of the customer to add a shipping address to.
AR_SHIP_ADRS | body | AR_SHIP_ADRS_POST | true | The customer shipping address (AR_SHIP_ADRS) to add..

AR_SHIP_ADRS | Required | Field Description
------- | -------- | -----------------
SHIP_ADRS_ID | * | The proiived id/description of the ship address.
NAM | * | The name for the ship address
NAM_UPR | |
FST_NAM | |
FST_NAM_UPR | |
LST_NAM | |
LST_NAM_UPR | |
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
FAX_1 | |
FAX_2 | |
CONTCT_1 | |
CONTCT_2 | |
EMAIL_ADRS_1 | |
EMAIL_ADRS_2 | |
URL_1 | |
URL_2 | |
SHIP_ZONE_COD | |
SHIP_VIA_COD | |
TAX_COD | |
COMMNT | |
LST_MAINT_USR_ID | |
LST_LCK_DT | |
SHIP_NAM_TYP | * | They name type of ship address
SHIP_FST_LST_NAM | |

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
