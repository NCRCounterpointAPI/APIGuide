# Elements of an http Request for the NCR Counterpoint API
The NCR Counterpoint API utilizes http requests similarly to other REST APIs. The table below shows the elements in a standard http request, and describes their general use in the NCR Counterpoint API. See documentation on individual endpoints for specifics of what elements are required for a given request:

Request element | Sample | Description
--------------- | ------ | -----------
Endpoint | `/Customer/{CustNo}` | This is the core endpoint path that indicates the resource or action you are interacting with. Together with the domain, this forms the URI submitted in the request. Elements in curly braces are path parameters which should be subsituted with the proper value. An example of a final URI would be: `https://localhost:81/Customers/1000`.
Verb | `GET` `POST` `PATCH` `PUT` `DELETE` | Http verbs are used to specify the type of action being taken on a resource. In general, `GET` indicates a select/read of a resource, `POST` is an add/insert of a resource, `PATCH` indicates a partial update of an existing resource, `PUT` indicates a full update of an existing resource, and `DELETE` indicates a deletion/removal of an existing resource.
URI parameters | `?{name1}={value1}&{name2=value2}` | URI parameters are generally used to provide additional information to a call. Typically this would be things such as paging information (if an endpoint supported data paging) or filter criteria. The question mark is used to separate URI parameters from the rest of the URI, and ampersands are used to separate the name/value pairs of multiple parameters.
Headers | `{name} : {value}` | Http headers are name value pairs submitted with each request. In the NCR Counterpoint API, these are typically used to provide additional, relevant content to the call. All calls to the API will require a basic authentication header to be included, and most calls will require a valid [APIKeys](https://github.com/NCRCounterpointAPI/NCRCounterpointAPI/blob/master/APIKeys/APIKeys.md) header to be included. See additional information on headers below.
Request Body |  | The request body is only present when the http verb is `POST`, `PUT`, or `PATCH`. It contains the payload containing the information to be added or updated. This is typically a JSON structured string. 

## Company vs. System Administration requests
Due to the fact that a single API server can connect to mulitiple distinct NCR Counterpoint installations and companies, for security purposes there are some endpoints accessible only to system administrators, and others only accessible to company level users. See documentation on an individual endpoint to determine if system administrator or company level authorization is required.

System administrator logins are identifiable by the lack of a company name/alias prefix on their username. Upon install, there is a default system administrator with the username "admin", and the password (TBD). Users will be required to change the admin password upon their first login to the NCR Counterpoint API Management Console. Administrative functionality generally does not require an API Key or registration.ini option in order to be used.

## Authorization
The NCR Counterpoint API uses standard http [basic authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) to validate NCR Counterpoint credentials in each call. Per basic authentication requirements, each call must contain an "Authorization" header in the following format:

`Authorization : Basic UUFUZXN0R29sZi5NR1I6UGFzc3dvcmQx`

The value after the word "Basic" is a base64 encoded (not encrypted) string containing the username and password of the NCR Counterpoint user for which the request is being submitted. For all company level requests, the company name/alias must be provided as a prefix to the user name in the format `<CompanyAlias>.<UserName>`. For instance, if my company alias is "QATestGolf", my Counterpoint user name is "MGR", and my Counterpoint password is "password1", I'll form the authentication string as such:

`QATestGolf.MGR:password1`

Base64 encoding the above string will yield "UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx", which is the string included in the sample Basic authentication example above.

**NOTE** Base64 encoding is not a form of encryption and does not provide security. All data included an an NCR Counterpoint API request and response is encrypted via the use of SSL, which provides the transport security. You can find a 3rd party website to experiment with base64 encoding and decoding [here](https://www.base64encode.org/).

If no authorization header is submitted with the request, or an invalid username or password is submitted, the request will fail with a `401 Unauthorized` http response.

## API Keys
Most calls require a valid API Key to be provided in the headers of the request. See documentation on specific endpoints to determine if an API Key is required. See the page on [APIKeys](https://github.com/NCRCounterpointAPI/NCRCounterpointAPI/blob/master/APIKeys/APIKeys.md) for more information.

## Content-Type header
The `Content-Type` header is a standard http header that describes the type of data being provided in the request body (if present). All testing on the NCR Counterpoint API is done using JSON data, so for `POST`, `PUT`, and `PATCH` requests, the following header should be included:
`Content-Type : application/json'

## Accept header
The `Accept` header is another standard http header that descripts the format of the data that should be returned in the response. Again, all testing on the NCR Counterpoint API is done using JSON data. If this header is not present in a request, then `Accept : application/json` is assumed.

## Working with Dates and Times
The NCR Counterpoint API server uses dates in the [ISO8601](http://en.wikipedia.org/wiki/ISO_8601) date format, as it is human readable, sortable, and increasingly considered the standard way to express dates on the web. Dates will be provided in the format 

`YYYY-MM-DDTHH:MM:SS.SSSSSSS`

such as:

`2006-03-19T00:00:00.0000000`

When submitting dates and times in a request, the same format should be used. If only a date is needed, the time portion can be left off. Similarly, the precision of the seconds can be shortened if it isn't needed. If only a time is needed, and no date, the date portion will be ignored (but must be provided).

## Caching
Certain data that is assumed to be relatively static is cached by the server after it's intially read. See the page on caching for more information. To force the server to reload data, the `ServerCache` header can be used:

`ServerCache: no-cache

The following data is cached for 24 hours from the point it's intially loaded. No data is preloaded, it is all lazily loaded upon the first request for the data:

- Company
- Customer Control
- Databases
- eCommerce Control
- eCommerce Categories
- Gift Card Codes
- Inventory Control
- Item Categories
- Items (not inventory information
- PayCodes
- Stores
- Stations
- Tax Codes
- Workstations

**NOTE:** When resources are added through the server (such as a POST to /Database), the cache is automatically updated with the new information, since the server is aware of the change. The cache typically will become stale when changes are made to the TLD or Counterpoint database that don't go through the API.

There are three ways to force the cache to be updated:
- Restart the NCR Counterpoint API server
- Issue a DELETE request to the /CACHE endpoint: All data cached for the company indicated in the authentication header will be invalidated and reloaded upon the next request for that data.
- Include a `need name` header in the request. This will invalidate all cached data for the company indicated in the authentication header. All data will be reloaded upon the next request for that data.
More to come...

