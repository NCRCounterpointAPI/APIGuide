# NCR Counterpoint API
The NCR Counterpoint API is a [REST](http://en.wikipedia.org/wiki/Representational_state_transfer) API server designed to be hosted on premises or in the cloud. It is built in pure .NET (C#) using the [ServiceStack](https://github.com/ServiceStack/ServiceStack/wiki) framework and uses [basic authentication](http://en.wikipedia.org/wiki/Basic_access_authentication) using existing NCR Counterpoint user credentials. Some key features of the API are:
- **Independent from Counterpoint code:** The API has no runtime dependencies on Counterpoint, and thus can be installed on a non-Counterpoint machine. This also allows flexibility in forward and backward compatibility and ensures that API upgrades aren't dependent on Counterpoint upgrades.
- **Multi-company capable:** The API server can connect to multiple independent NCR Counterpoint companies from the same and or separate installs. As long as the API server has connectivity to a Counterpoint system, it can work with it.
- **Multi-version capable:** The API server is designed to work with multiple versions of Counterpoint systems simultaneously. The same server instance can work with an 8.4.6.12 company and an 8.5.0 company. The API server determines the version of Counterpoint its connected to by querying <code>DB_CTL.DB_VER</code> from the Counterpoint database, and executes the proper set of business rules for the target version of Counterpoint.
- **Lightweight, simple, and performant:** As much as possible, we hope to keep the API server small, simple, and high performance. As with any software, it will grow as functionality grows, but key design goals are simplicity and performance.

## Requirements
Any instance of the NCR Counterpoint API server can connect to multiple NCR Counterpoint installations and companies. In order for the server to work against an NCR Counterpoint company, the following requirements must be met:
* Windows 7 (desktop OS) or Windows Server 2012 R2 (server OS) or newer.
* .NET 4.5.2
* 4GB RAM Minimum (8GB recommended)
* The NCR Counterpoint API server must be installed and running on an open http port.
* The NCR Counterpoint API server must have read/write access to the TLD folder for the company. This can be on a separate machine accessible via a UNC path.
* The NCR Counterpoint API server must have administrative access to the company database.
* The NCR Counterpoint API does not support offline databases.
* The company the server is connecting to must have the API user option enabled in its registration.ini file. There are some limited functions that will work without the API user option, but the bulk of the endpoints do require the registration option. See the documentation for an individual endpoint to determine if it requires the registration.ini option for use.
* Most API calls require that client applications or scripts provide a valid "APIKey" header in each request. This APIKey must also be installed on the API Server. See the page on [APIKeys](InstallationAndConfiguration/Licensing.md) for more information. There are some limited functions that will work without an API Key, but the bulk of the endpoints do require an API Key to be provided. See the documentation for an individual endpoint to determine if it requires an APIKey for use.

## Installation
Installation of the API Server is simple, you essentially just run the .msi to install. See the [Installing](InstallationAndConfiguration/Installing.md) page for more details.

## Configuration and Administration
The API server allows fine grained configuring over the companies, users, and API calls each user can make. See the [Configuring the NCR Counterpoint API Server](InstallationAndConfiguration/Configuring.md) page for information on how to configure the server properly for your environment.

## API Keys and licensing
Most, but not all calls to the API will require a free API License key (for the client application or script), and a paid registration.ini option for the Counterpoint merchant. The endpoint chart below indicates which endpoints require each piece of data. See the [API Keys and licensing page](InstallationAndConfiguration/Licensing.md) for more details.

## Functionality and Testing
Automated testing is used to validate the operation and accuracy of the API calls. It is highly recommended that consumers of the API review the automated tests to ensure the API provides the needed capabilities. In short, if it's not covered by our automated tests, there's no guarantee that a given usage of the API will continue to work as expected. 

## Reporting defects
To report a defect in the API, an automated test that illustrates the defect, using Postman, is required to be submitted as a pull request to our API Tests project. The test should follow the structure of the other tests in the repository as closely as possible. Hardcoded values may be used if needed. NCR will use your test case to reproduce the issue. If NCR deems the issue to be a defect, it will be resolved and the test will be added to our test suites (the test may be modified to better fit our structure, etc.). This method ensures we build a robust automated test suite, and ensures that your needed functionality is always tested and ensured to work in future releases of the API.

In addition, if there is a usage of the API that is working as expected, but not yet covered by an automated test, and you want to ensure it continues to work as expected, you should submit a pull request with an automated test case for us to consider including in the test suite.

We use and recommend the [Postman (Packaged app)](https://chrome.google.com/webstore/detail/postman-rest-client-packa/fhbjgbiflinjbdggehcddcbncdddomop?hl=en). It's a chrome web app that allows creating and saving REST requests. We also recommend the "Jetpacks" addon, which is very affordable and allows automated test scripting. These tools are required to create and submit additional test cases to NCR.

You can find all the automated tests we run for the API [here](https://github.com/NCRCounterpointAPI/APITests). They are written to run against a standard Counterpoint test database and TLD (coming soon). The tests are published not only as reference examples of API usage, but also in hopes the community will contribute to the test cases as well, to help reproduce bugs and improve test coverage. The preferable way to get an improvement to tests or documentation is for users to submit pull requests containing tests to illustrate issues or provide new test coverage. Please submit tests that will work against the standard test database and are structured similarly to our existing conventions.

## Making http requests
Calls to the API Server are made in the form of http requests. See the page on [API requests](Basics/Requests.md) for specifics on how to form http requests for the NCR Counterpoint API. See documentation on the language or script being used to make the request for details on how to properly create the request in your code.

## Working with http responses
Calls to the API Server issue http responses similarly to other REST APIs. See the page on [API responses](Basics/Responses.md) for specifics on how to work with http responses. See documentation on the language or script being used to handle the response for details on how to properly work with the response in your code.

## Endpoints
The endpoints below each represent individual REST API calls/requests that the API server supports. Each endpoint is either for system administrative functions or company functions, as categorized below. System administrative functions require a system username and password to be included in the Authorization header, while company functions require a counterpoint username (with a company prefix: <company>.<username>) and password to be submitted in the authorization header.

### System Administration Endpoints
Endpoint | Operation (Verb) | APIKey | CP Registration | Description
-------- | ---------------- | ------ | --------------- | -----------
`/APIKey` | [`GET`](Endpoints/GET_APIKey.md) | | | Gets information on a single API Key.
`/APIKeys` | [`GET`](Endpoints/GET_APIKeys.md) | | |  Gets a list of all API Keys installed on the server.
`/CompanyAdmin/{CompanyName}/{AdminUser}` | [`DELETE`](Endpoints/DELETE_CompanyAdmin.md) | | | Delete a company admin by user id.
`CompanyAdmins/{CompanyName}` | [`GET`](Endpoints/GET_CompanyAdmins.md) | | | Gets a list of Company Admins for the company.
`CompanyAdmins/{CompanyName}` | [`POST`](Endpoints/POST_CompanyAdmins.md) | | | Adds a list of Company Admins.
`CompanyAdmins/{CompanyName}` | [`PUT`](Endpoints/PUT_CompanyAdmins.md) | | | Sets a list of Company Admins for the company.
`/Database/{Id}` | [`GET`](Endpoints/GET_Database.md) | | |  Gets information about a Database (Company) configured for use by the API Server.
`/Database/{Id}` | [`PUT`](Endpoints/PUT_Database.md) | | |  Updates information about a Database (Company) configured for use by the API Server.
`/Database/{Id}` | [`DELETE`](Endpoints/DELETE_Database.md) | | |  Deletes a Database (Company) so it can no longer be used by the API Server.
`/Databases` | [`GET`](Endpoints/GET_Databases.md) | | |  Gets a list of all Databases (Companies) the API is able to interact with.
`/Databases` | [`POST`](Endpoints/POST_Databases.md) | | |  Adds one or more Databases (Companies) the API can interact with.
`/Databases/ini` | [`GET`](Endpoints/GET_Databases_Ini.md) | | |  Gets a list of company DB information from a companies.ini file
`/SystemInfo` | [`GET`](Endpoints/GET_SystemInfo.md) | | |  Gets information about the API server and hardware environment.
`/Users/{CompanyName}` | [`GET`](Endpoints/GET_UsersForCompany.md) | | |  Gets a list of users for the company.

### Company Endpoints
Endpoint | Operation (Verb) | APIKey | CP Registration |  Description
-------- | ---------------- | ------ | --------------- |  -----------
`/Company` | [`GET`](Endpoints/GET_Company.md) | X | X | Gets information about the given company (from SY_COMP & DB_CTL).
`/Customer` | [`POST`](Endpoints/POST_Customer.md) | X | X | Adds a new customer record.
`/Customer/{CustNo}` | [`GET`](Endpoints/GET_Customer.md) | X | X | Gets information about a customer.
`/Customer/{CustNo}` |  `PATCH` | X | X | Updates information about a customer.
`/Customer/{CustNo}/Address` | `GET` | X | X | Gets customer shipping addresses.
`/Customer/{CustNo}/Address` | `POST` | X | X | Adds a new shipping address to an existing customer.
`/Customer/{CustNo}/Address` | `PATCH` | X | X | Updates an existing shipping address for an existing customer.
`/Customer/{CustNo}/Address` | `DELETE` | X | X | Deletes a shipping address from an existing customer.
`/Customer/{CustNo}/Card` | `GET` | X | X | Gets credit cards on file for an existing customer.
`/Customer/{CustNo}/Card` | `POST` | X | X | Adds a credit card on file to an existing customer.
`/Customer/{CustNo}/Card` | `PATCH` | X | X | Updates an existing credit card on file for an existing customer.
`/Customer/{CustNo}/Card` | `DELETE` | X | X | Deletes a credit card on file for an existing customer.
`/Customer/{CustNo}/Note` | `GET` | X | X | Gets customer notes for a given customer.
`/Customer/{CustNo}/Note` | `POST` | X | X | Adds a new note to an existing customer.
`/Customer/{CustNo}/Note` | `PATCH` | X | X | Updates an existing note on an existing customer.
`/Customer/{CustNo}/Note` | `DELETE` | X | X | Deletes a note from an existing customer.
`/Customer/{CustNo}/OpenItems` | `GET` | X | X | Gets customer AR Open Item information.
`/CustomerControl` | `GET` | X | X | Gets customer control information.
`/Customers` | `GET` | X | X | Gets information on customers in bulk.
`/Customers/EC` | `GET` | X | X | Gets information on eCommerce customers in bulk.
`/Document` | [`POST`](Endpoints/POST_Document.md) | X | X | Adds a new document (ticket).
`/Document/{DocId}` | `GET` | X | X | Gets information on an existing document (ticket) that hasn't been posted yet.
`/Document/{DocId}/Contact` | `POST` | X | X | Adds a contact to an existing document.
`/Document/{DocId}/Contact` | `PATCH` | X | X | Updates a contact on an existing document.
`/Document/{DocId}/Contact` | `DELETE` | X | X | Deletes a contact from an existing document.
`/Document/{DocId}/Lines` | `POST` | X | X | Adds Lines to a document.
`/Document/{DocId}/Note` | `POST` | X | X | Adds a note to an existing document.
`/Document/{DocId}/Note` | `PATCH` | X | X | Updates a note on an existing document.
`/Document/{DocId}/Note` | `DELETE` | X | X | Deletes a note from an existing document.
`/Document/{DocId}/Payments` | `POST` | X | X | Adds Payments to a document.
`/EC` | `GET` | X | X | Gets eCommerce settings.
`/ECCategories` | `GET` | X | X | Gets eCommerce Categories and items.
`/GiftCard/{GiftCardNo}` | `GET` | X | X | Gets gift card information.
`/GiftCardCode/{GiftCardCode}` | `GET` | X | X | Gets gift card code information.
`/GiftCardCodes` | `GET` | X | X | Gets information on gift card codes in bulk.
`/GiftCards` | `GET` | X | X | Gets information of Gift Cards in bulk.
`/Inventory/{LocId}` | `GET` | X | X | Gets inventory information for all items for a given location. Can be filtered further by category or subcategory
`/InventoryControl` | [`GET`](Endpoints/GET_InventoryControl.md) | X | X | Gets inventory control information.
`/Inventory/EC` | `GET` | X | X | Gets eCommerce inventory information for all eCommerce items.
`/Item/Images/{Filename} ` | [`GET`](Endpoints/GET_Item_ImageFilename.md) | X | X | Gets an item image for the given item and filename.
`/Item/{ItemNo}` | [`GET`](Endpoints/GET_Item.md) | X | X | Methods to get item and item inventory information.
`/Item/{ItemNo}/Images` | [`GET`](Endpoints/GET_Item_Images.md) | X | X | Gets a list of available item images for a given item.
`/Item/{ItemNo}/Inventory/{LocId}` | `GET` | X | X | Gets item inventory information for a given item and location.
`/Item/{ItemNo}/InventoryCost/{LocId}` | [`GET`](Endpoints/GET_InventoryCost.md) | X | X | Gets item inventory information for a given item and location.
`/ItemCategories` | [`GET`](Endpoints/GET_ItemCategories.md) | X | X | Gets item Categories in bulk.
`/ItemCategory/{CategoryCode}` | [`GET`](Endpoints/GET_ItemCategory.md) | X | X | Gets item category information for the given category code.
`/Items` | [`GET`](Endpoints/GET_Items.md) | X | X | Gets item information in bulk. Can be further filtered by category or subcategory.
`/Items/{LocId}` | `GET` | X | X | Gets item information for a given location in bulk. Can be further filtered by category or subcategory.
`/PayCode/{Paycode}` | [`GET`](Endpoints/GET_Paycode.md) | X | X | Gets information about a given Paycode.
`/PayCode/{Paycode}` | `PATCH` | X | X | Updates information about a Paycode.
`/PayCodes` | [`GET`](Endpoints/GET_Paycodes.md) | X | X | Gets information on Paycodes in bulk.
`/Role/Endpoints` | [`GET`](Endpoints/GET_RoleEndpoints.md) | | | Gets a list of endpoints that can be made available to any role.
`/Role/{RoleName}` | [`DELETE`](Endpoints/DELETE_Role.md) | | | Delete a role.
`/Role/{RoleName}` | [`GET`](Endpoints/GET_Role.md) | | | Gets endpoint information for a role.
`/Role/{RoleName}` | [`PUT`](Endpoints/PUT_Role.md) | | | Update or insert a role.
`/Role/{RoleName}/Users` | [`GET`](Endpoints/GET_RoleUsers.md) | | | Gets a list of users assigned to the role.
`/Role/{RoleName}/Users` | [`PUT`](Endpoints/PUT_RoleUsers.md) | | | Add or update the users list belonging to the role.
`/Roles` | [`GET`](Endpoints/GET_Roles.md) | | | Gets a list of roles with endpoint data.
`/Roles/Names` | [`GET`](Endpoints/GET_RoleNames.md) | | | Gets a list of role names.
`/Roles/Users` | [`GET`](Endpoints/GET_RolesUsers.md) | | | Gets a list of all roles with permissions and assigned users.
`/Store/{StoreID}` | [`GET`](Endpoints/GET_Store.md) | X | X | Gets information on a store.
`/Store/{StoreID}/Station/{StationID}` | [`GET`](Endpoints/GET_Store_Station.md) | X | X | Gets information on a station.
`/TaxCodes` | [`GET`](Endpoints/GET_TaxCodes.md) | X | X | Gets information on Tax Codes.
`/User/{UserID}` | [`GET`](Endpoints/GET_User.md) | X | X | Gets information on a User.
`/User/{UserID}/Roles` | [`DELETE`](Endpoints/DELETE_UserRoles.md) | |  | Deletes a user's assigned roles.
`/User/{UserID}/Roles` | [`GET`](Endpoints/GET_UserRoles.md) | |  | Get a list of roles for the user.
`/User/{UserID}/Roles` | [`PUT`](Endpoints/PUT_UserRoles.md) | |  | Update a user's assigned roles.
`/Users` | [`GET`](Endpoints/GET_Users.md) | | |  Gets a list of users.
`/Users/Roles` | [`GET`](Endpoints/GET_UsersRoles.md) | |  | Get a list of users and their assigned roles.
`/Workgroup/{WorkgroupID}` | [`GET`](Endpoints/GET_Workgroup.md) | X | X | Gets workgroup information.
