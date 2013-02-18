---
weight: 7
layout: default
category: trackmaster
subcategory: agency
language: en
title: Channel
---

# Channel

* TOC
{:toc}


## List channels of the given media

    GET /medias/:media_id/channels

**Parameters**

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/channels?page=2>; rel="next",
          <http://{{site.track_api_host}}/channels?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       {
            //Channel ID
            "id": 1025,
            //Channel Name
            "name": "Sport News",
            //`webpage`,`video`,`client`,`se` Search Engine,`email`,`other` 
            "type": "web",
            //Which screen the placement is in
            "screen": 3,
            //Channel Website
            "home": "http://www.admaster.com.cn/",
            //Material Type `flash`，`image`，`video`, `textlink`, `other` ,`flash`(Default)
            "material_type": 'flash',
            //Material Dimension
            "material_dimension": "400x300",
            //Material Size
            "material_size": 200,
            //Material Unit，B K(Default) M
            "material_size_unit": "B"
        }

## Get details of the given channel

    GET /medias/channels/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
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
    }


