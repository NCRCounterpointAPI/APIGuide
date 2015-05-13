# NCR Counterpoint API
The NCR Counterpoint API is a [REST](http://en.wikipedia.org/wiki/Representational_state_transfer) API server designed to be hosted on premises or in the cloud. It is built in pure .NET (C#) using the [ServiceStack](https://github.com/ServiceStack/ServiceStack/wiki) framework and uses [basic authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) using existing NCR Counterpoint user credentials. Some key features of the API are:
- Independent from Counterpoint code: The API has no runtime dependencies on Counterpoint, and thus can be installed on a non-Counterpoint machine. This also allows flexibility in forward and backward compatibility and ensures that API upgrades aren't dependent on Counterpoint upgrades.
- Multi-company capable: The API server can connect to multiple independent NCR Counterpoint companies from the same and or separate installs. As long as the API server has connectivity to a Counterpoint system, it can work with it.
- Multi-version capable: The API server is designed to work with multiple versions of Counterpoint systems simultaneously. The same server instance can work with an 8.4.6.12 company and an 8.5.0 company. The API server determines the version of Counterpoint its connected to by querying <code>DB_CTL.DB_VER</code> from the Counterpoint database, and executes the proper set of business rules for the target version of Counterpoint.
- Lightweight, simple, and performant: As much as possible, we hope to keep the API server small, simple, and high performance. As with any software, it will grow as functionality grows, but key design goals are simplicity and performance.

## Requirements
Any instance of the NCR Counterpoint API server can connect to multiple NCR Counterpoint installations and companies. In order for the server to work against an NCR Counterpoint company, the following requirements must be met:
* The NCR Counterpoint API server must be installed and running on an open http port.
* The NCR Counterpoint API server must have read/write access to the TLD folder for the company. This can be on a separate machine accessible via a UNC path.
* The NCR Counterpoint API server must have administrative access to the company database
* The company the server is connecting to must have the API user option enabled in its registration.ini file. There are some limited functions that will work without the API user option, but the bulk of the endpoints do require the registration option. See the documentation for an individual endpoint to determine if it requires the registration.ini option for use.
* Client applications or scripts using the API must provide a valid API Key, which is installed on the API Server, and included in the "APIKey" header for the request. See the page on [APIKeys](https://github.com/NCRCounterpointAPI/NCRCounterpointAPI/blob/master/APIKeys/APIKeys.md) for more information. There are some limited functions that will work without an API Key, but the bulk of the endpoints do require an API Key to be provided. See the documentation for an individual endpoint to determine if it requires an APIKey for use.

## Installation
In progress

## Configuration and Administration
In progress

## Company vs. System Administration requests
Due to the fact that a single API server can connect to mulitiple distinct NCR Counterpoint installations and companies, for security purposes there are some endpoints accessible only to system administrators, and others only accessible to company level users. See documentation on an individual endpoint to determine if system administrator or company level authorization is required.

System administrator logins are identifiable by the lack of a company name/alias prefix on their username. Upon install, there is a default system administrator with the username "admin", and the password (TBD). Users will be required to change the admin password upon their first login to the NCR Counterpoint API Management Console. Administrative functionality generally does not require an API Key or registration.ini option in order to be used.

## Common http Request elements
### Authorization
The NCR Counterpoint API uses standard http [basic authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) to validate NCR Counterpoint credentials in each call. Per basic authentication requirements, each call must contain an "Authorization" header in the following format:

`Authorization : Basic UUFUZXN0R29sZi5NR1I6UGFzc3dvcmQx`

The value after the word "Basic" is a base64 encoded (not encrypted) string containing the username and password of the NCR Counterpoint user for which the request is being submitted. For all company level requests, the company name/alias must be provided as a prefix to the user name in the format `<CompanyAlias>.<UserName>`. For instance, if my company alias is "QATestGolf", my Counterpoint user name is "MGR", and my Counterpoint password is "password1", I'll form the authentication string as such:

`QATestGolf.MGR:password1`

Base64 encoding the above string will yield "UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx", which is the string included in the sample Basic authentication example above.

**NOTE** Base64 encoding is not a form of encryption and does not provide security. All data included an an NCR Counterpoint API request and response is encrypted via the use of SSL, which provides the transport security. You can find a 3rd party website to experiment with base64 encoding and decoding [here](https://www.base64encode.org/).

If no authorization header is submitted with the request, or an invalid username or password is submitted, the request will fail with a `401 Unauthorized` http response.

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
## Endpoints

### System Administration Endpoints
Endpoint | Operations (Verbs) | Description
-------- | ------------------ | -----------
`/APIKey` | <code>GET</code> | Gets information on a single API Key.
`/APIKeys` | <code>GET</code> | Gets a list of all API Keys installed on the server.
`/Database` |  <code>GET</code><code>PUT</code><code>DELETE</code> | Manages the Databases the API is able to interact with (NCR Counterpoint Database and corresponding TLD).
`/Databases` | <code>GET</code><code>POST</code> | Manages the Databases the API is able to interact with in bulk.

### Company Endpoints
Endpoint | Operations (Verbs) | Description
-------- | ------------------ | -----------
`/Company` | <code>GET</code> | Gets information about the given company (from SY_COMP & DB_CTL).
`/Customer` |  [<code>GET</code>](https://github.com/NCRCounterpointAPI/NCRCounterpointAPI/blob/master/Endpoints/GET_Customer.md)<code>POST</code><code>PATCH</code><code>DELETE</code> | Methods to manager customer information.
`/Customer/{CustNo}/Address` | <code>GET</code><code>POST</code><code>PATCH</code><code>DELETE</code> | Methods to manage customer shipping addresses.
`/Customer/{CustNo}/Card` | <code>GET</code><code>POST</code><code>PATCH</code><code>DELETE</code> | Methods to manage customer cards on file.
`/Customer/{CustNo}/Note` | <code>GET</code><code>POST</code><code>PATCH</code><code>DELETE</code> | Methods to manage customer notes.
`/Customer/{CustNo}/OpenItems` | <code>GET</code> | Gets customer AR Open Item information.
`/CustomerControl` | <code>GET</code> | Gets customer control information.
`/Customers` | <code>GET</code> | Gets information on customers in bulk.
`/Customers/EC` | <code>GET</code> | Gets information on eCommerce customers in bulk.
`/Document` | <code>GET</code><code>POST</code> | Methods to add or edit documents (tickets).
`/Document/{DocId}/Contact` | <code>POST</code><code>PATCH</code><code>DELETE</code> | Methods to add or edit document contacts.
`/Document/{DocId}/Lines` | <code>POST</code> | Adds Lines to a document.
`/Document/{DocId}/Note` | <code>POST</code><code>PATCH</code><code>DELETE</code> | Methods to manage document notes.
`/Document/{DocId}/Payments` | <code>POST</code> | Adds Payments to a document.
`/EC` | <code>GET</code> | Gets eCommerce settings.
`/ECCategories` | <code>GET</code> | Gets eCommerce Categories and items.
`/GiftCard` | <code>GET</code> | Gets gift card information.
`/GiftCardCode` | <code>GET</code> | Gets gift card code information.
`/GiftCardCodes` | <code>GET</code> | Gets information on gift card codes in bulk.
`/GiftCards` | <code>GET</code> | Gets information of Gift Cards in bulk.
`/InventoryControl` | <code>GET</code> | Gets inventory control information.
`/Item` | <code>GET</code> | Methods to get item and item inventory information.
`/ItemCategories` | <code>GET</code> | Gets item Categories in bulk.
`/ItemCategory` | <code>GET</code> | Gets item category information.
`/Items` | <code>GET</code> | Gets item information in bulk.
`/PayCode` | <code>GET</code><code>PATCH</code> | Methods to manage PayCodes.
`/PayCodes` | <code>GET</code> | Gets information on Paycodes in bulk.
`/Store` | <code>GET</code> | Gets information on a store.
`/Store/{StoreId}/Station` | <code>GET</code> | Gets information on a station.
`/TaxCodes` | <code>GET</code> | Gets information on Tax Codes.
`/User` | <code>GET</code> | Gets information on a User.
`/Workgroup` | <code>GET</code> | Gets workgroup information.
