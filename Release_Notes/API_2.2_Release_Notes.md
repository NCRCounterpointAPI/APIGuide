@@ -0,0 +1,59 @@
# NCR Counterpoint API v2.2 Release Notes
Version 2.2 of the NCR Counterpoint API addresses several issues, including:

### Issue CP-10435 REST API: Security Questions in regards to access of API’s metadata, endpoint information and request logs information
Previously an external user could access certain internal information from a running instance of the CPAPI process.

In this version, a configuration setting has been added to allow the administrator to enable or disable internal information such as metadata, request logs, SOAP12, SOAP11,  Debug Info section, Postman plugin, Swagger plugin. 

The setting can be found in the file CPAPI.exe.config at the “appSettings” section, and it is labeled “enableDebugInfo”.

By default, this is "false". In development environments, it may be convenient to turn it on by changing the value to "true". Note that changes to this setting require restarting the CPAPI service.

### Issue CP-10562 Counterpoint REST API: Cannot send updates from CP to the API service for all tables. (IM_ITEM).
Previously changes to an item in CP would not be reflected by the API's GET request for up to 24 hours. This was due to data caching on the Item after doing an inital GET request.

In this version, a configuration setting has been added to allow the administrator to change the time that a cache is active on the request to get an item.

The setting can be found in the file CPAPI.exe.config at the “appSettings” section, and it is labeled "ItemCacheActiveTimeMinutes".

The default value of this setting is 120 minutes which is equivalent to 2hrs. Setting this configuration value to 0 will eliminate any caching of the Item object and any changes made to an item in the database
will be reflected by the API's GET request immediately. Omitting/misspelling the name of this configuration setting or setting an incorrectly formatted value (ie. setting the value to 'E' instead of a numeric value) 
will set the cache time to be the default value of 120 minutes.  Note that changes to this setting require restarting the CPAPI service.

Note that the user will have to evaluate the trade-offs to determine an appropriate value for this caching. 


