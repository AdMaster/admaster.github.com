---
weight: 4
layout: default
category: trackmaster
subcategory: advertisers
language: en
title: Brand
version: v1
---

# Brand #

* TOC
{:toc}

##List brands of the given advertiser

    GET /advertisers/:advertiser_id/brands

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


{:.prettyprint}
	{
        "id": 30,//Network Brand ID
        "name": "巧乐兹",//Network Brand Name
        "created_at": "2012-09-06T20:39:23Z"//Creation Time
	}



##Get details of the given brand
    
    GET /advertisers/:advertiser_id/brands/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 30,//Network Brand ID
        "network_id": 11,//Network ID
        "advertiser_id": 10231,//Advertiser ID
        "name": "巧乐兹",//Network Brand Name
        "created_at": "2012-09-06T20:39:23Z"//Creation Time
    }