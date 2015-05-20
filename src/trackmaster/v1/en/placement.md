---
weight: 8
layout: default
category: trackmaster
subcategory: agency
language: en
title: Placement
version: v1
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
      [{
        //Placement ID
        "id": 20000006,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/20000006",
        //Campaign ID
        "campaign_id": 10000,
        //Placement Name
        "name": "Testing Placement",
        //Network media ID
        "network_media_id": 1314, 
        //Rotation- `1/1`(Default),`1/2`...
        "rotation" : "1/1",
        //Target URL(Click)
        "target_url": "http://www.admaster.com.cn/",
        //Payment Type- `purchase`,`offering`,`framework`,`compensation`,`other`
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
        //Cor Estimate Impression
        "sp_imp": 61821,
        //Cor Estimate Click
        "sp_clk": 300,
        //Total Impression
        "real_imp": 71821,
        //Total Click
        "real_clk": 400,
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z",
        //Channel ID
        "channel_id":1000,
        //Channel Name
        "channel_name": "banner",
        //Placement Type-`webpage`,`video`,`client`,`se` Search Engine,`email`,`other`
        "type": "webpage",
        //Which screen the placement is in
        "screen": 3,
        //Placement URL
        "page_url": "http://www.admaster.com.cn/",
        //Material Type- `flash`(Default),`image`,`video`, `textlink`, `other` 
        "material_type": "flash",
        //Material Dimension
        "material_dimension": "400x300",
        //Material Size
        "material_size": 200,
        //Material Unit，B KB(Default) MB
        "material_size_unit": "KB"
      }]

## Get details of the given placement

    GET /networks/advertisers/campaigns/placements/:id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //Placement ID
        "id": 20000006,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/20000006",
        //Campaign ID
        "campaign_id": 10000,
        //Placement Name
        "name": "Testing Placement",
        //Network media ID
        "network_media_id": 1314, 
        //Rotation- `1/1`(Default),`1/2`...
        "rotation" : "1/1",
        //Target URL(Click)
        "target_url": "http://www.admaster.com.cn/",
        //Payment Type- `purchase`,`offering`,`framework`,`compensation`,`other`
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
        //Cor Estimate Impression
        "sp_imp": 61821,
        //Cor Estimate Click
        "sp_clk": 300,
        //Total Impression
        "real_imp": 71821,
        //Total Click
        "real_clk": 400,
        //Creation Time
        "created_at": "2012-09-06T20:39:23Z",
        //Channel ID
        "channel_id":1000,
        //Channel Name
        "channel_name": "banner",
        //Placement Type-`webpage`,`video`,`client`,`se` Search Engine,`email`,`other`
        "type": "webpage",
        //Which screen the placement is in
        "screen": 3,
        //Placement URL
        "page_url": "http://www.admaster.com.cn/",
        //Material Type- `flash`(Default),`image`,`video`, `textlink`, `other` 
        "material_type": "flash",
        //Material Dimension
        "material_dimension": "400x300",
        //Material Size
        "material_size": 200,
        //Material Unit，B KB(Default) MB
        "material_size_unit": "KB"
    }

## Add a placement to the given campaign

    POST /networks/advertisers/campaigns/:campaign_id/placements

**Parameters**

`name`
: _Required_ **string** - Placement Name

`network_media_id`
: _Required_ **string** - Network Media ID

`page_url`
: _Required_ **string** - Placement URL，Example:"http://www.admaster.com.cn/"

`channel_id`
: _Optional_ **integer** - Channel ID 

`type`
: _Optional_ **string** - Placement Type

  * `webpage` WebPage _Default_
  * `video` Video
  * `client` Client
  * `se` Search Engine
  * `email` Email
  * `other` Other

`screen`:
: _Optional_ **integer** - Which screen the placement is in


`material_type`
: _Optional_ **string** - Material Type 

  * `flash` _Default_
  * `image`
  * `video`
  * `textlink`
  * `other` 

`material_dimension`
: _Optional_ **string** - Material Dimension

`material_size`
: _Optional_ **integer** -Material Size
 
`material_size_unit`  
: _Optional_ **string** -Material Unit

  * `B`
  * `KB`_Default_
  * `MB`    

`rotation`
: _Optional_ **string** - Rotation,`1/1`(Default),`1/2`...

`target_url`
: _Optional_ **string** - Target URL(Click) inherits campaign's target website. Null(Default)

	Please keep target_url correct, click code will point to this address.

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
        "name": "Testing Placement",
        "network_media_id": 1314,
        "channel_id":1000,
        "channel_name": "banner",
        "type": "webpage",
        "screen": 3,
        "page_url":"http://www.sina.com.cn/"
        "material_type": "flash",
        "material_dimension": "400x300",
        "material_size": 30,
        "material_size_unit": "KB",    
        "rotation" : "1/1",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873,
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
        "campaign_id": 10000,
        "name": "Testing Placement",
        "network_media_id": 1314,    
        "rotation" : "1/1",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "units": 0,
        "other_requirement": "Null",
        "est_imp": 0,
        "est_clk": 0,
        "sp_imp": 0,
        "sp_clk" 0,
        "real_imp": 0,
        "real_clk": 0,
        "created_at": "2012-09-06T20:39:23Z",
        "is_online": 0,
        "page_url":"http://www.sina.com.cn/",
        "type": "webpage",
        "channel_id":1000,
        "channel_name": "banner",
        "screen": 3,       
        "material_type": "flash",
        "material_dimension": "400x300",
        "material_size": 30,
        "material_size_unit": "KB",  
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

`type`
: _Optional_ **string** - Placement Type

  * `webpage` WebPage _Default_
  * `video` Video
  * `client` Client
  * `se` Search Engine
  * `email` Email
  * `other` Other

`screen`:
: _Optional_ **integer** - Which screen the placement is in

`page_url`
: _Optional_ **string** - Placement URL，Example:"http://www.admaster.com.cn/"

`material_type`
: _Optional_ **string** - Material Type 

  * `flash` _Default_
  * `image`
  * `video`
  * `textlink`
  * `other` 

`material_dimension`
: _Optional_ **string** - Material Dimension

`material_size`
: _Optional_ **integer** -Material Size
 
`material_size_unit`  
: _Optional_ **string** -Material Unit

  * `B`
  * `KB`_Default_
  * `MB`    

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
        "name": "Testing Placement",
        "network_media_id": 1314,
        "channel_id":1000,
        "channel_name": "banner",
        "type": "webpage",
        "screen": 3,
        "page_url":"http://www.sina.com.cn/"
        "material_type": "flash",
        "material_dimension": "400x300",
        "material_size": 30,
        "material_size_unit": "KB",    
        "rotation" : "1/1",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "Null",
    }

**Response**

    Status: 200
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
