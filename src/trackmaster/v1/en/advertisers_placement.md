---
weight: 9
layout: default
category: trackmaster
subcategory: advertisers
language: en
title: Placement
version: v1
---

#Placement

* TOC
{:toc}

##List placements of the given advertiser

    GET /advertisers/campaigns/:campaign_id/placements


**Parameters**

`advertiser_id`
: _Required_ **integer** - Advertiser ID

`name`
: _Optional_ **string** - Placement Name

	If the input is a part of placement name, it will search the placement.

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK

{:.prettyprint}
      [{
        //Placement ID
        "id": 20000006,
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

    GET /advertisers/campaigns/placements/:placements_id

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      [{
        //Placement ID
        "id": 20000006,
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