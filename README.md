# NCR Counterpoint API
The NCR Counterpoint API is a [REST](http://en.wikipedia.org/wiki/Representational_state_transfer) API server designed to be hosted on premises or in the cloud. It is built in pure .NET (C#) using the [ServiceStack](https://github.com/ServiceStack/ServiceStack/wiki) framework and uses [basic authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) using existing NCR Counterpoint user credentials. Some key features of the API are:
- Independent from Counterpoint code: The API has no runtime dependencies on Counterpoint, and thus can be installed on a non-Counterpoint machine. This also allows flexibility in forward and backward compatibility and ensures that API upgrades aren't dependent on Counterpoint upgrades.
- Multi-company capable: The API server can connect to multiple independent NCR Counterpoint companies from the same and or separate installs. As long as the API server has connectivity to a Counterpoint system, it can work with it
- Multi-version capable: The API server is designed to work with multiple versions of Counterpoint systems simultaneously. The same server instance can work with an 8.4.6.12 company and an 8.5.0 company. The API server determines the version of Counterpoint its connected to by querying <code>DB_CTL.DB_VER</code> from the Counterpoint database, and executes the proper set of business rules for the target version of Counterpoint.
- Lightweight, simple, and performant: As much as possible, we hope to keep the API server small, simple, and high performance. As with any software, it will grow as functionality grows, but key design goals are simplicity and performance.

## Requirements
Any instance of the NCR Counterpoint API server can connect to multiple NCR Counterpoint installations and companies. In order for the server to work against an NCR Counterpoint company, the following requirements must be met:
* The NCR Counterpoint API server must be installed and running on an open http port
* The NCR Counterpoint API server must have read/write access to the TLD folder for the company. This can be on a separate machine accessible via a UNC path
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

The value after the word "Basic" is a base64 encoded (not encrypted) string containing the username and password of the NCR Counterpoint user for which the request is being submitted. For all company level requests, the company name/alias must be provided as a prefix to the user name in the format <CompanyAlias>.<UserName>. For instance, if my company alias is "QATestGolf", my Counterpoint user name is "MGR", and my Counterpoint password is "password1", I'll form the authentication string as such:

`QATestGolf.MGR:password1`

Base64 encoding the above string will yield "UUFUZXN0R29sZi5NR1I6cGFzc3dvcmQx", which is the string included in the sample Basic authentication example above.

**NOTE** Base64 encoding is not a form of encryption and does not provide security. All data included an an NCR Counterpoint API request and response is encoded via the use of SSL. You can find a 3rd party website to experiment with base64 encoding and decoding [here](https://www.base64encode.org/).

If no authorization header is submitted with the request, or an invalid username or password is submitted, the request will fail with a `401 Invalid username or password` http response.

## Common http Response codes

## Endpoints

### System Administration Endpoints
- `/APIKey` <code>GET</code>
- `/APIKeys` <code>GET</code>
- `/Database` <code>GET</code><code>POST</code><code>PATCH</code><code>DELETE</code>
- `/Databases` <code>GET</code>

### Company Endpoints
- `/Company` <code>GET</code>
- `/Customer` <code>GET</code><code>POST</code><code>PATCH</code><code>DELETE</code>
- `/CustomerControl` <code>GET</code>
- `/Customers` <code>GET</code>
- `/Document` <code>GET</code><code>POST</code><code>PATCH</code>
- `/EC` <code>GET</code>
- `/ECCategories` <code>GET</code>
- `/GiftCard` <code>GET</code>
- `/GiftCardCode` <code>GET</code>
- `/GiftCardCodes` <code>GET</code>
- `/GiftCards` <code>GET</code>
- `/InventoryControl` <code>GET</code>
- `/Item` <code>GET</code>
- `/ItemCategories` <code>GET</code>
- `/ItemCategory` <code>GET</code>
- `/Items` <code>GET</code>
- `/PayCode` <code>GET</code>
- `/PayCodes` <code>GET</code>
- `/Store` <code>GET</code>
- `/TaxCodes` <code>GET</code>
- `/User` <code>GET</code>
- `/Workgroup` <code>GET</code>
