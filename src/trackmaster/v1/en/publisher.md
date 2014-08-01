---
weight: 14
layout: default
category: trackmaster
language: en
title: Publisher
version: v1
---


# TrackMaster API for Publishers

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
      "email": "your@email.com",
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

    GET http://track.admasterapi.com/medias/:media_id/campaigns

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


## Get the media daily report 

    GET http://track.admasterapi.com/medias/:media_id/campaigns/:campaign_id/daily_reports

**Parameters**

`media_id`   
: _Required_ **Integer** - The media ID you received from TrackMaster.    

`campaign_id`    
: _Required_ **Integer** - The campaign ID you received from TrackMaster.      

`access_token=***`     

`start_time`    
: _Optional_ **Date**   
   
Beginning date to retrieve data in format YYYY-MM-DD. Example:2012-08-01，listing campaigns which beginning time earlier than  `start_time`.

`end_time`     
: _Optional_ **Date** 

Final date to retrieve data in format YYYY-MM-DD. Example:2012-08-02，listing campaigns which final time later than `end_time`.    

`sort`    
: _Optional_ **String** - The order to retrieve the results.

`direction`    
: _Optional_ **String** - The direction to retrieve the results.



**Response**

    Status: 200 OK
{:.prettyprint}
    [

      {
        "time": "2012-08-01", // time
        "imp": 23, //impression
        "uimp": 20, //unique impression
        "clk": 20, //click
        "uclk": 10, //unique click
      }
    ]



## More information

[TrackMaster Index](/doc/trackmaster/v1/en/index.html)

[Protocal and Requests Instructions](/doc/openmaster/v1/en/verbs.html)
