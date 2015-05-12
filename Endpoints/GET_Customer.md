# GET /Customer/{CustNo}

#### Description
The endpoint gets information about the specified customer

Requires API Key: Yes
Requires System Administrator: No

#### Sample
https://localhost:81/Customer/100010

#### Parameters
Name|Parameter Type|Data Type|Required|Description
--------------------------------------------------
CustNo|path|string|true|The CUST_NO of the customer to retrieve.

#### Response Codes
**<code>200 OK</code>**|The request was successful, the result of the call will be in the response body.
**<code>404 Not Found</code>**|The CUST_NO provided was not a valid CUST_NO in the AR_CUST table.
**<code>500 Internal Server Error</code>**|The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.