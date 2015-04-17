---
weight: 1
layout: default
category: trackmaster
subcategory: agency
language: en
version: v2
title: Network
---

# Network

* TOC
{:toc}

## List the authorized networks ##

    GET http://m.trackmaster.com.cn/api_v2/session

**Response**

Note:`networks` means  the authorized networks.

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

## Network datails

    GET http://m.trackmaster.com.cn/api_v2/networks/:id

**Response**

{:.prettyprint}
      {
        "id": 999, //Network ID
        "name":"Test", // Network Name
        "status": enabled,
        "campaignLimit":999, //Maximum number of campaigns
        "userLimit": 999, //Maximum number of users
        "expiredAt": 2080-09-19 00:00:00 //Expiration date
      }
      
  