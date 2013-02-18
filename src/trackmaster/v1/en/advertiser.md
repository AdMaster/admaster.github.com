---
weight: 2
layout: default
category: trackmaster
subcategory: agency
language: en
title: Advertiser
---

# Advertiser

* TOC
{:toc}

## List advertisers of the authorized network

    GET /advertisers

**Parameters**

`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `id` - Sorting occurs by advertiser id.
  * `create_time` - Sorting occurs by `create_time`.

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
    Link: <http://{{site.track_api_host}}/advertisers?page=2>; rel="next",
          <http://{{site.track_api_host}}/advertisers?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 10199,//Advertiser ID
        "url": "http://{{site.track_api_host}}/advertisers/10199",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //Advertiser Name
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //Creation Time
      }
    ]


## Get details of the advertiser

    GET /advertisers/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 10199,//Advertiser Name
        "url": "http://{{site.track_api_host}}/advertisers/10199",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //Advertiser Name
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //Creation Time
    }


## List details of advertisers in the authorized network

    GET /networks/:network_id/advertisers

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "network_id":11,//Network ID
	    "advertiser_id": 10198,//Advertiser Name
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10198",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //Advertiser Name
        "status": "enabled",//Advertiser's Status
        "alias": "tencent",//Advertiser's Alias
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //Creation Time
      }
    ]

## Get details of the advertiser in the authorized network

    GET /networks/:network_id/advertisers/:advertiser_id

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10198/campaigns>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "network_id":11,//Network ID
        "advertiser_id": 10198,
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10198",
        "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //Advertiser Name
        "status": "enabled",//Advertiser's Status
        "alias": "通用电器",//Advertiser's Alias
        "logo": "http://www.trackmaster.com.cn/data/advIcon/GM.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z" //Creation Time
        "creator":"name"//Creator
    }

## Add an advertiser to the given network

    PUT /networks/:network_id/advertisers/:advertiser_id

**Response**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10198/campaigns>; rel="campaigns"
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10198
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Modify details of advertiser in the given network

    PATCH /networks/:network_id/advertisers/:advertiser_id

**Request**

{:.prettyprint}
    {
        "alias": "通用电器",
        "status": "enabled"
    }


`alias`
: _Optional_ **string** - Alias

`status`
: _Optional_ `enabled`, `disabled`

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10198/campaigns>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "advertiser_id": 10198,//Advertiser ID
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10198",
        "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //Advertiser Name
        "status": "enabled",//Advertiser's Status
        "alias": "通用电器",//Advertiser's Alias
        "logo": "http://www.trackmaster.com.cn/data/advIcon/GM.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z" //Creation Time
    }

## Delete advertiser of the given network

    DELETE /networks/:network_id/advertisers/:advertiser_id

When the advertiser which you want to delete has campaigns, it can not be deleted.

**Response**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/networks/11/advertisers>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

