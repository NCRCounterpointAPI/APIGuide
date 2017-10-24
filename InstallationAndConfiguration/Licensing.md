# API Licensing
While there are some administrative and other select API calls that can be freely used, most endpoints the API exposes require either a developer API key, a Counterpoint registration.ini option, or both. A description of each licensing component is below.

## Developer API Keys
Any 3rd party that wishes to use endpoints restricted by API Keys must submit an online application for a free NCR Counterpoint API Developer Key at [https://retailchannel.radiantsystems.com/api_request.htm]. All requests will be manually reviewed, and API Key files will be emailed to the provided contact for approved requests.

While API Keys are free to obtain, a primary requirement is that a distinct key is used for each "usage" of the API. If a developer plans on building two applications that use the API, they should apply for two developer keys. This serves a few purposes:

- It allows us to know who is using the API for what, which is helpful in making business decisions.
- In an environment with a single API server serving multiple companies, it allows us future potential to restrict which application can operate with which companies.
- For support, it allows us to analyze and identify any applications that may not be working properly, flooding the server, or causing other issues. It will also allow us to filter data on the server to help troubleshoot issues with particular applications.

The following information must be provided to request an API key:
- **Company Name**: The name of the company developing the application
- **Issued To**: The name of an individual who is a contact point for the application
- **eMail1**: The email of the contact point for the application (eMail could be used for any communication from NCR relating to the application, such as a notice to renew their API Key)
- **eMail2**: A backup email contact for communications
- **Application Name**: The name of the application being developed.
- **Description**: A description of the application being developed.

Once a developer API Key request is approved, they will get two files:
- **`<Appname>_key.txt:`** This file contains the unencrypted, plain text API key. This file is for safekeeping by the developer. The key value inside this file should be embedded in the developer application and submitted with each API request. Reasonable attempts should be made to protect the key inside the application (not easily obtainable), and it should not be shared with anyone.
- **`<Appname>_key.xml:`** This is a signed XML file containing information about the application, an encrypted version of the API Key, and an expiration date. If this file is edited in any way, the digital signature validation will fail and API Server instances will fail to recognize it. This file should be placed in the "APIKeys" subfolder of any API Server instance that your application will connect to. For example, on my test machine the APIKeys go in this folder:

`C:\Program Files (x86)\NCR\Counterpoint API\APIKeys`

The client application will then submit the API Key in the `APIKey` header of each API call as follows:
 
**`APIKey : KEkPhw538hsFS17dadWwXqmqUdpz2RGY4dqGQkuE`**

Any API Call that requires an API Key will fail with a `403 Forbidden` result if:
- No API Key is provided in the `APIKey` header for the call.
- The API Key file (xml file) on the server has an invalid signature indicating the file has been tampered with.
- The API Key file on the server is expired.

#### Expiration Dates
To ensure reliability, the API was designed to not require any connectivity to NCR. So instead of real-time API Key validity checks, we've implemented API Key expiration. Our initial plan is that API Keys will be valid for two years. At that point they will need to be renewed, and the renewed API Key file will need to be distributed to any API Server instance that your application connects to. It is the responsibility of the application developer to ensure that they renew their key prior to expiration, and distribute renewed keys to all merchants using thier application to ensure no disruption in the functionality of their application. For future functionality, we're looking into the ability for the API Server to automatically download renewed API Key files from NCR if connectivity is available.

## Counterpoint registration.ini option
Similarly to API Keys, most API endpoints require the merchant company to have the API option present in their Counterpoint registration.ini file. The API License is avaialble free of charge, but merchant partners will request this option similar to how they request other options, such as credit cards or advanced pricing. The API license option will be contained in the merchant's registration.ini file, which must be in place and valid. If an API call that requires the registration option is made to a company that does not have it, the call will fail with a `403 Forbidden` result code.

### Requesting the API registration option for existing merchants
Existing Counterpoint merchants can get the API Option added to their registration.ini by having their Counterpoint reseller partners request the option at [https://retailchannel.radiantsystems.com/api_option_request.htm] and following the instructions there:

1. Login to the partner portal
2. Navigate to [https://retailchannel.radiantsystems.com/api_option_request.htm]
3. Choose the appropriate Counterpoint system serial number, enter the email address that will receive the request confirmation and click the Submit Request button.

### Requesting the API registration option for new merchants
The Counterpoint reseller partner may request the API option for new merchants by adding a note saying "Please Add API Option" to the system notes. Sales ops has been instructed to look for this note and include the option when present.
