---
weight: 6
layout: default
category: trackmaster
subcategory: advertisers
language: en
title: Creative
---

# Creative

* TOC
{:toc}

##List creatives of the given campaign

    GET /advertisers/campaigns/:campaign_id/creatives

**Response**

    Status: 200 OK

{:.prettyprint}
	{
        //Creative ID
        "id": 2000000,
        //Creative Name
        "name": "Creative A",
        //Creative Shortname
        "shortname": "GO",
        //Description
        "description": "Null",
        //Target Website
        "target_url": "http://www.admaster.com.cn/",
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
	}


##Get details of the given creative

    GET /advertisers/campaigns/creatives/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //Creative ID
        "id": 200000271,
        //Creative Name
        "name": "Creative A",
        //Creative Shortname
        "shortname": "GO",
        //Description
        "description": "Null",
        //Target Website
        "target_url": "http://www.admaster.com.cn/",
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
    }
