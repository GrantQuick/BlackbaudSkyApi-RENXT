G# BlackbaudSkyApi
A Power BI custom data connector for the Blackbaud SKY API

## Getting Started
These instructions will describe how to configure the SKY API connector in order to connect to your organisation's data. See Microsoft's guide to installing and using custom data connectors in Power BI here: https://github.com/Microsoft/DataConnectors

### Installing
1. If one does not already exist, create a `[My Documents]\Microsoft Power BI Desktop\Custom Connectors` directory
2. Download the SkyApi.mez file from this repo, and place it in the `[My Documents]\Microsoft Power BI Desktop\Custom Connectors` directory.
3. Rename the SkyApi.mez file to SkyApi.zip
4. Open up SkyApi.zip. Edit the client_id, client_secret and api_subscription_key files. In each file, add the character string specific to your organisation for each entity. Save the files.
5. Rename SkyApi.zip back to SkyApi.mez.
4. Enable the **Custom data connectors** preview feature in Power BI Desktop (under *File | Options and settings | Custom data connectors*)
8. Restart Power BI Desktop
9. In Power BI Desktop, click **Get Data > Other > Blackbaud SkyAPi (Beta)**
10. The first time you use the connector you will need to log in using your Blackbaud account and authorise the app to work with your data.
