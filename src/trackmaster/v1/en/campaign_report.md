---
weight: 12
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

  * `hourly` Get hourly unique data.
  * `daily` Get daily unique data.
  * `weekly` Get weekly unique data.
  * `monthly` Get monthly unique data.

`dims`
: _Required_ **string** - The dimensions parameter defines the primary data keys for your Campaign report. Use dimensions to segment your metrics.

  * `media` 
  * `placement` 
  * `keyword` 
  * `creative` 
  * `geo` 
  * `time` 

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
: _Optional_ **hour** - Beginning date to retrieve data in format YYYY-MM-DD. Listing campaigns which beginning time date than  `start_date`.

`end_time`
: _Optional_ **hour** - Final date to retrieve data in format YYYY-MM-DD. Listing campaigns which final data later than  `end_data`.

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
    Link: <http://{{site.track_api_host}}/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,
        "network_media_id": 1484,
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

