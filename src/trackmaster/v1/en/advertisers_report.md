---
weight: 12
layout: default
category: trackmaster
subcategory: advertisers
language: en
title: Advertiser Report
version: v1
---

# Advertiser Report

* TOC
{:toc}


## Get the advertiser report

    GET /advertisers/campaigns/:campaign_id/reports

**Parameters**

`time`
: _Required_ **string**  

	It is connected with `start_time` and `end_time`.

  * `hourly` Get hourly unique data.
  * `daily` Get daily unique data.


`dims`
: _Optional_ **string** - The dimensions parameter defines the primary data keys for your Campaign report. Use dimensions to segment your metrics. If you want to ask for several dimensions, you should use ','. Example : media , placement, time. 
  
  *  `time` - The result will contains date messages.
  *  `media`    
  *  `placement` 
  *  `keyword` 
  *  `creative` 
  *  `provinve` 


When using dimensions in a feed request, be aware of the following constraints:

* You can not send a query comprised only of dimensions: you must combine any requested dimension with at least one metric.
* Any given dimension can be used with other dimensions or metrics, but only certain dimensions and metrics can be used together to create valid combinations. 

`network_media_id`
: _Optional_ **integer** - Network Media ID

`placement_id`
: _Optional_ **integer** - Placement ID

`keyword_id`
: _Optional_ **integer** - Keyword ID

`creative_id`
: _Optional_ **integer** - Creative ID

`geo_id`
: _Optional_ **integer** - Geography ID

`start_time`
: _Optional_ **hour** - Listing campaigns which beginning time date earlier than `start_date`. The format of `start_time` is connected with `time`.The parament  `start_time` is formatted according to the ISO 8601 standard.

time | start_time   | description
hourly   | YYYY-MM-DDThh:mm:ss+08:00   | 2012-11-06T01:00:00+08:00
daily    | YYYY-MM-DD     | 2012-11-06


`end_time`
: _Optional_ **hour** - Listing campaigns which final date later than `end_time`. The format of `end_time` is connected with `time`.The parament `end_time` is formatted according to the ISO 8601 standard.

time | end_time   | description
hourly   | YYYY-MM-DDThh:mm:ss+08:00   | 2012-11-06T01:00:00+08:00
daily    | YYYY-MM-DD     | 2012-11-06



`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `time` - Sorting occurs by time.
  * `imp` - Sorting occurs by impression.
  * `clk` - Sorting occurs by click.
  * `uimp` - Sorting occurs by unique impression.
  * `uclk` - Sorting occurs by unique click.
  * `network_media_id` - Sorting occurs by `network_media_id`
  * `placement_id` - Sorting occurs by `placement_id`

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend


**响应**

    Status: 200 OK
    

{:.prettyprint}
      {
        "campaign_id": 10185,//Campaign ID
        "network_media_id": 1484,//Network Media ID
        "time": "2012-08-03",//The parament `time` is formatted according to the ISO 8601 standard and `start_time`.
        "imp": 90,//Impression
        "uimp": 60,//Unique Impression
        "clk": 30,//Click
        "uclk": 23,//Unique Click
      }


**Dimensions Description**

Field | Type     | Description
imp      | integer     | Impression
uimp     | integer     | Unique Impression
clk      | integer     | Click
uclk     | integer     | Unique Click

**Valid Combinations Description**  
Not all combinations can be queried together. Only certain combinations can be used together to create valid combinations. 


|Valid Combinations
|time=daily
|time=daily&dims=province
|time=daily&dims=creative 
|time=daily&dims=media
|time=daily&dims=media,province
|time=daily&dims=media,creative 
|time=daily&dims=media,placement
|time=daily&dims=media,placement,province
|time=daily&dims=media,placement,creative 
|time=daily&dims=media,placement,keyword 
|time=hourly 
|time=hourly&dims=creative 
|time=hourly&dims=province 
|time=hourly&dims=media 
|time=hourly&dims=media,creative 
|time=hourly&dims=media,province 
|time=hourly&dims=media,placement 
|time=hourly&dims=media,placement,creative 
|time=hourly&dims=media,placement,province



**Example**

dims contain time

{:.prettyprint}
    [
        {
            "campaign_id": 10116,
            "time": "2012-11-01",
            "imp": 3,
            "uimp": 3,
            "clk": 7,
            "uclk": 7,
        },
        {
            "campaign_id": 10116,
            "time": "2012-11-02",
        …
    ]

dims without time

{:.prettyprint}
    [
        {
            "campaign_id": 10116,
            "imp": 28,
            "uimp": 27,
            "clk": 72,
            "uclk": 39,
        }
    ]
