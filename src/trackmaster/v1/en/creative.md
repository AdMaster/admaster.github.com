---
weight: 5
layout: default
category: trackmaster
subcategory: agency
language: en
title: Creative
---

# Creative

* TOC
{:toc}

## List creatives of the given campaign

    GET /networks/advertisers/campaigns/:campaign_id/creatives

**Parameters**

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/creatives?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/creatives?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      {
        //Creative ID
        "id": 200000271,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/200000271",
        //Creative Name
        "name": "A Good Creative",
        //Creative Shortname
        "shortname": "GO",
        //Description
        "description": "This is a good creative",
        //Color Identifier
        "color": "#ff00ff",
        //Attachment file
        "file": {
            "id": 293,
            "name": "creative.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //Target Website
        "target_url": "http://www.admaster.com.cn/",
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
      }


## Get creative details of the given campaign

    GET /networks/advertisers/campaigns/creatives/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //Creative ID
        "id": 200000271,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/200000271",
        //Creative Name
        "name": "Creative A",
        //Creative Shortname
        "shortname": "GO",
        //Description
        "description": "Null",
        //Color Identifier
        "color": "#ff00ff",
        //Attachment file
        "file": {
            "id": 293,
            "name": "creative.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //Target Website
        "target_url": "http://www.admaster.com.cn/",
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
    }


## Add a creative to the given campaign

    POST /networks/advertisers/campaigns/:campaign_id/creatives

**Parameters**

`name`
: _Required_ **string** - Creative Name

`shortname`
: _Required_ **string** - Creative Shortname

`color`
: _Required_ **string** - Color Identifier, Example：`#ff00ff`.

`description`
: _Optional_ **string** - Description

`file_id`
: _Optional_ **integer** - Attachment ID

`target_url`
: _Optional_ **string** - Target Website

**Request**

{:.prettyprint}
    {
        "name": "A Good Creative",
        "shortname": "GO",
        "description": "This is a good creative",
        "color": "#ff00ff",
        "file_id": 123,
        "target_url": "http://www.admaster.com.cn/",
    }

**Response**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/200000271
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //Creative ID
        "id": 200000271,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/2000002711",
        //Creative Name
        "name": "A Good Creative",
        //Creative Shortname
        "shortname": "GO",
        //Description
        "description": "This is a good creative",
        //Color Identifier
        "color": "#ff00ff",
        //Attachment File
        "file": {
            "id": 123,
            "name": "creative.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //Target Website
        "target_url": "http://www.admaster.com.cn/",
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
    }

## Delete the given creative

    DELETE /networks/advertisers/campaigns/creatives/:id

When the creative's data which you want to delete is not "0", the creative's data will be changed as "0".   
When the creative's data which you want to delete is "0", it can not be deleted. 
 

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/123/creatives
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## Modify details of the given creative

    PATCH /networks/advertisers/campaigns/creatives/:id

**Parameters**

`name`
: _Required_ **string** - Creative Name

`shortname`
: _Required_ **string** - Creative Shortname

`color`
: _Optional_ **string** - Color Identifier, Example：`#ff00ff`

`description`
: _Optional_ **string** - Description

`file_id`
: _Optional_ **integer** - Creative ID

`target_url`
: _Optional_ **string** - Target Website

**Request**

{:.prettyprint}
    {
        "name": "A Good Creative",
        "shortname": "GO",
        "description": "This is a good creative",
        "color": "#ff00ff",
        "file_id": 123,
        "target_url": "http://www.admaster.com.cn/",
    }

**Response**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

