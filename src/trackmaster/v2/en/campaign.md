---
weight: 3
layout: default
category: trackmaster
subcategory: agency
language: en
title: Campaign
version: v2
---

# Campaign

* TOC
{:toc}

## List the authorized campaigns

    GET http://m.trackmaster.com.cn/api_v2/networks/:networkId/campaigns

**Response**

{:.prettyprint}
    [{
    "id": 999,//Campaign ID
    "name": "Test",//Campaign Name
    "advertiserId": 999, // Advertiser ID
    "brandId": 999, // Brand ID
    "networkId": 999, // Network ID
    "trackType": "nonmobile", //Campaign Type,`mobile`,`nonmobile`
    "startDate": "2015-04-15T00:00:00.000Z", // Start Date
    "endDate": "2015-04-30T00:00:00.000Z", //End Date
    "mediaIds":"440", // Media list
    "status": "enabled"", //`enabled`,`disabled`
    "costType":"none", //Settlement currency,`cny`,`usd`,`none`
    "siteMasterId": "999", //SiteMaster ID
    "defaultTarget": "http://www.ui168.com", //Default Target URL
    "isDelete":no, //`yes`, `no`
    "party_name":"zhaoxiongfei", //Contactor(for emergencies and other important matters)
    "party_email"://Contact email(for emergencies and other important matters)
    "placements":20 // The actual number of existed placements.(Maximum:500)
    }]


## Campaign details

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:id

**Response**

{:.prettyprint}
    {
    "id": 999,//Campaign ID
    "name": "Test",//Campaign Name
    "advertiserId": 999, // Advertiser ID
    "brandId": 999, // Brand ID
    "networkId": 999, // Network ID
    "trackType": "nonmobile", //Campaign Type,`mobile`,`nonmobile`
    "startDate": "2015-04-15T00:00:00.000Z", // Start Date
    "endDate": "2015-04-30T00:00:00.000Z", //Start Date
    "mediaIds":"440", // Media list
    "status": "enabled"", //`enabled`,`disabled`
    "costType":"none", //Settlement currency,`cny`,`usd`,`none`
    "siteMasterId": "999", //SiteMaster ID
    "defaultTarget": "http://www.ui168.com", //Default Target URL
    "isDelete":no, //`yes`, `no`
    "party_name":"zhaoxiongfei", //Contactor(for emergencies and other important matters)
    "party_email"://Contact email(for emergencies and other important matters)
    "placements":20 // The actual number of existed placements.(Maximum:500)

    }

## Add a campaign

    POST http://m.trackmaster.com.cn/api_v2/networks/:networkId/campaigns


Note:That it will not create a new campaign, if the name has been used in the same advertise.

**Paremeters**

`name`
: _Required_  Campaign Name

`advertiserId`
: _Required_  Advertiser ID

`brandId`
: _Required_  Brand ID

`networkId`
: _Required_  Network ID

`trackType`
: _Required_  Campaign Type - `mobile`or`nonmobile`.

`startDate`
: _Required_  Beginning date to retrieve data in format YYYY-MM-DD.

`endDate`
: _Required_  Final date to retrieve data in format YYYY-MM-DD.

`defaultTarget`
: _Required_   Target Website. Example:http://www.admaster.com.cn/

`mediaIds`
: _Optional_   Media list

`costType`
: _Optional_   `cny`,`usd`,`none`

`party_name`
: _Optional_   Contactor（for emergencies and other important matters)

`party_email`
: _Optional_   Contact email(for emergencies and other important matters)

**Request**


{:.prettyprint}   
    {	
    	"name": "Test",//Campaign Name
    	"advertiserId": 999, // Advertiser ID
    	"brandId": 999, // Brand ID
    	"networkId": 999, // Network ID
    	"trackType": "nonmobile", //Campaign Type,`mobile`,`nonmobile`
    	"startDate": "2015-04-15T00:00:00.000Z", // Start Date
    	"endDate": "2015-04-30T00:00:00.000Z", //End Date
    	"mediaIds":"440", // Media list
    	"costType":"none", //Settlement currency,`cny`,`usd`,`none`
    	"defaultTarget": "http://www.ui168.com", //Default Target URL
   	 	"party_name":"zhaoxiongfei", //Contactor(for emergencies and other important matters)
    	"party_email"://Contact email(for emergencies and other important matters)
    }

	


**Response**


{:.prettyprint}
    {
    "id": 999,//Campaign ID
    "name": "Test",//Campaign Name
    "advertiserId": 999, // Advertiser ID
    "brandId": 999, // Brand ID
    "networkId": 999, // Network ID
    "trackType": "nonmobile", //Campaign Type.Value:`mobile`,`nonmobile`
    "startDate": "2015-04-15T00:00:00.000Z", // Start Date
    "endDate": "2015-04-30T00:00:00.000Z", //End Date
    "mediaIds":"440", // Media list
    "status": "enabled"", //`enabled`,`disabled`
    "costType":"none", //Settlement currency.Value:`cny`,`usd`,`none`
    "siteMasterId": "999", //SiteMaster ID
    "defaultTarget": "http://www.ui168.com", //Default Target URL
    "isDelete":no, //`yes`, `no`
   	"party_name":"zhaoxiongfei", //Contactor(for emergencies and other important matters)
    "party_email"://Contact email(for emergencies and other important matters)
    "placements":20 // The actual number of existed placements.(Maximum:500)
    }

## Update a campaign

    PATCH http://m.trackmaster.com.cn/api_v2/campaigns/:id

Note: Only submitted paremeters will be updated.

**Paremeters**

`name`
: _Optional_  Campaign Name

`advertiserId`
: _Optional_  Advertiser ID

`brandId`
: _Optional_  Brand ID

`trackType`
: _Optional_  Campaign Type - `mobile`or`nonmobile`.

`startDate`
: _Optional_  Beginning date to retrieve data in format YYYY-MM-DD.

`endDate`
: _Optional_  Final date to retrieve data in format YYYY-MM-DD.

`defaultTarget`
: _Optional_   Target Website. Example:http://www.admaster.com.cn/

`mediaIds`
: _Optional_   Media list

`costType`
: _Optional_   `cny`,`usd`,`none`

`party_name`
: _Optional_   Contactor(for emergencies and other important matters)

`party_email`
: _Optional_   Contact email(for emergencies and other important matters)

**Request**


{:.prettyprint}   
    {	
    	"name": "Test",//Campaign Name
    	"advertiserId": 999, // Advertiser ID
    	"brandId": 999, // Brand ID
    	"networkId": 999, // Network ID
    	"trackType": "nonmobile", //Campaign Type.Value:`mobile`,`nonmobile`
    	"startDate": "2015-04-15T00:00:00.000Z", // Start Date
    	"endDate": "2015-04-30T00:00:00.000Z", //End Date
    	"mediaIds":"440", // Media list
    	"status": "enabled"", //`enabled`,`disabled`
    	"costType":"none", //Settlement Currency.Value:`cny`,`usd`,`none`
    	"defaultTarget": "www.ui168.com", //Default Target URL
   		"party_name":"zhaoxiongfei", //Contactor(for emergencies and other important matters)
    	"party_email"://Contact email(for emergencies and other important matters)
    }

    
    
**Response**

{:.prettyprint}
    {
    	"id": 999,//Campaign ID
    	"name": "Test",//Campaign Name
    	"advertiserId": 999, // Advertiser ID
    	"brandId": 999, // Brand ID
    	"networkId": 999, // Network ID
    	"trackType": "nonmobile", //Campaign Type.Value:`mobile`,`nonmobile`
    	"startDate": "2015-04-15T00:00:00.000Z", // Start Date
    	"endDate": "2015-04-30T00:00:00.000Z", //End Date
    	"mediaIds":"440", // Media list
    	"status": "enabled"", //`enabled`,`disabled`
    	"costType":"none", //Settlement Currency.Value:`cny`,`usd`,`none`
    	"siteMasterId": "999", //SiteMaster ID
    	"defaultTarget": "www.ui168.com", //Default Target URL
    	"isDelete":no, //`yes`, `no`
   		"party_name":"zhaoxiongfei", //Contactor(for emergencies and other important matters)
    	"party_email"://Contact email(for emergencies and other important matters)
    	"placements":20// The actual number of existed placements.(Maximum:500)
    }


## Delete a campaign

    DELETE http://m.trackmaster.com.cn/api_v2/campaigns/:id


Note:That it will not delete an existed campaign, if the campaign contains placements - old placements must be deleted first.

**Response**

    Status: 204 OK
