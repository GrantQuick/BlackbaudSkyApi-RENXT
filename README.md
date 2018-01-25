## BlackbaudSkyApi
A Power BI custom data connector for the Blackbaud SKY API
![PBIGetData](blobs/getdata.png "SKY API in Get Data")

## Getting Started
These instructions will describe how to configure the SKY API connector in order to connect to your organisation's data. See Microsoft's guide to installing and using custom data connectors in Power BI here: https://github.com/Microsoft/DataConnectors.

A Blackbaud developer account is required in order to create an application. Once an application has been created, you will need the client_id of the application, the client_secret of your application, and your developer account's api_subscription_key.

### Setting up a Blackbaud developer account
Follow the instructions at https://apidocs.sky.blackbaud.com/docs/getting-started/ to create a developer account and acquire your api_subscription key.

### Creating an app
Follow the instructions at https://apidocs.sky.blackbaud.com/docs/createapp/ to register and activate your app. Registering your app will generate a client_id and client_secret for the app. Ensure that the Redirect URL for the app you create is set to http://localhost/5000

### Installing the connector
1. If one does not already exist, create a `[My Documents]\Microsoft Power BI Desktop\Custom Connectors` directory
2. Download the SkyApi.mez file from this repo, and place it in the `[My Documents]\Microsoft Power BI Desktop\Custom Connectors` directory.
3. Rename the SkyApi.mez file to SkyApi.zip
4. Open up SkyApi.zip. Edit the client_id, client_secret and api_subscription_key files. In each file, copy and paste the character strings for the appropriate entity (the client_id, client_secret and api_subscription_key generated when creating a Blackbaud developer account and app) into the correct file. Save the changes to each of the three files.
5. Rename SkyApi.zip back to SkyApi.mez.
4. Enable the **Custom data connectors** preview feature in Power BI Desktop (under *File | Options and settings | Custom data connectors*)
8. Restart Power BI Desktop
9. In Power BI Desktop, click **Get Data > Other > Blackbaud SkyAPi (Beta)**
10. The first time you use the connector you will need to log in using your Blackbaud account and authorise the app to work with your data.

## Supported Endpoints
Additional endpoints will be added in time. Currently the connector supports:
* Constituent list
* Phone list
* Email Address list
* Address list
* Education list
* Constituent Code list
* Online Presence list
* Relationship list
* Constituent Custom Field list
* Gift list
* Gift Custom Field list
* Appeal list
* Campaign list
* Fund list
* Opportunity list

## Additional Information
The connector will only generate a barebones data model. List or record type data fields will have to be expanded when designing your own data model. For example, when connecting to the Gifts endpoint, in Power BI you will need to click **Edit Queries** in order to expand and view the gift amounts.

Handling of rate limiting has now been implemented, meaning that the connector should now gracefully wait and retry a call following a 429 error.

## Known Issues
Depending on dataset size, data load time can be long. As a maximum of 500 records can be returned by any single call to an endpoint, datasets of several hundred thousand records will require many hundred calls to the API. The API also employs rate limiting to prevent overload of Blackbaud servers. This can mean that data loads of all endpoints will take several minutes. Connecting to only the required endpoints will reduce data load time.

As an indicator of expected performance, the connector has been tested with an initial concurrent load on all (currently supported) endpoints on a database with the following record counts per endpoint:

* 150,000 addresses
* 100,000 constituent codes
* 350,000 constituent custom fields
* 100,000 constituents
* 100,000 education
* 40,000 emails
* 1,000 online presences
* 55,000 phones
* 45,000 relationships
* 30 appeals
* 6 campaigns
* 70 funds
* 1,000 gift custom fields
* 50,000 gifts
* 100 opportunities

The data load time for all of the above is in the region of 55 minutes

## Authors
* **Grant Quick** - *Iniital work* - [GrantQuick](https://github.com/GrantQuick)

## Acknowledgments
* This connector is based on the [custom data connector samples](https://github.com/Microsoft/DataConnectors) provided by [Microsoft](https://github.com/Microsoft)
* Thanks to Microsoft’s [CurtHagenlocher](https://gist.github.com/CurtHagenlocher) for the [Web.ContentsCustomRetry](https://gist.github.com/CurtHagenlocher/68ac18caa0a17667c805) function.
