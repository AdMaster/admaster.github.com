---
weight: 6
layout: default
category: trackmaster
subcategory: agency
language: en
title: Media
---

# Media

* TOC
{:toc}

## List system media

    GET /medias

**Parameters**

`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `id` - Sorting occurs by media id
  * `name` - Sorting occurs by media name
  * `create_time` - Sorting occurs by creation time

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.


**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      {
        "id": 400,//System Media ID
        "url": "http://{{site.track_api_host}}/medias/400",
        "name": "Sina",//System Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "status": "enabled",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
      }


## Get details of the given system media

    GET /medias/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 400,//System Media ID
        "url": "http://{{site.track_api_host}}/medias/400",
        "name": "Sina",//System Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "status": "enabled",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
    }


## List media of the given network

    GET /networks/:network_id/medias

**Parameters**

`name`
: _Optional_ **string** - Network Media Name


`domain`
: _Optional_ **string** - Media Domain

`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `id` - Sorting occurs by network media id.
  * `name` - Sorting occurs by network media name.
  * `status` - Sorting occurs by `status`.
  * `framework` - Sorting occurs by `framework`.

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/11/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/11/medias/1314",
        "name": "Sina",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled",
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//System Media ID
        "framework": "no"
      }


## Get details of the given system media ID in the authorized network

    GET /networks/:network_id/medias/:media_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/11/medias/1314",
        "name": "Sina",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled",
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//System Media ID
        "framework": "no"
    }


## Add a media to the given network

    POST /networks/:network_id/medias

If the status of media is disabled, you can not add this media to network.

**Request**

{:.prettyprint}
    {
        'media_id': 400
    }

`media_id`: _Required_ **integer** - System Media ID

**Response**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/11/medias/2
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/11/medias/1314",
        "name": "Sina",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled",
        "created_at": "2012-09-06T20:39:23Z",
        "media_id": 400//System Media ID
        "framework": "no"
    }

## Get details of the given network media ID

    GET /networks/medias/:network_media_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/11/medias/1314",
        "name": "Sina",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled",
        "created_at": "2012-09-06T20:39:23Z",
        "media_id": 400, //System Media ID
        "framework": "no"
    }

## Delete media of the given network

    DELETE /networks/medias/:id

When the media which you want to delete has campaigns, it can not be deleted.

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/11/medias
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Modify details of media in the given network

    PATCH /networks/:network_id/medias/:media_id

**Request**

{:.prettyprint}
    {
        "name": "新浪财经",//Network Media Name
        "framework": "no",
        "status": "enabled"
    }

`name`
: _Optional_ **string** - Network Media Name

`framework`
: _Optional_ **enum** -  `yes`, `no`



**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/1/medias/1314",
        "name": "新浪财经",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled",
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//System Media ID
        "framework": "no"
    }


## List media of the given campaign

    GET /networks/advertisers/campaigns/:campaign_id/medias/attributes

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/1314",
        "name": "Sina",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "created_at": "2012-09-06T20:39:23Z",
        "status": "enabled"
      }
    ]

## Get details of the given media in the authorized campaign

    GET /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id/attributes

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,//Network Media ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/1314",
        "name": "Sina",//Network Media Name
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "created_at": "2012-09-06T20:39:23Z",
        "status": "enabled"
    }

## Match a media in the given campaign

    GET /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

**Response**

Match

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

No Match

    Status: 404 Not Found
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Add a media to the given campaign

    PUT /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

If the status of media is disabled, you can not add this media to campaign. 

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/2010/attributes
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Delete a media in the given campaign

    DELETE /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

When the media which you want to delete has placements, it can not be deleted.

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/attributes
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
