# NCR Counterpoint API v2.4 Release Notes
Version 2.4 of the NCR Counterpoint API addresses several issues, including:

### Issue CP-12850 Message "IndexOutOfRangeException." returned using the Counterpoint Rest API
### Issue CP-12457 REST API: Price-1 is being used when adding an line item to a ticket, vs the one sent in API code
Previously, for endpoints that support Override Price, Price is overridden when HAS_PRC_OVRD is set to "Y" in the request body.

In this version, the Override Price logic has been updated. Price is now overridden when USR_ENTD_PRC is set to "Y".

Note that USR_ENTD_PRC determines the value of HAS_PRC_OVRD. If USR_ENTD_PRC="Y", then HAS_PRC_OVRD will be set to "Y", indicating that the price is overridden. Otherwise, HAS_PRC_OVRD will be set to "N".

### Issue CP-11550 Rest API - SSL Certificate issue during update unbinds the association to the current certificate
### Issue CP-12017 REST API Customer cannot run the API, they receive a DateTime error.
### Issue CP-8329 Message "An item with the same key has already been added." returned with every call using the Counterpoint Rest API

### NOTE:
Counterpoint V8.6 is not compatible with CPAPI V2.3 and prior versions. If you use the CPAPI, update to CPAPI V2.4 before updating to Counterpoint V8.6. (CPAPI V2.4 is compatible with prior Counterpoint versions.)
