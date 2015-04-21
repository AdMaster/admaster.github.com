---
weight: 14
layout: default
category: trackmaster
language: en
title: Agency
version: v2
---


# TrackMaster API for Agency #

* TOC
{:toc}



TrackMaster APIs use the OAuth 2.0 protocol for authentication and authorization. This API provided for accessing authorised data in programming. Rules:1. API requests will only be accepted via HTTP.2. When using HTTP, the content-type may be defined as application/json . You can send and receive data encoded as JSON.  3. All developers need to have their own application and TrackMaster account before getting started. 4. The TrackMaster account and application information can be got from our company(TrackMaster).5. Every registered OAuth application is assigned a unique `client_id` and `client_secret`. The `client_secret` should not be shared!You can get more informations in our User Guide  [TrackMaster Index](/doc/trackmaster/v2/en/index.html).



# Guides #

## Get your access_token ##

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


The lifetime of an `access_token` is limited. The connection between application and TrackMaster API based on the lifetime of `expires_in` in some cases. 
The application can request a new token by invoking a reconnect method with some parameters in those cases.


**Paremeters**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## List the authorized networks ##

    GET http://m.trackmaster.com.cn/api_v2/session

**Response**

{:.prettyprint}
    {
        "id": 1, 
        "name": "xxx", 
        "role": "user", 
        "email": "xxx@admaster.com.cn", 
        ... 
        "networks": {
            "11": {
                "id": 72, 
                "networkId": 11, 
                "userId": 1, 
                "roleId": 11, 
                "expiredAt": "2020-11-18T00:00:00.000Z", 
                "status": "enabled", 
                "isOwnAllCampaign": "no", 
                "isDelete": "no", 
                "createdAt": "2014-11-18T08:31:29.000Z", 
                "updatedAt": "2014-12-18T08:52:16.000Z", 
                "network": {
                    ...
                    "id": 11, 
                    "name": "AdMaster", 
                    "creator": "xxx@admaster.com.cn", 
                    "status": "enabled", 
                    "campaigns": 168, 
                    "campaignLimit": 10000, 
                    "users": 88, 
                    "userLimit": 100, 
                    "expiredAt": "2020-11-29T00:00:00.000Z", 
                    "isDelete": "no", 
                    "createdAt": "2014-10-29T02:23:25.000Z", 
                    "updatedAt": "2015-03-05T09:02:45.000Z"
                }, 
                ...
            }, 
            "70": {
                "id": 0, 
                "networkId": 70, 
                "network": {
                    ...
                    "id": 70, 
                    "name": "Name xxx", 
                    "creator": "xxx@admaster.com.cn", 
                    "status": "enabled", 
                    "campaigns": 0, 
                    "campaignLimit": 5000, 
                    "users": 6, 
                    "userLimit": 200, 
                    "expiredAt": "2025-01-01T00:00:00.000Z", 
                    "isDelete": "no", 
                    "createdAt": "2014-08-01T10:15:31.000Z", 
                    "updatedAt": "2015-02-26T04:06:02.000Z"
                }
            }
        }
    }

    ]


## List the authorized campaigns ##

    GET http://m.trackmaster.com.cn/api_v2/networks/:networkId/campaigns

Note: For vertify permission, the `queryString` must contain `access_token`.

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
    "placements":20 // the actual number of existed placements(Maximum:500)
    }]


# More information #

[TrackMaster Index](/doc/openmaster/v1/en/index.html)  
[Protocal and Requests Instructions](/doc/openmaster/v1/en/verbs.html)




