#NCR Counterpoint API Keys

Most API calls require and APIKey to be submitted in the http headers of the API call in the following format:

**<code>APIKey : KEkPhw538hsFS17dadWwXqmqUdpz2RGY4dqGQkuE</code>**

API Keys can be obtained by submitting a request at *need link*. If an invalid or expired API Key is submitted with a request, the request will fail with a **<code>403 forbidden</code>** http response code. See documentation on a particular API call to determine if it requires an API Key or not.

**NOTE:** Per the developer agreement, a unique APIKey should be used for each application or unique usage of the API. It is a violation of the agreement to use APIKeys that were not issued to you, or to use the same APIKey for multiple uses.

**NOTE:** API Keys have an expiration date. To ensure your applications continue to work with the NCR Counterpoint API, please ensure that you're aware of the expiration date of your API Key and that you proactively renew and update the API Key xml file in your merchant's API installations.
