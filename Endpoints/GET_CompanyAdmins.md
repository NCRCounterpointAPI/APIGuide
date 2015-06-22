
# GET /CompanyAdmins

#### Description

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/CompanyAdmins/{CompanyName}`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
**CompanyName**: The Company Name to retrieve information for.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the list of admins is present under the `CompanyAdmins` section of the response body.
- Company not found - Add?

#### Sample Response Body

```
{
  "CompanyAdmins": [
    "Dev3",
    "MGR",
    "Person1",
    "User2"
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**User List**

Element | Datatype | Description
------- | -------- | -----------
CompanyAdmins | String List | A list of users who have the Company Admin assigned.
