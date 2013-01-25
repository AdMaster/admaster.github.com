---
weight: 13
layout: default
category: trackmaster
subcategory: publisher
language: en
title: Publisher Report
---

# Publisher Report

* TOC
{:toc}

## List campaigns of the given media

    GET /medias/:media_id/campaigns

**Response**

    Status: 200 OK

{:.prettyprint}
    [
      {
        "id": 10185,//Campaign ID
        "name": "Testing Campaign",//Campaign Name
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]

## Get daily report of the given campaign

    GET /medias/:media_id/campaigns/:campaign_id/daily_reports

**Parameters**

`start_time`
: _Optional_ **date** - Beginning date to retrieve data in format YYYY-MM-DD. Listing campaigns which beginning date earlier than `start_date`.

`end_time`
: _Optional_ **date** - Final date to retrieve data in format YYYY-MM-DD. Listing campaigns which final date later than `end_data`.

`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `time` - Sorting occurs by time.
  * `imp` - Sorting occurs by impression.
  * `clk` - Sorting occurs by click.
  * `uimp` - Sorting occurs by unique impression.
  * `uclk` - Sorting occurs by unique click.

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend

**Response**

    Status: 200 OK


{:.prettyprint}
    [
      {
        "time": "2012-08-01", 
        "imp": 23, 
        "uimp": 20, 
        "clk": 20, 
        "uclk": 10, 
      }
    ]


## Get daily report of the given code 

    GET /medias/campaigns/daily_reports/codes

**Parameters**

`code`
: _Required_ **string** - Monitoring code

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/medias/1308/campaigns/10256/daily_reports
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Get campaign report of the given code

    GET /medias/campaigns/reports/codes

**Parameters**

`code`
: _Required_ **string** - Monitoring code

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/medias/1308/campaigns/10256/reports
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Get iab data 

    GET /medias/:id/ies

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/1/ies?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/1/ies?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

**Parameters**

`pubid`
: _Optional_ **string** 


`date`
: _Optional_ **date** - Date of the form YYYY-MM-DD

If not supplied, the date is yesterday. The parament `date` is formatted according to the ISO 8601 standard.

`page`
: _Optional_ **integer** - the start index
       
If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

{:.prettyprint}
    [
      {
        "date_hour": 2012061015,
        "pubid": "IYK_IMloxnwepMEqlx",
        "city": "北京",
        "geoid": 110000,
        "impression": 12039423,
        "click": 43432,
      }
    ]

## Get campaign report of the given media

    GET /medias/:media_id/campaigns/:campaign_id/reports

**Parameters**

`time`
: _Required_ **string**          
It is connected with `start_time` and `end_time`.

  * `hourly` Get hourly unique data
  * `daily` Get daily unique data.
  * `weekly` Get weekly unique data.
  * `monthly` Get monthly unique data.

`dims`
: _Optional_ **string** - The dimensions parameter defines the primary data keys for your Campaign report. Use dimensions to segment your metrics. If you want to ask for several dimensions, you should use ‘,’. Example : media , placement, time.

  * `placement` 
  * `keyword` 
  * `creative` 
  * `geo` 
  * `time`     


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
hourly   | YYYY-MM-DDThh:mm+08:00   | 2012-11-06T01:57+08:00
daily    | YYYY-MM-DD     | 2012-11-06
weekly   | YYYY-Www     | 2005-W01
monthly  | YYYY-MM     | 2005-01

`end_time`
: _Optional_ **hour** - Listing campaigns which final date later than `end_time`. The format of `end_time` is connected with `time`.The parament `end_time` is formatted according to the ISO 8601 standard.

time | end_time   | description
hourly   | YYYY-MM-DDThh:mm+08:00   | 2012-11-06T01:57+08:00
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
  * `placement_id` - Sorting occurs by `placement_id`

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend


**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/1/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/1/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,
        "time": "2012-08-03",
        "imp": 9,
        "uimp": 6,
        "ipuimp": 6,
        "clk": 3,
        "uclk": 3,
        "ipuclk": 2
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
|time=daily&dims=placement
|time=daily&dims=placement,geo
|time=daily&dims=placement,keyword
|time=daily&dims=placement,creative 
|time=hourly
|time=hourly&dims=creative 
|time=hourly&dims=geo
|time=hourly&dims=placement
|time=hourly&dims=placement,creative 
|time=hourly&dims=placement,geo
|time=hourly&dims=placement,keyword
|time=monthly
|time=monthly&dims=placement
|time=monthly&dims=placement,keyword
|time=weekly
|time=weekly&dims=placement
|time=weekly&dims=placement,keyword 

