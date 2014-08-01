---
weight: 1
layout: default
category: trackmaster
subcategory: agency
language: en
title: Network
version: v1
---

# Network

* TOC
{:toc}

## Get authorized networks

    GET /user/networks

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       {
        "id": 11,//Network ID
        "url": "https://api.trackmaster.com.cn/networks/11",
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

## Get details of the given network

    GET /networks/:id

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers>; rel="advs"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
      "id": 11,//Network ID
      "url": "https://api.trackmaster.com.cn/networks/11",
      "name": "Testing Network",//Network Name
      "created_at": "2012-09-06T20:39:23Z" //Creation Time
    }
