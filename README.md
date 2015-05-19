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
* Client applications or scripts using the API must provide a valid API Key, which is installed on the API Server, and included in the "APIKey" header for the request. See the page on [APIKeys](https://github.com/NCRCounterpointAPI/NCRCounterpointAPI/blob/master/APIKeys/APIKeys.md) for more information. There are some limited functions that will work without an API Key, but the bulk of the endpoints do require an API Key to be provided. See the documentation for an individual endpoint to determine if it requires an APIKey for use.

## Installation
In progress

## Configuration and Administration
In progress

### Testing
For ad hoc testing, we use and recommend the [Postman (Packaged app)](https://chrome.google.com/webstore/detail/postman-rest-client-packa/fhbjgbiflinjbdggehcddcbncdddomop?hl=en). It's a chrome web app that allows creating and saving REST requests. We're writing automated functional tests using Postman (and their $10 "Jetpacks" addon, which is well worth it). We plan on sharing our Postman tests via GitHub in the future as well so the community can see what we test, use our tests, and contribute to our tests.

## Making http requests
Calls to the API Server are made in the form of http requests. See the page on [API requests](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/Basics/Requests.md) for specifics on how to form http requests for the NCR Counterpoint API. See documentation on the language or script being used to make the request for details on how to properly create the request in your code.

## Working with http responses
Calls to the API Server issue http responses similarly to other REST APIs. See the page on [API responses](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/Basics/Responses.md) for specifics on how to work with http responses. See documentation on the language or script being used to handle the response for details on how to properly work with the response in your code.

### System Administration Endpoints
Endpoint | Operations (Verbs) | Description
-------- | ------------------ | -----------
`/APIKey` | `GET` | Gets information on a single API Key.
`/APIKeys` | `GET` | Gets a list of all API Keys installed on the server.
`/Database` |  `GET` `PUT` `DELETE` | Manages the Databases the API is able to interact with (NCR Counterpoint Database and corresponding TLD).
`/Databases` | `GET` `POST` | Manages the Databases the API is able to interact with in bulk.
`/Databases/ini` | `GET` | Gets a list of company DB information from a companies.ini file
`/SystemInfo` | `GET` | Gets information about the API server and hardware environment.

### Company Endpoints
Endpoint | Operations (Verbs) | Description
-------- | ------------------ | -----------
`/Company` | `GET` | Gets information about the given company (from SY_COMP & DB_CTL).
`/Customer` |  [`GET`](https://github.com/NCRCounterpointAPI/NCRCounterpointAPI/blob/master/Endpoints/GET_Customer.md) [`POST`](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/Endpoints/POST_Customer.md) `PATCH` | Methods to manage customer information.
`/Customer/{CustNo}/Address` | `GET` `POST` `PATCH` `DELETE` | Methods to manage customer shipping addresses.
`/Customer/{CustNo}/Card` | `GET` `POST` `PATCH` `DELETE` | Methods to manage customer cards on file.
`/Customer/{CustNo}/Note` | `GET` `POST` `PATCH` `DELETE` | Methods to manage customer notes.
`/Customer/{CustNo}/OpenItems` | `GET` | Gets customer AR Open Item information.
`/CustomerControl` | `GET` | Gets customer control information.
`/Customers` | `GET` | Gets information on customers in bulk.
`/Customers/EC` | `GET` | Gets information on eCommerce customers in bulk.
`/Document` | `GET` `POST` | Methods to add or edit documents (tickets).
`/Document/{DocId}/Contact` | `POST` `PATCH` `DELETE` | Methods to add or edit document contacts.
`/Document/{DocId}/Lines` | `POST` | Adds Lines to a document.
`/Document/{DocId}/Note` | `POST` `PATCH` `DELETE` | Methods to manage document notes.
`/Document/{DocId}/Payments` | `POST` | Adds Payments to a document.
`/EC` | `GET` | Gets eCommerce settings.
`/ECCategories` | `GET` | Gets eCommerce Categories and items.
`/GiftCard` | `GET` | Gets gift card information.
`/GiftCardCode` | `GET` | Gets gift card code information.
`/GiftCardCodes` | `GET` | Gets information on gift card codes in bulk.
`/GiftCards` | `GET` | Gets information of Gift Cards in bulk.
`/InventoryControl` | `GET` | Gets inventory control information.
`/Item` | `GET` | Methods to get item and item inventory information.
`/ItemCategories` | `GET` | Gets item Categories in bulk.
`/ItemCategory` | `GET` | Gets item category information.
`/Items` | `GET` | Gets item information in bulk.
`/PayCode` | `GET` `PATCH` | Methods to manage PayCodes.
`/PayCodes` | `GET` | Gets information on Paycodes in bulk.
`/Store` | `GET` | Gets information on a store.
`/Store/{StoreId}/Station` | `GET` | Gets information on a station.
`/TaxCodes` | `GET` | Gets information on Tax Codes.
`/User` | `GET` | Gets information on a User.
`/Workgroup` | `GET` | Gets workgroup information.
