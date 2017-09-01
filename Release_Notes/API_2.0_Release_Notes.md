# NCR Counterpoint API v2.0 Release Notes
Version 2.0 of the NCR Counterpoint API includes the following new features and improvements:
## Version Number and PA-DSS Validation
While we originally intended this release to be version 1.1, due to the nature of changes included in thisrelease, along with our PCI-DSS versioning guidance, we were compelled to label this release version 2.0.

This version change means that the current PA-DSS validation for the 1.x release of the API is not applicable for this release. We will be pursuing a 2.x PA validation to cover the v2.0 release line.

When the PA-DSS assessment of the v2.0 API is complete, we will publish a new Attestation of Validation (AOV) and announce the API's PA-DSS compliance status.
## NCR Counterpoint V8.5.3 Support
Version 2.0 of the NCR Counterpoint API has been tested with and is fully supported by NCR Counterpoint V8.5.3.
## SHA-256 Certificate with TLS 1.2 Compatibility
The installer for version 2.0 of the NCR Counterpoint API now generates a self-signed certificate, using the SHA-256 cryptographic algorithm, that is compatible with Transport Layer Security (TLS) 1.2.
## Start/End Date Filters for Item, Customer, and Inventory Endpoints
To provide date filtering functionality, a number of endpoints now support the **StartDate** and **EndDate** parameters. These parameters allow you to specify a date range that filters the modified date (**RS_UTC_DT**) field for calls to the following endpoints:
- [**GET /Customers**](../Endpoints/GET_Customers.md)
- [**GET /Customers/EC**](../Endpoints/GET_Customers_EC.md)
- [**GET /Inventory/EC**](../Endpoints/GET_InventoryEC.md)
- [**GET /Inventory/{LocID}**](../Endpoints/GET_Inventory_ByLocation.md)
- [**GET /Items**](../Endpoints/GET_Items.md)
- [**GET /Items/{LocID}**](../Endpoints/GET_Items_ByLocation.md)

**NOTE:** You must use the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date format in the **StartDate** and **EndDate** parameters. Other formats may produce unexpected results.
## Paging Parameters for Item, Customer, and Inventory Endpoints
To accomodate large data sets, a number of endpoints now support the new **Page** and **Rows** parameters. These parameters allow you to specify the number of rows to retrieve per page and the specific page number to retrieve for the following endpoints:
- [**GET /Customers**](../Endpoints/GET_Customers.md)
- [**GET /Customers/EC**](../Endpoints/GET_Customers_EC.md)
- [**GET /Inventory/EC**](../Endpoints/GET_InventoryEC.md)
- [**GET /Inventory/{LocID}**](../Endpoints/GET_Inventory_ByLocation.md)
- [**GET /Items**](../Endpoints/GET_Items.md)
- [**GET /Items/{LocID}**](../Endpoints/GET_Items_ByLocation.md)
## New Endpoint: GET /Inventory/Locations
This version of the NCR Counterpoint API includes a new [**GET /Inventory/Locations**](../Endpoints/GET_InventoryLocations.md) endpoint, which allows you to retrieve information from the IM_LOC table for all stocking locations.
## Resolved Issues
Version 2.0 addresses a number of issues that were reported in the initial v1.0 release of the NCR Counterpoint API, including:
### GET /Items Endpoint - Error 500 ([Issue #7](https://github.com/NCRCounterpointAPI/APIGuide/issues/7 ))
Previously, calls to the **/Items** endpoint in databases with a large number (10,000+) of item records returned an error, due to the size of the dataset and the number of child records that needed to be retreived.

In this version, the underlying queries for the following endpoints have been updated to be able to retrieve large datasets without returning an error: 
- **GET /Customers/EC**
- **GET /Inventory/{LocID}**
- **GET /Inventory/EC**
- **GET /Items**
- **GET /Items/{LocID}**
### GET /Item/Images/{filename} - Case-sensitive File Names ([Issue #29](https://github.com/NCRCounterpointAPI/APIGuide/issues/29))
Previously, **GET /Item/Images/{filename}** calls would only successfully return results when the item image file names on the corresponding NCR Counterpoint server were all uppercase with lowercase file extensions (e.g., ITEM_IMAGE.jpg).

In this version, **GET /Item/Images/{filename}** calls are no longer case-sensitive and always return the specified image(s), regardless of the image file names.
### Installing API on a System without Counterpoint ([Issue #2](https://github.com/NCRCounterpointAPI/APIGuide/issues/2))
Previously, the NCR Counterpoint API would not start properly when it was installed on a system that did not already have NCR Counterpoint installed.

In this version, the API starts without error on a system that does not have NCR Counterpoint installed.
### Saving a New Role
Previously, when you added a new role in the API Admin Console, the new role was not saved unless endpoints were defined for the role, which could result in roles "disappearing" from the **Edit Roles** list.

In this version, each new role is saved automatically when you click the **Add New Role** button.
### Edit Admin Form Returns No Results when Company is Edited
Previously, when you used the **Edit Company** function of the API Admin Console, even if no changes were made, the **Add Company Admins** dialog that appears when you click **Edit Admins** did not list any administrator users.

In this version, clicking **Edit Admins** always displays a list of administrator users in the **Add Company Admins** dialog, regardless of whether you have recently edited your company.
### Edit Company Function in Admin Console Not Working
In previous builds of the NCR Counterpoint API, the **Edit Company** function in the API Admin Console could sometimes fail, preventing changes to a company once it was added.

In this version, administrator users can reliably use the **Edit Company** function to edit existing companies and save their changes correctly.
