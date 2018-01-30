# Secure Pay card on file tokenization

The tokenization utility was implemented as part of the API to allow converting card on file data stored in a Counterpoint database into Secure Pay tokens, thus removing card data from the Counterpoint system. As such it can be called the same way other API calls are made in order to script or automate the tokenization of cards. In addition, the API admin console has a web based UI that allows for viewing and tokenizing card data for Secure Pay. There are two API calls that are provided to allow tokenization of card data:
* **POST /Store/{StoreId}/Tokenize**: Used to tokenize card data for the provided Store
* **GET /Store/{StoreId}/Tokenize**: Used to get information about how many cards are tokenized or not for the provided store 
	
## Setup:
Regardless of whether you are using the UI or direct API calls, the following steps must be completed in order to use the tokenization utility:
1. Install the API server, instructions can be found [here](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/InstallationAndConfiguration/Installing.md).
1. Connect the API server to the Counterpoint company containing cards you wish to tokenize. Instructions can be found [here](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/InstallationAndConfiguration/Configuring.md). Note that the tokenization API calls or utility is not run by an API admin. It must be run by a company level login with a role assigned to the user which has access to the two tokenization related API calls. Also note that an API Key is not required in order to use the tokenization API calls. However, the API Option is required to be present in your registration.ini file. See the section titled "Counterpoint registration.ini Option" on [this page](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/InstallationAndConfiguration/Licensing.md) for details.

## Using the API admin console to tokenize cards
Once everything is configured, the web utility can be accessed to easily tokenize cards on file (Chrome browser recommended):
1. Navigate to the login page of your API server: `https://<apiservername>:<port>/app/index.htm#/login` . The default port is 52000.
1. Login to the API admin console using your Counterpoint user that has the proper roles/permissions assigned as described above. Note the user name will be in the format <company>.<user>, and the password will be the user's Counterpoint password.
1. Once logged in, Select "Utilities > Secure Pay Tokenization" from the menu
1. The tokenization utility will display a list of stores, along with information on how many cards are tokenized or not tokenized for each store. 
1. Click the "Tokenize Store" button on any store record to tokenize any non-tokenized card on file records for the store. Note the button will not be visible if there are no non-tokenized card on file records for the store. Depending on the number of card on file records that need to be tokenized, the process could take a few minutes. When complete the page will refresh and update the tokenized record count. If everything goes as planned, the store should now show 0 non tokenized cards. 
1. Repeat the process for each store you wish to tokenize card on file records for.

## Using API calls to tokenize cards
Alternatively, direct API calls can be made to retrieve tokenization data for each store, or tokenize data for a given store. This allows for the tokenization functionality to be scripted using a tool such as cURL, or embedded into your own custom utility. Documentation on the two API calls can be found here:
* [POST /Store/{StoreId}/Tokenize](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/Endpoints/POST_StoreTokenize.md)
* [GET /Store/{StoreId}/Tokenize](https://github.com/NCRCounterpointAPI/APIGuide/blob/master/Endpoints/GET_StoreTokenizeInfo.md)

