---
weight: 11
layout: default
category: trackmaster
subcategory: agency
language: en
title: Campaign Report
---

# Campaign Report

* TOC
{:toc}

## Get the authorized campaign report  

    GET /campaigns/:campaign_id/reports

**Parameters**

`time`
: _Required_ **string**  
It is connected with `start_time` and `end_time`.

  * `hourly` Get hourly unique data.
  * `daily` Get daily unique data.
  * `weekly` Get weekly unique data.
  * `monthly` Get monthly unique data.

`dims`
: _Optional_ **string** - The dimensions parameter defines the primary data keys for your Campaign report. Use dimensions to segment your metrics. If you want to ask for several dimensions, you should use ','. Example : media , placement, time. 
  
  *  `media`    
  *  `placement` 
  *  `keyword` 
  *  `creative` 
  *  `geo` 
  *  `time` 

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
hourly   | YYYY-MM-DDThh:mmZ   | 2012-11-06T01:57Z
daily    | YYYY-MM-DD     | 2012-11-06
weekly   | YYYY-Www     | 2005-W01
monthly  | YYYY-MM     | 2005-01


`end_time`
: _Optional_ **hour** - Listing campaigns which final date later than `end_time`. The format of `end_time` is connected with `time`.The parament `end_time` is formatted according to the ISO 8601 standard.

time | end_time   | description
hourly   | YYYY-MM-DDThh:mmZ   | 2012-11-06T01:57Z
daily    | YYYY-MM-DD     | 2012-11-06
weekly   | YYYY-Www     | 2005-W01
monthly  | YYYY-MM     | 2005-01


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


**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,//Campaign ID
        "network_media_id": 1484,//Network Media ID
        "time": "2012-08-03",//The parament `time` is formatted according to the ISO 8601 standard and `start_time`.
        "imp": 90,//Impression
        "uimp": 60,//Unique Impression
        "ipuimp": 56,//Unique Impression IP
        "clk": 30,//Click
        "uclk": 23,//Unique Click
        "ipuclk": 22//Unique Click IP
      }
    ]


**Dimensions Description**

Field | Type     | Description
imp      | integer     | Impression
uimp     | integer     | Unique Impression
ipuimp   | integer     | Unique Impression IP
clk      | integer     | Click
uclk     | integer     | Unique Click
ipuclk   | integer     | Unique Click IP

**Valid Combinations Description**  
Not all combinations can be queried together. Only certain combinations can be used together to create valid combinations. 


|Valid Combinations
|time=daily
|time=daily&dims=geo
|time=daily&dims=creative 
|time=daily&dims=media
|time=daily&dims=media,geo
|time=daily&dims=media,creative 
|time=daily&dims=media,placement
|time=daily&dims=media,placement,geo
|time=daily&dims=media,placement,creative 
|time=daily&dims=media,placement,keyword 
|time=hourly 
|time=hourly&dims=creative 
|time=hourly&dims=geo 
|time=hourly&dims=media 
|time=hourly&dims=media,creative 
|time=hourly&dims=media,geo 
|time=hourly&dims=media,placement 
|time=hourly&dims=media,placement,creative 
|time=hourly&dims=media,placement,geo
|time=hourly&dims=media,placement,keyword
|time=monthly
|time=monthly&dims=media
|time=monthly&dims=media,placement
|time=monthly&dims=media,placement,keyword
|time=weekly
|time=weekly&dims=media
|time=weekly&dims=media,placement
|time=weekly&dims=media,placement,keyword

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
            "ipuimp": 3,
            "ipuclk": 4
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
            "ipuimp": 27,
            "ipuclk": 24
        }
    ]
