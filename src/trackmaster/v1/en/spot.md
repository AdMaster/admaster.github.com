---
weight: 9
layout: default
category: trackmaster
subcategory: agency
language: en
title: Spot
---

# Spot

* TOC
{:toc}

## Get spots of the given campaign in a period of time

    GET /networks/advertisers/campaigns/:campaign_id/spots

**Parameters**

`start_date`
: _Required_ **date** - Beginning date to retrieve data in format YYYY-MM-DD.

`end_date`
: _Required_ **date** - Final date to retrieve data in format YYYY-MM-DD.

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.


**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/:campaign_id/spots?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/:campaign_id/spots?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      {
        //Placement ID
        "placement_id": 200019261,
        //Online Date
        "online_date": "2012-04-13",
        //Creative ID
        "creative_id": 200019827,
        //Perchase Unites
        "units": 23,
      }

## Modify the given spot

    PUT /networks/advertisers/campaigns/placements/:placement_id/spots/:date

**Request**

`units`
: _Required_ **integer** - Perchase Unites

`creative_id`
: _Optional_ **integer** - Creative ID

**Response**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

