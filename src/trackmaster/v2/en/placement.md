---
weight: 5
layout: default
category: trackmaster
subcategory: agency
language: en
title: placement
version: v2
---

#Placement

* TOC
{:toc}

## List placements

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/placements

**Response**

{:.prettyprint}
    [
        {
        "id": 999,//Placement ID
        "name": //Placement Name
        "mediaId": 999, // Media ID
        "campaignId": 999, // Campaign ID
        "channelName": // Channel Name
        "targetUrl":"http://www.sdf.com" // Target URL
        "rollRate": 1, //Value:`1`,`1/2`…
        "materialType":"image", //Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`
        "size":"0x0", //Material Size
        "screen":1, //Which screen the placement in   		"costType":"day",//Purchase Type. Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`
        "estimateImp":999, //Estimate Impression(per_unit)
        "estimateClk":999 //Estimate Click(per_unit)
        }
    ]


## Placement details

    GET http://m.trackmaster.com.cn/api_v2/placements/:id

**Response**

{:.prettyprint}
        {
        "id": 999,//Placement ID
        "name": //Placement Name
        "mediaId": 999, // Media ID
        "campaignId": 999, // Campaign ID
        "channelName": // Channel Name
        "targetUrl":"http://www.sdf.com" // Target URL
        "rollRate": 1, //Value:`1`,`1/2`…
        "materialType":"image", //Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`
        "size":"0x0", //Material Size
        "screen":1, //Which screen the placement in   		"costType":"day",//Purchase Type. Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`
        "estimateImp":999, //Estimate Impression(per_unit)
        "estimateClk":999 //Estimate Click(per_unit)

        }

## Add a placement

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/placements

Note: Maximum number of placement to creat in the same campaign is 400.

**Paremeters**

`name`
: _Required_  Placement Name

`campaignId`
: _Required_  Campaign ID. This paremeter can not be modified.

`mediaId`
: _Required_  Media ID. It must has been in the campaign paremeter `mediaIds`, or it will not add a new placement. This paremeter can not be modified.

`channelName`
: _Optional_  Channel Name

`targetUrl`
: _Optional_  Target URL. Target URL(Click) inherits campaign’s target website. Please keep target_url is correct, click code will point to this address.

`rollRate`
: _Optional_  Rotation.Value:`1`,`1/2`…

`materialType`
: _Optional_  Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`

`size`
: _Optional_  Material Size

`screen`
: _Optional_  Which screen the placement in

`costType`
: _Optional_  Purchase Type. Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`

`estimateImp`
: _Optional_  Estimate Impression(per_unit)

`estimateClk`
: _Optional_  Estimate Click(per_unit)


**Request**


{:.prettyprint} 
    {
        "name": //Placement Name
        "mediaId": 999, // Media ID
        "campaignId": 999, // Campaign ID
        "channelName": // Channel Name
        "targetUrl":"http://www.sdf.com" // Target URL
        "rollRate": 1, //Value:`1`,`1/2`…
        "materialType":"image", //Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`
        "size":"0x0", //Material Size
        "screen":1, //Which screen the placement in   		"costType":"day",//Purchase Type. Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`
        "estimateImp":999, //Estimate Impression(per_unit)
        "estimateClk":999 //Estimate Click(per_unit)
    }
    
**Response**

{:.prettyprint}
    {
        "id": 999,//Placement ID
        "name": //Placement Name
        "mediaId": 999, // Media ID
        "campaignId": 999, // Campaign ID
        "channelName": // Channel Name
        "targetUrl":"http://www.sdf.com" // Target URL
        "rollRate": 1, //Rotation.1,1/2…
        "materialType":"image", //Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`
        "size":"0x0", //Material Size
        "screen":1, //Which screen the placement is in   		"costType":"day",//Purchase Type.Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`
        "estimateImp":999, //Estimate Impression(per_unit)
        "estimateClk":999 //Estimate Click(per_unit)
    }

## Update placement

    PATCH http://m.trackmaster.com.cn/api_v2/placements/:id

Note: Only submitted paremeters will be updated.

**Paremeters**

`name`
: _Required_  Placement Name


`channelName`
: _Optional_  Channel Name

`targetUrl`
: _Optional_  Target URL. Target URL(Click) inherits campaign’s target website. Please keep target_url is correct, click code will point to this address.

`rollRate`
: _Optional_  Rotation.Value:`1`,`1/2`…

`materialType`
: _Optional_  Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`

`size`
: _Optional_  Material Size

`screen`
: _Optional_  Which screen the placement in

`costType`
: _Optional_  Purchase Type. Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`

`estimateImp`
: _Optional_  Estimate Impression(per_unit)

`estimateClk`
: _Optional_  Estimate Click(per_unit)


**Request**

{:.prettyprint}
    {
        "name": //Placement Name
        "channelName": // Channel Name
        "targetUrl":"http://www.sdf.com" // Target URL
        "rollRate": 1, //Rotation.1,1/2…
        "materialType":"image", //Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`
        "size":"0x0", //Material Size
        "screen":1, //Which screen the placement is in   		"costType":"day",//Purchase Type.Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`
        "estimateImp":999, //Estimate Impression(per_unit)
        "estimateClk":999 //Estimate Click(per_unit)
    }

**Response**

{:.prettyprint}
    {
        "id": 999,//Placement ID
        "name": //Placement Name
        "mediaId": 999, // Media ID
        "campaignId": 999, // Campaign ID
        "channelName": // Channel Name
        "targetUrl":"http://www.sdf.com" // Target URL
        "rollRate": 1, //Rotation.1,1/2…
        "materialType":"image", //Material Type. Value:`falsh`,`image`(default),`video`,`txt`,`other`
        "size":"0x0", //Material Size
        "screen":1, //Which screen the placement is in   		"costType":"day",Type.Value:`day`(default),`week`,`month`,`cpc`,`cpm`,`cpa`,`article`,`edm`,`other`
        "estimateImp":999, //Estimate Impression(per_unit)
        "estimateClk":999 //Estimate Click(per_unit)
    }
    
## Delete a placement

    DELETE http://m.trackmaster.com.cn/api_v2/placements/:id

Note:That it will not delete an existed placement, if the placement has data.


**Response**

    Status: 204 OK

