---
weight: 5
layout: default
category: trackmaster
subcategory: agency
language: en
title: Brand
---

# Brand #

* TOC
{:toc}


## Get brands of advertiser in the authorized network

    GET /networks/:network_id/advertisers/:advertiser_id/brands

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


{:.prettyprint}
    [
      {
        "id": 30,//Network Brand ID
        "name": "巧乐兹",//Brand Name
        "created_at": "2012-09-06T20:39:23Z"//Creation Time
      }
    ]


## Get details of brand

    GET /networks/advertisers/brands/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 30,//Network Brand ID
        "network_id": 11,//Network ID
        "advertiser_id": 10231,//Advertiser ID
        "name": "巧乐兹",//Advertiser Name
        "url": "http://{{site.track_api_host}}/networks/advertisers/brands/30",
        "created_at": "2012-09-06T20:39:23Z"//Creation Time
    }


## Add a brand to the given advertiser 

    POST /networks/:network_id/advertisers/:advertiser_id/brands

**Request**

    {
        "name": "巧乐兹"
    }

`name`
: _Required_ **string** - Brand Name

**Response**

    Status: 201 Created 
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 30,//Network Brand ID
        "network_id": 11,//Network ID
        "advertiser_id": 10231,//Advertiser ID
        "name": "巧乐兹",//Advertiser Name
        "url": "http://{{site.track_api_host}}/networks/advertisers/brands/30",
        "created_at": "2012-09-06T20:39:23Z"//Creation Time
    }


## Modify brand name of the given advertiser 

    PATCH /networks/advertisers/brands/:id

**Request**

{:.prettyprint}
    {
        "name": "巧乐鸡"
    }

`name`
: _Required_ **string** - Brand Name


**Response**

    Status: 204 No Content 
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Delete brand of the given advertiser

    DELETE /networks/advertisers/brands/:id

When the brand which you want to delete connects campaigns, it can not be deleted. 

**Response**

{:.prettyprint}
    Status: 204 No Content 
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
