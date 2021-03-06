# Microsoft Power BI Custom Data Connectors
The Microsoft Power BI custom connector support-project.
Thank you for the support from users all over giving me feedback and using the connectors.
Users I know of: Francisco Altamirano, Blastam, Masai, Puori, Bangerhead, Columban Mission, Stanton Fisher and Tanger Outlet

## Available custom data connectors
* [Stripe](#the-stripe-connector)
* [LinkedIn](#the-linkedin-connector)
* [Facebook Pages Insight](#the-facebook-pages-insight-connector)
* [Facebook Ads Insight](#the-facebook-ads-insight-connector)
* [Instagram](#the-instagram-connector)

## Any wishes?
I would like feedback on which data connector YOU need. Maybe I can help or we can build it together.

## Download ready-to-use packages
You can download ready-to-use .mez files from SCITYLANA [here][sl-pbi-gallery].

## The Stripe Connector

This connector should be used instead of the broken official connector.

Here is a list of features that have been fixed:
* Limited access API keys (the original connector only works with the master API key, which is REALLY bad when you want to publish a dashboard)
* Fetching all rows data for all tables (the original connector doesn't handle paging correct)

## The LinkedIn Connector

To build the connector you need to create a Linked In App to get an OAuth2 key and secret.
[Create a the app here][li-api]

In LinkedIn\WebApp.json set Client Id and Client Secret
```
      "client_id": "[Client ID]",
      "client_secret": "[Client Secret]",
```

The connector is an interface to historical endpoints of linkedin Manage Company Pages endpoints

- Get historical follower statistics about a company
- Get historical status update statistics about a company

Focus is on the granular endpoints since they can be aggregated which play well with Power BI.
We would prefer the raw hit-level data behind each aggregated date but that is not available through the LinkedIn API

This is how it looks in Power BI:

<img src="https://github.com/mbilling/PBIConnectors/blob/master/img/linkedin-company-navigator-shot.png" alt="The LinkedIn Connector in Power BI" title="The LinkedIn Connector in Power BI"/>

## The Facebook Pages Insight Connector

To build the connector you need to create a Facebook App to get an OAuth2 key and secret.
[Create a the app here][fb-api]

In FacebookPages\WebApp.json set Client Id and Client Secret
```
      "client_id": "[App ID]",
      "client_secret": "[App Secret]",
```

This connector is focused on accessing page insights using the pages insights API: [Facebook Pages Insights][fb_pages_insights]

The built-in Facebook connector provides access to Facebook user profile, not pages or ads statistics.

This is how it looks in Power BI:

<img src="https://github.com/mbilling/PBIConnectors/blob/master/img/fb_pages_insights_navigator_shot.PNG" alt="The Facebook Pages Insight Connector in Power BI" title="The Facebook Pages Insight Connector in Power BI"/>


## The Facebook Ads Insight Connector

To build the connector you need to create a Facebook App to get an OAuth2 key and secret.
[Create a the app here][fb-api]

In FacebookAds\WebApp.json set Client Id and Client Secret
```
      "client_id": "[App ID]",
      "client_secret": "[App Secret]",
```

This connector is focused on accessing page insights using the ads insights API: [Facebook Ads Insights][fb_ads_insights]

The built-in Facebook connector provides access to Facebook user profile, not pages or ads statistics.

This is how it looks in Power BI:

<img src="https://github.com/mbilling/PBIConnectors/blob/master/img/fb_ads_insights_navigator_shot.PNG" alt="The Facebook Ads Insight Connector in Power BI" title="The Facebook Ads Insight Connector in Power BI"/>


## The Instagram Connector

### Instagram - Facebok page association issue
To pull statistics from Instagram you need to set-up an association with a Facebook Page. This is not a big deal.
But if you already did this a while ago, you might need doing it again.
If the Instagram connector fails with the message "The field 'connected_instagram_account' of the record wasn't found." then the Instagram account and the Facebook page are not completely connected.

I have been able to circumvent this problem by 
1. Switching the IOS/Android app from Business Account to Personal Account and back to Business Account.
2. The again from the IOS/Android app - Unlink Facebook account and Link it again.

## Get started

To build the connector you need to create a Facebook/Instagram App to get an OAuth2 key and secret. 
You need to have your Instagram Account conected to your Facebook Page, [read more here][instagram-info]

[Create a the app here][fb-api]

In Instagram\WebApp.json set Client Id and Client Secret
```
      "client_id": "[App ID]",
      "client_secret": "[App Secret]",
```

This connector is focused on accessing page insights using the Instagram insights API: [Instagram Insights][instagram-api]

This is how it looks in Power BI:

<img src="https://github.com/mbilling/PBIConnectors/blob/master/img/instagram_insights_navigator_shot.PNG" alt="The Instagram Insight Connector in Power BI" title="The Instagram Insight Connector in Power BI"/>




## How to use the custom connectors
Microsoft only supports custom connectors for Power BI Desktop. We expect this to change when they release the Power Query SDK.

Using the connectors
1. When custom connectors are built into .mez files, they should be copied to Documents\Microsoft Power BI Desktop\Custom Connectors
2. Start Power BI
3. Ooen the Options dialog
4. Select Preview features and Click OK
5. Click Get Data and select Other
6. You find the Connectors here.

## Related repos
[Facebook Ads Connector][hugo]

[Youtube Connector][miguel]


[fb_pages_insights]: https://developers.facebook.com/docs/graph-api/reference/page/insights
[fb_pages_insights_navigator_shot]: https://github.com/mbilling/PBIConnectors/blob/master/img/fb_pages_insights_navigator_shot.PNG
[ms_repo]: https://github.com/Microsoft/DataConnectors
[hugo]: https://github.com/Hugoberry/FacebookAds
[miguel]: https://github.com/migueesc123/YoutubeAnalytics
[li-api]: https://www.linkedin.com/developer/apps
[fb-api]: https://developers.facebook.com/apps/
[instagram-api]: https://developers.facebook.com/docs/instagram-api/reference/user/insights
[instagram-info]: https://help.instagram.com/356902681064399
[fb_ads_insights]: https://developers.facebook.com/docs/graph-api/reference/page/insights
[fb_ads_insights_navigator_shot]: https://github.com/mbilling/PBIConnectors/blob/master/img/fb_pages_insights_navigator_shot.PNG
[sl-pbi-gallery]: https://www.scitylana.com/connectors
