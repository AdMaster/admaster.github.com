---
weight: 5
layout: default
category: trackmaster
subcategory: publisher
language: en
title: Keyword
---

# Keyword

* TOC
{:toc}

## List keywords of the given placement

	GET /medias/placements/:placement_id/keywords

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
            "name": Example
            //Target URL
            "target_url": http://www.admaster.com.cn
            //Creation Time
            "created_at": "2012-12-27T15:45:27Z"
        }


## Get keywords details of the given placement

    GET /medias/placements/:placemment_id/keywords/:id

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
            "name": Example
            //Target URL
            "target_url": http://www.admaster.com.cn
            //Creation Time
            "created_at": "2012-12-27T15:45:27Z"
        }

