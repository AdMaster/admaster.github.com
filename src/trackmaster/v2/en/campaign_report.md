---
weight: 12
layout: default
category: trackmaster
subcategory: agency
language: en
title: Campaign Report
version: v2
---

# Campaign Report


* TOC
{:toc}

## Campaign report

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:campaign_id/reports/basics

**Paremeters**

* `startDate` Required.Start date of required report
* `endDate` Required.End date of required report
* `metrics` Required.Data metrics. 
* `dimensions` Optional. Data dimensions. The dimensions parameter defines the primary data keys for your Campaign report. Use dimensions to segment your metrics. If you want to ask for several dimensions, you should use `,`.
* `filters` Filters can be chained. `;` - and,`,`- or. Example:filters=mediaId==1018;geoId==310021,placementId=50000012;imp>1000;clk>10
* `sort` The field which should be used to sort the results.Descending order:'-'.
* `startIndex` The start number of records to retrieve. Default: 0.
* `maxResults` The number of records to retrieve. Default:10, Maximum:5000. 

Header information `X-Content-Record-Total` means the number of total records.

**Response**

  {:.prettyprint}
	  [{
	  "date": "2014-07-11",
	  "media": 1018,
	  "imp": 12133323,
	  "clk": 7832
		}]


**Dimensions**

* media 
* placement
* keyword
* creative
* province
* city
* os  //Operating System:Android,IOS
* app 
* network //Network Type:WIFI,2G/3G
* deviceType //Device Type:Pad,Phone
* factory //Device Factory:Apple,Samsung
* model //Model:iPad mini,Samsung GALAXY Note II (N7100)
* date 
* hour 

**Avaliable dimensions combination**

Note:Not all combinations can be queried together. Only certain combination can be used together to create avaliable combinations.

* media
* placement
* creative
* province
* city
* os
* app
* network
* deviceType
* factory
* model
* date
* hour

* media, placement
* media, creative
* media, province
* media, city
* media, os
* media, app
* media, network
* media, deviceType
* media, factory
* media, model

* placement, keyword
* placement, creative
* placement, province
* placement, city
* placement, os
* placement, app
* placement, network
* placement, deviceType
* placement, factory
* placement, model

* media, placement, keyword
* media, placement, creative
* media, placement, province
* media, placement, city
* media, placement, os
* media, placement, app
* media, placement, network
* media, placement, deviceType
* media, placement, factory
* media, placement, model

* date, media
* date, placement
* date, creative
* date, province
* date, city
* date, os
* date, app
* date, network
* date, deviceType
* date, factory
* date, model

* date, media, placement
* date, media, creative
* date, media, province
* date, media, city
* date, media, os
* date, media, app
* date, media, network
* date, media, deviceType
* date, media, factory
* date, media, model

* date, placement, keyword
* date, placement, creative
* date, placement, province
* date, placement, city
* date, placement, os
* date, placement, app
* date, placement, network
* date, placement, deviceType
* date, placement, factory
* date, placement, model

* date, media, placement, keyword
* date, media, placement, creative
* date, media, placement, province
* date, media, placement, city
* date, media, placement, os
* date, media, placement, app
* date, media, placement, network
* date, media, placement, deviceType
* date, media, placement, factory
* date, media, placement, model

* hour, media
* hour, placement
* hour, creative
* hour, province
* hour, city

* hour, placement, keyword
* hour, placement, creative
* hour, placement, province
* hour, placement, city

* hour, media, placement, keyword
* hour, media, placement, creative
* hour, media, placement, province
* hour, media, placement, city




**Filters/Sort**

* Filter metrics must in selected metrics. 
* Metrics and Dimensions could be used to sort.


**Dimensions Description**

* imp:Impression
* clk:Click
* uimp:Unique Impression
* uclk:Unique Click

**Example**

dims=time

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

