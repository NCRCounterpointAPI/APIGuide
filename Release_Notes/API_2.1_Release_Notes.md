# NCR Counterpoint API v2.1 Release Notes
Version 2.1 of the NCR Counterpoint API addresses several issues, including:

### Error When Adding a Document with Paycode Set as final_pmt='Y' ([Issue #43](https://github.com/NCRCounterpointAPI/APIGuide/issues/43))
Previously, an error was encountered when the customer selected to apply a payment with a card paycode but did not provide the payment credit card information.
 
In this version, the error handling has been improved to indicate the missing information.

### Error When Inserting Document with Credit Card as Paycode ([Issue #48](https://github.com/NCRCounterpointAPI/APIGuide/issues/48))
Previously, an error was encountered when the customer chose to apply a payment with credit card paycode. However, some of the configurations were found to be invalid.
 
In this version, the code was updated to include better error handling. This update helps validate any similar errors that might be encountered.

### Error When Pulling a Known Document ID Due to Invalid Column Name OFFLINE_GUID ([Issue #52](https://github.com/NCRCounterpointAPI/APIGuide/issues/52))
Previously, an error was encountered when attempting to pull a known document ID because of an invalid column name, **OFFLINE_GUID**.
 
In this version, optional columns like **OFFLINE_GUID** are now excluded by the auto-gen functions.

### Error When Adding a New Customer Using the POST /Customer Endpoint ([Issue#60](https://github.com/NCRCounterpointAPI/APIGuide/issues/60))
Previously, an error was encountered when trying to add a new customer in some versions because an embedded resource file was missing in the code. 
 
In this version, the errors were fixed by updating the missing embedded resource file.

### Unknown Errors When Adding Customer ([Issue #61](https://github.com/NCRCounterpointAPI/APIGuide/issues/61))
Previously, unknown errors were encountered because of invalid settings in the workgroup, store, and customer template configurations.
 
In this version, the code was updated to provide better feedback and response to errors when using the **POST Document** function.

### Error When Inserting Quotes in Version 8.5.2.x and 8.4.6.18 ([Issue #68](https://github.com/NCRCounterpointAPI/APIGuide/issues/68))
Previously, an exception was encountered when inserting a quote document to version 8.5.2.x and 8.4.6.18 data sets.

In this version, the code was updated to check for nulls before trying to assign values to the object. 

### Out of Balance Distribution Error when Posting Ticket ([Issue #69](https://github.com/NCRCounterpointAPI/APIGuide/issues/69))
Previously, Out of Balance distribution errors were encountered because the procedure to copy data across mixed tickets did not fully work with Counterpoint logic. 
 
In this version, the errors were fixed by making changes to match the procedure with the logic.

### Error in AddDocument POST: 'Missing type map configuration or unsupported mapping' ([Issue #70](https://github.com/NCRCounterpointAPI/APIGuide/issues/70))
Previously, an error was encountered when performing **AddDocument POST** because of missing type map configuration or unsupported mapping. 
 
In this version, the mapping of the objects was fixed to avoid a mismatch between repository and model objects.

### POST Document Not Taking TKT_NO ([Issue #71](https://github.com/NCRCounterpointAPI/APIGuide/issues/71))
Previously, when creating a document type **T**, the ticket created doesn't have the **TKT_NO** sent. Instead, it used the value in the station settings. 
 
In this version, the code has been updated to use the **TKT_NO** value entered by the user. Otherwise, the auto-generated value in the store or station settings will be used.

### Error When Running Card Tokenization Utility Request ([Issue #85](https://github.com/NCRCounterpointAPI/APIGuide/issues/85))
Previously, an error was encountered when running the tokenization utility because the request had too many parameters.

In this version, the code was updated to further filter the amount of data being fetched by the original query. 

### When Viewing the /Requestlogs Endpoint, Sensitive Information is Sent to the API. ([Issue #122](https://github.com/NCRCounterpointAPI/APIGuide/issues/122))

Previously, sensitive information such as passwords and credit card data are sent to the API when viewing the **/Requestlogs** endpoint.

In this version, the sensitive information is masked to provide data security.

