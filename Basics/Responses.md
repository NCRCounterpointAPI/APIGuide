# Working with http responses
http responses that are issued back to API clients use a similar format to other REST API implementations. First and foremost, the http Status code should be checked to determine the result of the call. A complete list of http status codes can be found [here](), but below is a table that shows the subset of result codes that are typically used by the NCR Counterpoint API server:

## Common http Result status codes
Status Code | Name | Description
----------- | ---- | -----------
200 | OK / Success | The call was successful. Most commonly used with GET operations.
201 | Created | The call was successful and the resource submitted was created. Typically used with POST operations that add resources to Counterpoint.
400 | Bad Request | The call failed because the required information was not provided. This could mean JSON was malformed, required data was missing, or invlalid data was submitted.
401 | Unauthorized | The username or password submitted in the basic authorization header was not valid. This could include an invalid company name prefix on a username.
403 | Forbidden | The user is not allowed to make this request. Often this means the required "APIKey" header was not supplied or is invalid, or the company does not have the API option enabled in their registration.ini file.
404 | Not Found | The resource requested does not exist. This typically means the provided endpoint may not be valid.
500 | Internal Server Error | The request could not be fulfilled due to an internal error. This could indicate a configuration issue, a bug in the system, or some other error.

## Common response data
Of course, the response body will typically include the request specific data for a given endpoint, but all Counterpoint calls also return some standard information to help applications identify more specific error cases, and provide user friendly messaging for most error conditions. Below is a typical response object from a failed call:
```
{
  "ErrorCode": "ERROR_RECORD_NOT_FOUND",
  "Message": "Customer 10034 not found"
}
```
Note that on successful calls (http status in the 2xx range, and ErrorCode equals "SUCCESS"), the "Message" element will not be included in the response, as there is no error message to return.

In addition to the elements above, a successful call will typically include other data elements that are specific to the endpoint. See the document on a given endpoint for more information. Below is a complete list of current ErrorCodes:
```
    public enum ErrorCodes
    {
        SUCCESS,
        ERROR_MISSING_REQUIRED_DATA,
        ERROR_RECORD_NOT_FOUND,
        ERROR_UNKNOWN,
        ERROR_DOCUMENT_ALREADY_COMPLETED,
        ERROR_INVALID_APIKEY,
        ERROR_DOCUMENT_NOT_FULLY_PAID,
        ERROR_CARD_PAYMENT_FAILED,
        ERROR_INVALID_GIFTCARD_PAYMENT,
        ERROR_AR_PAYMENT_FAILED,
        ERROR_INVALID_LIN_TYP,
        ERROR_NOT_PURE_ORDER,
        ERROR_DOCUMENT_HAS_SHIPPING_ADDRESS,
        ERROR_DOCUMENT_HAS_BILLING_ADDRESS,
        ERROR_INVALID_CONTACT_ID,
        ERROR_DOCUMENT_BILLING_ADDRESS_NOT_FOUND,
        ERROR_DOCUMENT_SHIPPING_ADDRESS_NOT_FOUND,
        ERROR_INVALID_CONFIGURATION
    }
```

