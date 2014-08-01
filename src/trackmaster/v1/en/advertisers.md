---
weight: 15
layout: default
category: trackmaster
language: en
title: Advertiser
version: v1
---


# TrackMaster API for Advertisers

* TOC
{:toc}


TrackMaster provides an API for programmatic access to account data. All API access is over HTTP. All data is sent and received as JSON.

TrackMaster APIs use the OAuth 2.0 protocol for authentication and authorization.

All developers need to register their application before getting started. A registered OAuth application is assigned a unique `client_id` and `client_secret`. The client_secret should not be shared.

Please read more about [OAuth](http://dev.admaster.com.cn/doc/openmaster/v1/en/oauth.html) and [Protocal and Requests Instructions](http://dev.admaster.com.cn/doc/openmaster/v1/en/verbs.html).

## Get the access_token

Before your application can access a TrackMaster API, it must obtain an access token that grants access to that API.

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

Access tokens have a limited lifetime and, in some cases, an application needs access to a TrackMaster API beyond the lifetime of `expires_in`. In this case, your application can obtain what is called a refresh token. A refresh token and some parameters allow your application to obtain new access tokens. 

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## List the campaigns

    GET http://track.admasterapi.com/advertisers/:advertiser_id/campaigns

**Parameters**

The `access_token` you received as a response to `Getting the access_token`.

    access_token=***

**Response**

    [
      {
        "id": 1,
        "name": "Testing campaign",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## Get the advertiser report 

    GET /advertisers/campaigns/:campaign_id/reports

**Parameters**

`time`
: _Required_ **string**  
It is connected with `start_time` and `end_time`.

  * `hourly` Get hourly unique data.
  * `daily` Get daily unique data.

`dims`
: _Optional_ **string** - The dimensions parameter defines the primary data keys for your Campaign report. Use dimensions to segment your metrics. If you want to ask for several dimensions, you should use ','. Example : media , placement, time. 
  
  *  `media`    
  *  `placement` 
  *  `keyword` 
  *  `creative` 
  *  `province` 
  *  `time` 

When using dimensions in a feed request, be aware of the following constraints:

* You can not send a query comprised only of dimensions: you must combine any requested dimension with at least one metric.
* Any given dimension can be used with other dimensions or metrics, but only certain dimensions and metrics can be used together to create valid combinations. 

`network_media_id`
: _Optional_ **integer** - Network Media ID

`placement_id`
: _Optional_ **integer** - Placement ID

`keyword_id`
: _Optional_ **integer** - Keyword ID

`creative_id`
: _Optional_ **integer** - Creative ID

`geo_id`
: _Optional_ **integer** - Geography ID

`start_time`
: _Optional_ **hour** - Listing campaigns which beginning time date earlier than `start_date`. The format of `start_time` is connected with `time`.The parament  `start_time` is formatted according to the ISO 8601 standard.

time | start_time   | description
hourly   | YYYY-MM-DDThh:mm:ss+08:00   | 2012-11-06T01:00:00+08:00
daily    | YYYY-MM-DD     | 2012-11-06


`end_time`
: _Optional_ **hour** - Listing campaigns which final date later than `end_time`. The format of `end_time` is connected with `time`.The parament `end_time` is formatted according to the ISO 8601 standard.

time | end_time   | description
hourly   | YYYY-MM-DDThh:mm:ss+08:00   | 2012-11-06T01:00:00+08:00
daily    | YYYY-MM-DD     | 2012-11-06


`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `time` - Sorting occurs by time.
  * `imp` - Sorting occurs by impression.
  * `clk` - Sorting occurs by click.
  * `uimp` - Sorting occurs by unique impression.
  * `uclk` - Sorting occurs by unique click.
  * `network_media_id` - Sorting occurs by `network_media_id`
  * `placement_id` - Sorting occurs by `placement_id`

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend


**响应**

    Status: 200 OK
    

{:.prettyprint}
    [
      {
        "campaign_id": 10185,//Campaign ID
        "network_media_id": 1484,//Network Media ID
        "time": "2012-08-03",//The parament `time` is formatted according to the ISO 8601 standard and `start_time`.
        "imp": 90,//Impression
        "uimp": 60,//Unique Impression
        "clk": 30,//Click
        "uclk": 23,//Unique Click
      }
    ]



## More information 

[TrackMaster Index](/doc/trackmaster/v1/en/index.html)

[Protocal and Requests Instructions](/doc/openmaster/v1/en/verbs.html)

