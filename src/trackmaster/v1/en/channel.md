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

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/channels?page=2>; rel="next",
          <http://{{site.track_api_host}}/channels?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
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
    ]

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


