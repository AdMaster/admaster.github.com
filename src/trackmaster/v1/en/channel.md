---
weight: 6
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


## Add a channel to the given media

    POST /medias/:media_id/channels

**Parameters**

`name`
: _Required_ **string** - Channel Name

`type`
: _Optional_ **string** - Channel Type

  * `webpage`
  * `video`
  * `client`
  * `se`： Search Engine
  * `email`
  * `other`

`screen`
: _Optional_ **string** - Which screen the placement is in

`home`
: _Optional_ **string** - Channel Website

`material_type`
: _Optional_ **string** - Material Type 

  * `flash`(Default)
  * `image`
  * `video`
  * `textlink`
  * `other`

`material_dimension`
: _Optional_ **string** - Material Dimension

`material_size`
: _Optional_ **enum** - Material Size

`material_size_unit`
: _Optional_ **string** - Material Unit

  * `B`:Byte
  * `K`:Kbyte (Default)
  * `M`:Mbyte

**Request**

{:.prettyprint}
    {
        //Channel Name
        "name": "Sport News",
        //Type-`webpage`,`video`,`client`,`se` Search Engine,`email`,`other` 
        "type": "webpage",
        //Which screen the placement is in
        "screen": 3,
        //Channel Website
        "home": "http://www.admaster.com.cn/",
        //Material Type- `flash`(Default)，`image`，`video`, `textlink`, `other` 
        "material_type": 'flash',
        //Material Dimension
        "material_dimension": "400x300",
        //Material Size
        "material_size": 200,
        //Material Unit，B K(Default) M
        "material_size_unit": "B"
    }


**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/channel/123
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
