---
weight: 10
layout: default
category: trackmaster
subcategory: publisher
language: en
title: Placement
---

#Placement

* TOC
{:toc}

## List placements of the given publisher

    GET /medias/:media_id/placements

**Parameters**

`media_id`
: _Required_ **integer** - Media ID   
If the input is a part of placement name, it will search the placement.

`name`
: _Optional_ **string** - Placement Name


`page`
: _Optional_ **integer** - the start index  
  
If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results     

You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/100/placements?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/100/placements?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //Placement ID
        "id": 200057486,
        //Placement Name
        "name": "A Testing Placement",
        //Channel Information
        "channel": {
       //Channel ID
        "id": 1025,
        //Channel Name
        "name": "Sport News",
        //Type-`webpage`,`video`,`client`,`se` Search Engine,`email`,`other` 
        "type": "webpage",
        //Which screen the placement is in
        "screen": 3,
        //Channel Website
        "home": "http://www.admaster.com.cn/",
        //Material Type -`flash`(Default)，`image`，`video`, `textlink`, `other`
        "material_type": 'flash',
        //Material Dimension
        "material_dimension": "400x300",
        //Material Size
        "material_size": 200,
        //Material Unit，B K(Default) M
        "material_size_unit": "B"
    },
        //Target URL(Click)
        "target_url": "http://www.admaster.com.cn/",
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
       //Campaign ID
        "campaign_id":1000
      }
    ]


## Get details of the given placement

    GET /medias/placements/:placement_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
    //Placement ID
    "id": 200057486,
    //Placement Name
    "name": "A Testing Placement",
    //Channel Information
    "channel": {
       //Channel ID
        "id": 1025,
        //Channel Name
        "name": "Sport News",
        //Type-`webpage`,`video`,`client`,`se` Search Engine,`email`,`other` 
        "type": "webpage",
        //Which screen the placement is in
        "screen": 3,
        //Channel Website
        "home": "http://www.admaster.com.cn/",
        //Material Type -`flash`(Default)，`image`，`video`, `textlink`, `other`
        "material_type": 'flash',
        //Material Dimension
        "material_dimension": "400x300",
        //Material Size
        "material_size": 200,
        //Material Unit，B K(Default) M
        "material_size_unit": "B"
    },
    //Target URL(Click)
    "target_url": "http://www.admaster.com.cn/",
    //Creation Time
    "created_at": "2012-09-06T20:39:23Z"
    //Campaign ID
    "campaign_id":1000

    }
