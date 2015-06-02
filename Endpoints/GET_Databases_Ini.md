
# GET /Databases/ini

#### Description
Gets a list of all database aliases defined in the given companies.ini file.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`GET https://localhost:81/Databases/ini?inipath=C:\Program Files (x86)\Radiant Systems\CounterPoint\CPSQL.1\Toplevel`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
inipath: The path (relative to the API Server process) to a folder containing a companies.ini file. This path can be local or a UNC path.

#### Response Codes
- **<code>200 OK</code>** The request was successful, the result of the call will be in the response body.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.

#### Sample Response Body

```
{
  "DatabaseNames": [
    "QATESTSECUREPAY",
    "TESTGOLF"
  ],
  "Databases": [
    {
      "Name": "QATESTSECUREPAY",
      "TLD": "C:\\\\Program Files (x86)\\\\Radiant Systems\\\\CounterPoint\\\\CPSQL.1\\\\Toplevel",
      "DataSource": "127.0.0.1",
      "DB": "QATestsecurePay",
      "IntegratedSecurity": true,
      "Enabled": false
    },
    {
      "Name": "TESTGOLF",
      "TLD": "C:\\\\Program Files (x86)\\\\Radiant Systems\\\\CounterPoint\\\\CPSQL.1\\\\Toplevel",
      "DataSource": "127.0.0.1",
      "DB": "TestGolf",
      "IntegratedSecurity": false,
      "UserName": "sa",
      "Enabled": false
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

Element | Datatype | Description
------- | -------- | -----------
DatabaseNames | Array<String> | An array of database names (aliases) found in the Companies.ini file. 
Databases | Array<Database> | An array of database records found in the Companies.ini file.

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

