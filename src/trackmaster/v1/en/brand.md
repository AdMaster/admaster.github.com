---
weight: 3
layout: default
category: trackmaster
subcategory: agency
language: en
title: Brand
version: v1
---

# Brand #

* TOC
{:toc}


## Get brands of advertiser in the authorized network

    GET /networks/:network_id/advertisers/:advertiser_id/brands

**Parameters**

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

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

    Status: 200
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
