---
weight: 8
layout: default
category: trackmaster
subcategory: agency
language: en
title: Placement
---

#Placement

* TOC
{:toc}

## List placements of the given campaign

    GET /networks/advertisers/campaigns/:campaign_id/placements

**Parameters**

`name`
: _Optional_ **string** - Placement Name

If the input is a part of placement name, it will search the placement.

`network_media_id`
: _Optional_ **integer** - Network Media ID

`page`
: _Optional_ **integer** - the start index

If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //Placement ID
        "id": 200057486,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/200057486",
        //Placement Name
        "name": "This is a testing Placement",
        //Network Media ID
        "network_media_id": 1314,
        //Channel Information
        "channel": {
            //Channel ID
            "id": 1025,
            //Channel Name
            "name": "Sport News",
            //Type-`webpage`,`video`,`client`,`se` Search Engine,`email`,`other`
            "type": "web",
            //Which screen the placement is in
            "screen": 3,
            //Channel Website
            "home": "http://www.admaster.com.cn/",
            //Material Type- `flash`(Default),`image`,`video`, `textlink`, `other` 
            "material_type": "flash",
            //Material Dimension
            "material_dimension": "400x300",
            //Material Size
            "material_size": 200,
            //Material Unit，B K(Default) M
            "material_size_unit": "B"
        }
        //Rotation- `1/1`(Default),`1/2`...
        "rotation" : "1/4",
        //Target URL(Click)
        "target_url": "http://www.admaster.com.cn/",
        //Payment Type- `purchase`,`offering`,`framework`,`Compensation`,`other`
        "payment_type": "purchase",
        //Cost Type-`day`,`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`kmail`,`other`
        "cost_type": "day"
        //Cost(per_unit)
        "cost_per_unit": 873.12,
        //Estimate Impression(per_unit)
        "est_imp_per_unit": 239,
        //Estimate Click(per_unit)
        "est_clk_per_unit": 3,
        //Units
        "units": 58,
        //Other Requirement
        "other_requirement": "Null",
        //Estimate Impression(total)
        "est_imp": 871821,
        //Estimate Click(total)
        "est_clk": 1231,
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## Get details of the given placement

    GET /networks/advertisers/campaigns/placements/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
    //Placement ID
    "id": 200057486,
    "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/200057486",
    //Placement Name
    "name": "This is a testing Placement",
    //Network Media ID
    "network_media_id": 1314,
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
        //Material Type- `flash`(Default),`image`,`video`, `textlink`, `other`
        "material_type": "flash",
        //Material Dimension
        "material_dimension": "400x300",
        //Material Size
        "material_size": 200,
        //Material Unit，B K(Default) M
        "material_size_unit": "B"
    },
    //Rotation- `1/1`(Default),`1/2`...
    "rotation" : "1/4",
    //Target URL(Click)
    "target_url": "http://www.admaster.com.cn/",
    //Payment Type- `purchase`,`offering`,`framework`,`Compensation`,`other`
    "payment_type": "purchase",
    //Cost Type-`day`,`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`kmail`,`other`
    "cost_type": "day"
    //Cost(per_unit)
    "cost_per_unit": 873.12,
    //Estimate Impression(per_unit)
    "est_imp_per_unit": 239,
    //Estimate Click(per_unit)
    "est_clk_per_unit": 3,
    //Units
    "units": 58,
    //Other Requirement
    "other_requirement": "Null",
    //Estimate Impression(total)
    "est_imp": 871821,
    //Estimate Click(total)
    "est_clk": 1231,
    //Creation Time
    "created_at": "2012-09-06T20:39:23Z"
    }

## Add a placement to the given campaign

    POST /networks/advertisers/campaigns/:campaign_id/placements

**Parameters**

`name`
: _Required_ **string** - Placement Name

`network_media_id`
: _Required_ **string** - Network Media ID

`channel_id`
: _Required_ **integer** - Channel ID

`rotation`
: _Optional_ **string** - Rotation,`1/1`(Default),`1/2`...

`target_url`
: _Optional_ **string** - Target URL(Click) inherits campaign's target website. Null(Default)


`payment_type`
: _Optional_ **string** - Payment Type

  * `purchase` _Default_
  * `offering`
  * `framework`
  * `Compensation`
  * `other`

`cost_type`
: _Optional_ **string** - Cost Type

  * `day` _Default_
  * `week` 
  * `month` 
  * `cpc` 
  * `cpm` 
  * `cpa` 
  * `article` 
  * `kmail` 
  * `other`  

`cost_per_unit`
: _Optional_ **float** - Cost(per_unit)

`est_imp_per_unit`
: _Optional_ **integer** - Estimate Impression(per_unit)

`est_clk_per_unit`
: _Optional_ **integer** - Estimate Click(per_unit)

`other_requirement`
: _Optional_ **string** - Other Requirement

**Request**

{:.prettyprint} 
    {
        "name": "This is a Testing Placement",
        "network_media_id": 1314,
        "channel_id": 123,
        "rotation" : "1/4",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873.12,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "Null",
    }
    
**Response**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 200057486,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/200057486",
        "name": "This is a Testing Placement",
        "network_media_id": 1314,
        "channel": {
            "id": 123,
            "name": "Sport News",
            "type": "webpage",
            "screen": 3,
            "home": "http://www.admaster.com.cn/",
            "material_type": "flash",
            "material_dimension": "400x300",
            "material_size": 200,
            "material_size_unit": "B"
        },
        "rotation" : "1/4",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873.12,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "units": 0,
        "other_requirement": "Null",
        "est_imp": 40000,
        "est_clk": 3000,
        "created_at": "2012-09-06T20:39:23Z"
    }

## Delete the given placement

    DELETE /networks/advertisers/campaigns/placements/:id

When the placement which you want to delete has impression or click data, it can not be deleted.

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/placements
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Modify details of the given placement

    PATCH /networks/advertisers/campaigns/placements/:id

**Request**

`name`
: _Optional_ **string** - Placement Name

`channel_id`
: _Optional_ **integer** - Channel ID

`rotation`
: _Optional_ **string** - Rotation,`1/1`(Default),`1/2`...

`target_url`
: _Optional_ **string** - Target URL(Click) inherits campaign's target website. Null(Default)

`payment_type`
: _Optional_ **string** - Cost Type

  * `purchase` _Default_
  * `offering` 
  * `framework` 
  * `Compensation` 
  * `other` 

`cost_type`
: _Optional_ **string** - Cost Type 

  * `day`  _Default_
  * `week` 
  * `month` 
  * `cpc` 
  * `cpm` 
  * `cpa` 
  * `article` 
  * `kmail` 
  * `other` 

`cost_per_unit`
: _Optional_ **float** - Cost(per_unit)

`est_imp_per_unit`
: _Optional_ **integer** - Estimate Impression(per_unit)

`est_clk_per_unit`
: _Optional_ **integer** - Estimate Click(per_unit)

`other_requirement`
: _Optional_ **string** - Other Requirement

**Request**

{:.prettyprint}
    {
        "name": "This is a Testing Placement",
        "channel_id": 123,
        "rotation" : "1/4",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873.12,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "Null",
    }

**Response**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
