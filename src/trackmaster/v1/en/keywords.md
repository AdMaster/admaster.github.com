---
weight: 5
layout: default
category: trackmaster
subcategory: agency
language: en
title: Keyword
version: v1
---

# Keyword

* TOC
{:toc}

## List keywords of the given placement

    GET /networks/advertisers/campaigns/placements/:placement_id/keywords

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
        {
            //Placement ID
            "placement_id":1
            //Keyword ID
            "order_num":1
            //Keyword Name
            "name": example
            //Target URL
            "target_url": http://www.admaster.com.cn
            //Creation Time
            "created_at": "2012-12-27T15:45:27Z"
        }


## Get keywords details of the given placement

    GET /networks/advertisers/campaigns/placements/:placement_id/keywords/:keyword_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
        {
            //Placement ID
            "placement_id":1
            //Keyword ID
            "order_num":1
            //Keyword Name
            "name": example
            //Target URL
            "target_url": http://www.admaster.com.cn
            //Creation Time
            "created_at": "2012-12-27T15:45:27Z"
        }

## Add keyword to the given placement

    POST /networks/advertisers/campaigns/placements/:placement_id/keywords

The number of keywords' URLs in a placement must not exceed 100.


**Parameters**

`name`
: _Required_ **string** - Keyword Name

`target_url`
: _Optional_ **string** - Target URL


**Request**

{:.prettyprint}
    	{
        	"name": "keyword name"
        	"target_url": "http://www.admaster.com.cn"
    	}

**Response**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/keywords/1
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}	
	 {
        //Placement ID
        "placement_id":1
        //Keyword ID
        "order_num":1
        //Keyword Name
        "name": this is example
        //Target URL
        "target_url": http://www.admaster.com.cn
        //Creation Time
        "created_at": "2012-12-27T15:45:27Z"
    }


## Modify keyword of the given placement

    PATCH /networks/advertisers/campaigns/placements/:placement_id/keywords/:keyword_id

**Parameters**

`name`
: _Required_ **string** - Keyword Name

`target_url`
: _Optional_ **string** - Target URL

**Request**

{:.prettyprint}
    	{
        	"name": "keyword name"
        	"target_url": "http://www.admaster.com.cn"
    	}

**Response**

    Status: 200
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999



## Delete the given keyword

    DELETE /networks/advertisers/campaigns/placements/:placement_id/keywords/:keyword_id


**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1/keywords
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4996



