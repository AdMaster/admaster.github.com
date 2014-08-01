---
weight: 4
layout: default
category: trackmaster
subcategory: advertisers
language: en
title: Media
version: v1
---

# Media

* TOC
{:toc}

## List media of the given advertiser

    GET /advertisers/:advertiser_id/medias

**Response**

    status: 200 ok

{:.prettyprint}
	{
        "id": 400,//System Media ID
        "name": "Sina",//System Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z",
        "status": "enabled"
	}


##Get details of the given advertisers

    GET /advertisers/:advertiser_id/medias/:media_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 400,//System Media ID
        "name": "Sina",//System Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z",
        "status": "enabled"
    }


##Get details of system media in the given network media ID  

    GET /advertisers/:advertiser_id/networks/medias/:network_media_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 400,//System Media ID
        "url": "http://{{site.track_api_host}}/medias/400",
        "name": "Sina",//System Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z",
        "status": "enabled"
    }
