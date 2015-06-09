# NCR Counterpoint API
The NCR Counterpoint API is a [REST](http://en.wikipedia.org/wiki/Representational_state_transfer) API server designed to be hosted on premises or in the cloud. It is built in pure .NET (C#) using the [ServiceStack](https://github.com/ServiceStack/ServiceStack/wiki) framework and uses [basic authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) using existing NCR Counterpoint user credentials. Some key features of the API are:
- **Independent from Counterpoint code:** The API has no runtime dependencies on Counterpoint, and thus can be installed on a non-Counterpoint machine. This also allows flexibility in forward and backward compatibility and ensures that API upgrades aren't dependent on Counterpoint upgrades.
- **Multi-company capable:** The API server can connect to multiple independent NCR Counterpoint companies from the same and or separate installs. As long as the API server has connectivity to a Counterpoint system, it can work with it.
- **Multi-version capable:** The API server is designed to work with multiple versions of Counterpoint systems simultaneously. The same server instance can work with an 8.4.6.12 company and an 8.5.0 company. The API server determines the version of Counterpoint its connected to by querying <code>DB_CTL.DB_VER</code> from the Counterpoint database, and executes the proper set of business rules for the target version of Counterpoint.
- **Lightweight, simple, and performant:** As much as possible, we hope to keep the API server small, simple, and high performance. As with any software, it will grow as functionality grows, but key design goals are simplicity and performance.

## Requirements
Any instance of the NCR Counterpoint API server can connect to multiple NCR Counterpoint installations and companies. In order for the server to work against an NCR Counterpoint company, the following requirements must be met:
* The NCR Counterpoint API server must be installed and running on an open http port.
* The NCR Counterpoint API server must have read/write access to the TLD folder for the company. This can be on a separate machine accessible via a UNC path.
* The NCR Counterpoint API server must have administrative access to the company database
* The company the server is connecting to must have the API user option enabled in its registration.ini file. There are some limited functions that will work without the API user option, but the bulk of the endpoints do require the registration option. See the documentation for an individual endpoint to determine if it requires the registration.ini option for use.
* Most API calls require that client applications or scripts provide a valid "APIKey" header in each request. This APIKey must also be installed on the API Server. See the page on [APIKeys](APIKeys/APIKeys.md) for more information. There are some limited functions that will work without an API Key, but the bulk of the endpoints do require an API Key to be provided. See the documentation for an individual endpoint to determine if it requires an APIKey for use.

## Installation
Installation of the API Server is simple, you essentially just run the .msi to install. See the [Installing](InstallationAndConfiguration/Installing.md) page for more details.

## Configuration and Administration
In progress

### Testing
For ad hoc testing, we use and recommend the [Postman (Packaged app)](https://chrome.google.com/webstore/detail/postman-rest-client-packa/fhbjgbiflinjbdggehcddcbncdddomop?hl=en). It's a chrome web app that allows creating and saving REST requests. We're writing automated functional tests using Postman (and their $10 "Jetpacks" addon, which is well worth it). 

You can find all the automated tests we run for the API [here](https://github.com/NCRCounterpointAPI/APITests). They are written to run against a standard Counterpoint test database and TLD (coming soon). The tests are published not only as reference examples of API usage, but also in hopes the community will contribute to the test cases as well, to help reproduce bugs and improve test coverage. The preferable way to get an improvement to tests or documentation is for users to submit pull requests containing tests to illustrate issues or provide new test coverage. Please submit tests that will work against the standard test database and are structured similarly to our existing conventions.

## Making http requests
Calls to the API Server are made in the form of http requests. See the page on [API requests](Basics/Requests.md) for specifics on how to form http requests for the NCR Counterpoint API. See documentation on the language or script being used to make the request for details on how to properly create the request in your code.

## Working with http responses
Calls to the API Server issue http responses similarly to other REST APIs. See the page on [API responses](Basics/Responses.md) for specifics on how to work with http responses. See documentation on the language or script being used to handle the response for details on how to properly work with the response in your code.

## Endpoints
The endpoints below each represent individual REST API calls/requests that the API server supports. Each endpoint is either for system administrative functions or company functions, as categorized below. System administrative functions require a system username and password to be included in the Authorization header, while company functions require a counterpoint username (with a company prefix: <company>.<username>) and password to be submitted in the authorization header.

### System Administration Endpoints
Endpoint | Operation (Verb) | Description
-------- | ------------------ | -----------
`/APIKey` | [`GET`](Endpoints/GET_APIKey.md) | Gets information on a single API Key.
`/APIKeys` | [`GET`](Endpoints/GET_APIKeys.md) | Gets a list of all API Keys installed on the server.
`/Database/{Id}` | [`GET`](Endpoints/GET_Database.md) | Gets information about a Database (Company) configured for use by the API Server.
`/Database/{Id}` | [`PUT`](Endpoints/PUT_Database.md) | Updates information about a Database (Company) configured for use by the API Server.
`/Database/{Id}` | [`DELETE`](Endpoints/DELETE_Database.md) | Deletes a Database (Company) so it can no longer be used by the API Server.
`/Databases` | [`GET`](Endpoints/GET_Databases.md) | Gets a list of all Databases (Companies) the API is able to interact with.
`/Databases` | [`POST`](Endpoints/POST_Databases.md) | Adds one or more Databases (Companies) the API can interact with.
`/Databases/ini` | [`GET`](Endpoints/GET_Databases_Ini.md) | Gets a list of company DB information from a companies.ini file
`/SystemInfo` | [`GET`](Endpoints/GET_SystemInfo.md) | Gets information about the API server and hardware environment.

### Company Endpoints
Endpoint | Operation (Verb) | Description
-------- | ------------------ | -----------
`/Company` | [`GET`](Endpoints/GET_Company.md) | Gets information about the given company (from SY_COMP & DB_CTL).
`/Customer` | [`POST`](Endpoints/POST_Customer.md) | Adds a new customer record.
`/Customer/{CustNo}` | [`GET`](Endpoints/GET_Customer.md) | Gets information about a customer.
`/Customer/{CustNo}` |  `PATCH` | Updates information about a customer.
`/Customer/{CustNo}/Address` | `GET` | Gets customer shipping addresses.
`/Customer/{CustNo}/Address` | `POST` | Adds a new shipping address to an existing customer.
`/Customer/{CustNo}/Address` | `PATCH` | Updates an existing shipping address for an existing customer.
`/Customer/{CustNo}/Address` | `DELETE` | Deletes a shipping address from an existing customer.
`/Customer/{CustNo}/Card` | `GET` | Gets credit cards on file for an existing customer.
`/Customer/{CustNo}/Card` | `POST` | Adds a credit card on file to an existing customer.
`/Customer/{CustNo}/Card` | `PATCH` | Updates an existing credit card on file for an existing customer.
`/Customer/{CustNo}/Card` | `DELETE` | Deletes a credit card on file for an exsitng customer.
`/Customer/{CustNo}/Note` | `GET` | Gets customer notes for a given customer.
`/Customer/{CustNo}/Note` | `POST` | Adds a new note to an existing customer.
`/Customer/{CustNo}/Note` | `PATCH` | Updates an existing note on an existing customer.
`/Customer/{CustNo}/Note` | `DELETE` | Deletes a note from an existing customer.
`/Customer/{CustNo}/OpenItems` | `GET` | Gets customer AR Open Item information.
`/CustomerControl` | `GET` | Gets customer control information.
`/Customers` | `GET` | Gets information on customers in bulk.
`/Customers/EC` | `GET` | Gets information on eCommerce customers in bulk.
`/Document` | `POST` | Adds a new document (ticket).
`/Document/{DocId}` | `GET` | Gets information on an existing document (ticket) that hasn't been posted yet.
`/Document/{DocId}/Contact` | `POST` | Adds a contact to an existing document.
`/Document/{DocId}/Contact` | `PATCH` | Updates a contact on an existing document.
`/Document/{DocId}/Contact` | `DELETE` | Deletes a contact from an existing document.
`/Document/{DocId}/Lines` | `POST` | Adds Lines to a document.
`/Document/{DocId}/Note` | `POST` | Adds a note to an existing document.
`/Document/{DocId}/Note` | `PATCH` | Updates a note on an existing document.
`/Document/{DocId}/Note` | `DELETE` | Deletes a note from an existing document.
`/Document/{DocId}/Payments` | `POST` | Adds Payments to a document.
`/EC` | `GET` | Gets eCommerce settings.
`/ECCategories` | `GET` | Gets eCommerce Categories and items.
`/GiftCard/{GiftCardNo}` | `GET` | Gets gift card information.
`/GiftCardCode/{GiftCardCode}` | `GET` | Gets gift card code information.
`/GiftCardCodes` | `GET` | Gets information on gift card codes in bulk.
`/GiftCards` | `GET` | Gets information of Gift Cards in bulk.
`/InventoryControl` | `GET` | Gets inventory control information.
`/Item/{ItemNo}` | `GET` | Methods to get item and item inventory information.
`/Item/{ItemNo}/Images` | `GET` | Gets a list of available item images for a given item.
`/Item/{ItemNo}/Images/{Filename} ` | `GET` | Gets an item image for the given item and filename.
`/Item/{ItemNo}/Inventory/{LocId}` | `GET` | Gets item inventory information for a given item and location.
`/Item/Inventory/EC` | `GET` | Gets eCommerce inventory information for all eCommerce items.
`/ItemCategories` | `GET` | Gets item Categories in bulk.
`/ItemCategory/{CategoryCode}` | `GET` | Gets item category information for the given category code.
`/Items` | `GET` | Gets item information in bulk.
`/PayCode/{Paycode}` | `GET` | Gets information about a given Paycode.
`/PayCode/{Paycode}` | `PATCH` | Updates information about a Paycode.
`/PayCodes` | `GET` | Gets information on Paycodes in bulk.
`/Store/{StoreId}` | `GET` | Gets information on a store.
`/Store/{StoreId}/Station` | `GET` | Gets information on a station.
`/TaxCodes` | `GET` | Gets information on Tax Codes.
`/User/{UserId}` | [`GET`](Endpoints/GET_User.md) | Gets information on a User.
`/Workgroup/{WorkgroupId}` | [`GET`](Endpoints/GET_Workgroup.md) | Gets workgroup information.
