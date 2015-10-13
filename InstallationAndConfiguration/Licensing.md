# API Licensing
While there are some administrative and other select API calls that can be freely used, most endpoints the API exposes require either a developer API key, a Counterpoint registration.ini option, or both. A description of each licensing component is below.

## Developer API Keys
Any 3rd party that wishes to use endpoints restricted by API Keys must submit an online application for a free NCR Counterpoint API Developer Key `need link`. More details are on the signup site but essentially developers will need to provide some information explaining what they will use the API Key for, and agree to the Terms of Use for the API.

While API Keys are free to obtain, a primary requirement is that a distinct key is used for each "usage" of the API. If a developer plans on building two applications that use the API, they should apply for two developer keys. This serves a few purposes:

- It allows us to know who is using the API for what, which is helpful in making business decisions.
- In an environment with a single API server serving multiple companies, it allows us future potential to restrict which application can operate with which companies.
- For support, it allows us to analyze and identify any applications that may not be working properly, flooding the server, or causing other issues. It will also allow us to filter data on the server to help troubleshoot issues with particular applications.

Once a developer API Key request is approved, they will get two files:
- **`<Appname>_license.txt:`** This file contains the unencrypted, plain text API key. This file is for safekeeping by the developer. The key value inside this file should be embedded in the developer application and submitted with each API request. Reasonable attempts should be made to protect the key inside the application (not easily obtainable), and it should not be shared with anyone.
- **`<Appname>_license.xml:`** This is a signed XML file containing information about the application, an encrypted version of the API Key, and an expiration date. If this file is edited in any way, the digital signature validation will fail and API Server instances will fail to recognize it. This file should be placed in the "APIKeys" subfolder of any API Server instance that your application will connect to. For example, on my test machine the APIKeys go in this folder:

`C:\Program Files (x86)\NCR\Counterpoint API\APIKeys`

The client application will then submit the API Key in the `APIKey` header of each API call as follows:
 
**`APIKey : KEkPhw538hsFS17dadWwXqmqUdpz2RGY4dqGQkuE`**

Any API Call that requires an API Key will fail with a `403 Forbidden` result if:
- No API Key is provided in the `APIKey` header for the call.
- The API Key file (xml file) on the server has an invalid signature indicating the file has been tampered with.
- The API Key file on the server is expired.

#### Expiration Dates
To ensure reliability, the API was designed to not require any connectivity to NCR. So instead of real-time API Key validity checks, we've implemented API Key expiration. Our initial plan is that API Keys will be valid for two years. At that point they will need to be renewed, and the renewed API Key file will need to be distributed to any API Server instance that your application connects to. For future functionality, we're looking into the ability for the API Server to automatically download renewed API Key files from NCR if connectivity is available.

## Counterpoint registration.ini option
Similarly to API Keys, most API endpoints require the merchant company to have purchased the API option. Merchants will purchase this option the same way other options, such as credit cards or advanced pricing, are purchased. The API Key option will be contained in the merchant's registration.ini file, which must be in place and valid. If an API call that requires the registration option is made to a company that does not have it, the call will fail with a `403 Forbidden` result code.

Pricing is not yet determined on the registration.ini option. Communication will go out when pricing is determined, and it will be available in the same location as other registration options.
