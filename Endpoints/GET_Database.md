
# GET /Database/{Id}

#### Description
Gets information about a given Database

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/Database/1`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Id: The Id of the Database to retrieve information for.

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
  "Database": {
    "Id": 1,
    "Name": "QATESTGOLF",
    "TLD": "C:\\\\Program Files (x86)\\\\Radiant Systems\\\\CounterPoint\\\\CPSQL.85\\\\Toplevel",
    "DataSource": "127.0.0.1",
    "DB": "QATestGolf",
    "IntegratedSecurity": true,
    "Enabled": true
  },
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

**Database object**

Element | Datatype | Description
------- | -------- | -----------
Id | int | A unique Id for the database in this system.
Name | string | The alias/name for the database. This is the prefix used with the user name when making company level calls. It is recommended that this be identical to the company alias in companies.ini
TLD | string | The path (relative to the API server instance) to the TLD.
DataSource | string | The datasource name for the SQL server.
DB | string | The database name on the SQL server.
IntegratedSecurity | boolean | If true, the SQL server uses integrated security, and the windows credentials of the API server process will be used to connect to the SQL server. If false, SQL authentication will be used with the provided UserName. The Password is not returned in a "GET" call for security purposes.
UserName | string | When using SQL Authentication (non IntegratedSecurity), the UserName used for authentication to the SQL server.
Enabled | boolean | Specifies whether this database is accessible by the API server. If false, no company level calls to this database will be allowed.



