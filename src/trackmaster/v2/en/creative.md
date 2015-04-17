---
weight: 6
layout: default
category: trackmaster
subcategory: agency
language: cn
title: creative
version: v2
---

# Creative

* TOC
{:toc}

## List creatives 

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/creatives

**Response**

{:.prettyprint}
    [{
        "id": 999,//Creative ID
        "name": // Creative Name
        "shortName"://Creative Shortname. Limite:2 characters
        "targetUrl"://Target URL
        "campaignId": 999 // Campaign ID
    }]


## Creative details

    GET http://m.trackmaster.com.cn/api_v2/creatives/:id

**Response**

{:.prettyprint}
    {
        "id": 999,//Creative ID
        "name": // Creative Name
        "shortName"://Creative Shortname. Limite:2 characters
        "targetUrl"://Target URL
        "campaignId": 999, // Campaign ID
    }


## Add a creative

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/creatives

Note:Maximum number of creative to creat is 20 in the same campaign.

**Paremeters**

`name`
: _Required_  Creative Name

`shortName`
: _Required_  Creative Shortname. Limite:2 characters

`targetUrl`
: _Optional_  Target URL



{:.prettyprint}
    {
        "name": // Creative Name
        "shortName"://Creative Shortname. Limite:2 characters
        "targetUrl"://Target URL
    }

**Response**

{:.prettyprint}
    {
        "id": 999,//Creative ID
        "name": // Creative Name
        "shortName"://Creative Shortname. Limite:2 characters
        "targetUrl"://Target URL
        "campaignId": 999, // Campaign ID
    }



## Update creative

    PATCH http://m.trackmaster.com.cn/api_v2/creatives/:id

Note: Only submitted paremeters will be updated.

**Paremeters**

`name`
: _Optional_  Creative Name

`shortName`
: _Optional_  Creative Shortname. Limite:2 characters

`targetUrl`
: _Optional_  Target URL


{:.prettyprint}
    {
        "id": 999,//Creative ID
        "name": // Creative Name
        "shortName"://Creative Shortname. Limite:2 characters
        "targetUrl"://Target URL
    }

**Response**

{:.prettyprint}
    {
        "id": 999,//Creative ID
        "name": // Creative Name
        "shortName"://Creative Shortname. Limite:2 characters
        "targetUrl"://Target URL
        "campaignId": 999, // Campaign ID
    }


## Delete creative

    DELETE http://m.trackmaster.com.cn/api_v2/creatives/:id

Note: The code which connected a user-defined creative will be changed to the default creative code when the user-defined creative is deleted. 

**Response**

    Status: 204 OK