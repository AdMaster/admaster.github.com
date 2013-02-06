---
weight: 14
layout: default
category: trackmaster
language: en
title: Agency
---


# TrackMaster API for Agency #

* TOC
{:toc}

TrackMaster provides an API for programmatic access to account data. All API access is over HTTP. All data is sent and received as JSON.

TrackMaster APIs use the OAuth 2.0 protocol for authentication and authorization. Please read more about [OAuth](http://dev.admaster.com.cn/doc/openmaster/v1/en/oauth.html) and [Protocal and Requests Instructions](http://dev.admaster.com.cn/doc/openmaster/v1/en/verbs.html).

All developers need to register their application before getting started. A registered OAuth application is assigned a unique `client_id` and `client_secret`. The `client_secret` should not be shared.

You must have a TrackMaster account. You can contact us to apply for a TrackMaster account. 

Read [Help Center](http://help.admaster.com.cn/trackmaster/) to learn about business logic.

Read [TrackMaster Index](/doc/trackmaster/v1/en/index.html) to learn about main objects.


# Guides #

## Get an access_token ##

    POST http://open.admaster.com.cn/oauth/access_token

**Parameters**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "password",
      "email": "yourmailaddress@email.com",
      "password": "***"
    }

**Response**

    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "18000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }

Access tokens have a limited lifetime and, in some cases, an application needs access to a TrackMaster API beyond the lifetime of `expires_in`. When this is the case, your application can obtain what is called a refresh token. A refresh token and some parameters allow your application to obtain new access tokens. 

**Parameters**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## List the authorized networks   ##

    GET /user/networks

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
       {
        "id": 11,//Network ID
        "url": "https://{{site.track_api_host}}/networks/11",
        "name": "Testing Network", //Network Name
        "created_at": "2012-09-06T20:39:23Z" //Creation Time
        "account": {
            "status": "enabled", //`enabled` , `disabled` , `unactive` 
            "created_at": "2012-01-10T02:30:59Z", //Network Authorized Time for User  
            "role": {
                "id": 1,//Role ID
                "name": "高级管理员(super admin)"//Role Name
             }
          }
       }
    ]

## List the advertisers ##
List advertisers data for the specified network.

    GET /networks/:network_id/advertisers

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "advertiser_id": 10933,//Advertiser ID
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10933",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //Advertiser Name
        "status": "enabled",//Advertise's status
        "alias": "腾讯",//Advertise's Alias
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //Creation Time
      }
    ]

## List the campaigns ##

List campaigns for the specified advertiser in authorized network.

    GET /networks/:network_id/advertisers/:advertiser_id/campaigns

**Parameters**

`name`
: _Optional_ **string** - Campaign Name

If the input is a part of campaign name, it will search the campaign.

`network_brand_id`
: _Optional_ **integer** - Network Brand ID

`status`
: _Optional_ *Enum* - Campaign Status

  * `all` - All Status, (_Default_)
  * `typing` - Typing
  * `testing` - Testing
  * `kickoff` - Beginning Period
  * `midterm` - Medium-term
  * `teminal` - Terminal
  * `finished` - Finished

`start_date`
: _Optional_ **date** - Beginning date to retrieve data in format YYYY-MM-DD. Listing campaigns which beginning date earlier than `start_date`.

`end_date`
: _Optional_ **date** - Final date to retrieve data in format YYYY-MM-DD. Listing campaigns which final date later than `end_data`.

`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `id` - Sorting occurs by campaign id.
  * `network_brand_id` - Sorting occurs by network brand id.
  * `name` - Sorting occurs by campaign name.
  * `total_cost` - Sorting occurs by total cost.
  * `media_num` - Sorting occurs by`media_num`.
  * `placement_num` - Sorting occurs by `placement_num`.
  * `start_date` - Sorting occurs by beginning date.
  * `end_date` - Sorting occurs by final date.
  * `est_imp` - Sorting occurs by estimate impression.
  * `est_clk` - Sorting occurs by estimate click.

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/12/advertisers/10282/campaigns?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/12/advertisers/10282/campaigns?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [

      {
        "id": 10903,//Campaign ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10903",
        "name": "This is a testing campaign",//Campaign Name
        "network_brand_id": 18,//Network Brand ID
        "cost_type": "CNY",//The `cost_type` that was performed: “CNY” , “USD” or "None".
        "total_cost": 20000000,//Total cost of campaign
        "start_date": "2012-01-03",//Beginning date of campaign
        "end_date": "2012-06-23",//Final date of campaign
        "default_target": "http://www.admaster.com.cn"
        "media_num": 8,//The number of media in the campaign 
        "placement_num": 258,//The number of placements in the campaign
        "est_imp": 9183213,//Estimate of impression
        "est_clk": 12334,//Estimate of click
        "status": "kickoff",//Status of campaign 
        "is_online": "yes",//If the current time is between `start_date` and `end_date plus seven days`, the data of `is_online` is "yes". 
        "created_at": "2012-09-06T20:39:23Z"//Creation time of campaign
      }
    ]

## Get the campaign report ##

[Campaign Report](/doc/trackmaster/v1/en/campaign_report.html)
 
## More information 

[TrackMaster Index](/doc/trackmaster/v1/en/index.html)

[Protocal and Requests Instructions](/doc/openmaster/v1/en/verbs.html)




