

# POST /Databases

#### Description
Adds one or more databases (companies) to the API Server. This makes the API Server aware of existing Counterpoint databases so it can access them for company level API calls. Using this endpoint, databases can either be added by providing a TLD and DB connection information, or by providing the path to a folder containing a companies.ini along with a list of company aliases in that file to add.

- Requires API Key: No
- Requires System Administrator: Yes
- Requires Counterpoint Registration option: No

#### Sample Request

**URI**

`POST https://localhost:81/Databases`

**Headers**
- `Authorization : Basic UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx`
- `Accept : application/json`

#### Parameters
Id: The Id of the Database to update information for.

**Request Body (adding by directly providing a TLD and DB info**
```
{
  "Databases": [
    {
      "Name": "QATESTGOLF",
      "TLD": "C:\\\\Program Files (x86)\\\\Radiant Systems\\\\CounterPoint\\\\CPSQL.85\\\\Toplevel",
      "DataSource": "127.0.0.1",
      "DB": "QATestGolf",
      "IntegratedSecurity": true,
      "Enabled": true
    },
    {
      "Name": "TESTGOLF",
      "TLD": "C:\\\\Program Files (x86)\\\\Radiant Systems\\\\CounterPoint\\\\CPSQL.1\\\\Toplevel",
      "DataSource": "127.0.0.1",
      "DB": "TestGolf",
      "IntegratedSecurity": false,
      "UserName": "sa",
      "Password": "password",
      "Enabled": true
    }
  ]
}
```

**Request Body (adding by providing a path to a companies.ini and company aliases**
```
{
  "IniPath": "C:\\\\Program Files (x86)\\\\Radiant Systems\\\\CounterPoint\\\\CPSQL.1\\\\Toplevel",
  "CompanyNames": [
    "QATESTGOLF",
    "TESTGOLF"
  ]
}
```

#### Request Body
Name | Parameter Type | Data Type | Required | Description
---- | -------------- | --------- | -------- | -----------
Databases | body | Array<Database> | false | A JSON structure containing an array of database records to add. If this is not provided, it is assumed that an IniPath and CompanyNames will be provided.
IniPath | body | string | false | The path to a folder containing a companies.ini from which companies should be added. If IniPath is provided, the CompanyNames parameter should be provided too.
CompanyNames | body | Array<String> | false | Required if IniPath parameter is provided. Provides a list of company aliases in the companies.ini file (which resides at the given IniPath) from which to add to the API server.

Database | Required | Field Description
------- | -------- | -----------------
Name | string | The alias/name for the database. This is the prefix used with the user name when making company level calls. It is recommended that this be identical to the company alias in companies.ini
TLD | string | The path (relative to the API server instance) to the TLD.
DataSource | string | The datasource name for the SQL server.
DB | string | The database name on the SQL server.
IntegratedSecurity | boolean | If true, the SQL server uses integrated security, and the windows credentials of the API server process will be used to connect to the SQL server. If false, SQL authentication will be used with the provided UserName.
UserName | string | When using SQL Authentication (non IntegratedSecurity), the UserName used for authentication to the SQL server.
Password | string | When using SQL Authentication (non IntegratedSecurity), the Password used for authentication to the SQL server.
Enabled | boolean | Specifies whether this database is accessible by the API server. If false, no company level calls to this database will be allowed.

#### Response Codes
- **<code>200 OK</code>** If at lease one database record was successfully added, 200 will be returned. You must look at the array of responses to get results for each individual company being added.
- **<code>401 Unauthorized</code>** The request could not be fulfilled. Likely due to a missing or invalid authorization header.
- **<code>500 Internal Server Error</code>** The request could not be fulfilled due to an unexpected internal error. This could be caused by a bug in the system, an unavailable database, or any other unexpected internal problem processing the request.
 
#### Error Codes
The following error codes may be returned from requests to this endpoint:
- `SUCCESS`: The request was successful and the customer information is present under the `SystemInfo` section of the response body.

#### Sample Response Body

```
{
  "AddDatabasesResults": [
    {
      "Result": "SUCCESS",
      "Id": 12,
      "Link": {
        "uri": "http://localhost:81/Databases/12",
        "method": "get"
      },
      "Message": "Added"
    }
  ],
  "ErrorCode": "SUCCESS"
}
```

#### Response Body

Array<AddDatabaseResults>

Element | Datatype | Description
------- | -------- | -----------
Result | string | The result code for the individual database record being added.
Id | int | The unqiue Id added to the database record.
Link | string | A uri that can be used to get the database record.
Method | string | The http verb that should be used to get the database record.
Message | string | A string describing the result of the add operation for the individual database record.



