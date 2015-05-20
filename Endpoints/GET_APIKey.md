
# GET /APIKey

#### Description

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/APIKey/{APIKey}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
**APIKey**: The APIKey to retrieve information for.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `APIKey` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested APIKey was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "APIKey": {
    "DevID": "f7f5bdb1-4dc8-4844-a5e1-f57b885e1b65",
    "DevName": "Hall of Justice",
    "IssuedTo": "Clark Kent",
    "eMail1": "Clark.Kent@HallofJustice.com",
    "eMail2": "Bruce.Wayne@HallofJustice.com",
    "AppID": "ee51f0f2-1d1c-4b02-a428-013833b1575d",
    "AppName": "Test Key",
    "AppDescription": "Clark's test key",
    "expiration": "2017-05-06T00:00:00.0000000"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**APIKey object**

Element | Datatype | Description
------- | -------- | -----------
DevID | String/Guid | A unqiue Guid identifying the company/3rd party developer the key is issued to.
DevName | String | The name of the company/3rd party developer the key is issued to.
IssuedTo | String | The name of the person the key was issued to.
eMail1 | String | The primary eMail address of the key owner. This email will be used to notify the 3rd party of pending APIKey expirations and other relevant events.
eMail2 | String | A backup eMail address of the key owner. Ideally this is a different individual to ensure any emails. regarding pending APIKey expirations will be received by the 3rd party developer.
AppID | String/Guid | A unique Guid identifying the application/use case using this APIKey.
AppName | String | The name of the application/use case using this APIKey.
AppDescription | String | A brief description of the application using this APIKey.
expiration | DateTime | The expiration Date of the APIKey. After the key expires, requests made using this APIKey will cease to function.


