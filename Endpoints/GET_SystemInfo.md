
# GET /SystemInfo

#### Description
Retrieves information about the API Server and server environment

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/SystemInfo`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
None

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.
- `ERROR_RECORD_NOT_FOUND`: The requested System Info was not present. Restarting the server should regenerate the information

#### Sample Response Body

```
{
  "SystemInfo": {
    "SystemDBCreatedDateTime": "2015-05-19T13:36:51.3570000-04:00",
    "ServerLastStartedDateTime": "2015-05-20T09:36:58.8644532-04:00",
    "ServerCodeVersion": "1.0.0.0",
    "ServerOS": "Microsoft Windows NT 6.1.7601 Service Pack 1",
    "Is64bitOS": true,
    "ServerUser": "CORP\\mr185122"
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**SystemInfo object**

Element | Datatype | Description
------- | -------- | -----------
SystemDBCreatedDateTime | DateTime | The date and time the system database (sysadmin.sqlite) was created.
ServerLastStartedDateTime | DateTime | The date and time the API server was last started.
ServerCodeVersion | String | The version of code the API server is running.
ServerOS | String | The OS running on the server. You can find help to translate a windows version into well known releases [here](https://msdn.microsoft.com/library/windows/desktop/ms724832.aspx?f=255&MSPPError=-2147217396).
Is64bitOS | boolean | "True" if the server OS is a 64bit OS, "False" otherwise.
ServerUser | string | The windows user the API server process is running under.


