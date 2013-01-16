---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: en
title: Campaign
---

# Campaign

* TOC
{:toc}

## List campaigns of the given advertiser in the authorized network

    GET /networks/:network_id/advertisers/:advertiser_id/campaigns

**Parameters**

`name`
: _Optional_ **string** - Campaign Name

If the input is a part of campaign name, it will search the campaign.

`network_brand_id`
: _Optional_ **integer** - Network Brand ID

`status`
: _Optional_ *Enum* - Campaign Status

  * `all` - All Status, (_Default_)
  * `typing` - Typing
  * `testing` - Testing
  * `kickoff` - Beginning Period
  * `midterm` - Medium-term
  * `teminal` - Terminal
  * `finished` - Finished

`start_date`
:  _Optional_ **date** - Beginning date to retrieve data in format YYYY-MM-DD. Listing campaigns which beginning date earlier than `start_date`.

`end_date`
: _Optional_ **date** - Final date to retrieve data in format YYYY-MM-DD. Listing campaigns which final date later than `end_data`.

`sort`
: _Optional_ **string** - The order to retrieve the results.

  * `id` - Sorting occurs by campaign id.
  * `network_brand_id` - Sorting occurs by network brand id.
  * `name` - Sorting occurs by campaign name.
  * `total_cost` - Sorting occurs by total cost.
  * `media_num` - Sorting occurs by`media_num`.
  * `placement_num` - Sorting occurs by `placement_num`.
  * `start_date` - Sorting occurs by beginning date.
  * `end_date` - Sorting occurs by final date.
  * `est_imp` - Sorting occurs by estimate impression.
  * `est_clk` - Sorting occurs by estimate click.

`direction`
: _Optional_ **string** - The direction to retrieve the results.

  * `asc` Ascend (_Default_)
  * `desc` Descend

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10282/campaigns?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/11/advertisers/10282/campaigns?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [

      {
        "id": 10786,//Campaign ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name":"This is a testing campaign",//Campaign Name
        "network_brand_id": 10213,//Network Brand ID
        "cost_type": "CNY",//The `cost_type` that was performed: “CNY” , “USD” or "None".
        "total_cost": 20000000,//Total cost of campaign
        "start_date": "2012-01-03",//Beginning date of campaign
        "end_date": "2012-06-23",//Final date of campaign
        "default_target": "http://www.admaster.com.cn"
        "media_num": 8,//The number of media in the campaign 
        "placement_num": 258,//The number of placements in the campaign
        "real_imp": 10187535,//Total Impression
        "real_clk": 13700,//Total Click
        "est_imp": 9183213,//Estimate Impression
        "est_clk": 12334,//Estimate Click
        "sp_imp": 753823,//Cor Estinate Impression
        "sp_clk": 15342,//Cor Estinate Click
        "status": "midterm",//Status of campaign
        "is_online": "yes",//If the current time is between `start_date` and `end_date plus seven days`, the data of `is_online` is "yes". 
        "created_at": "2012-09-06T20:39:23Z"//Creation time of campaign
      }
    ]


## Get details of the given campaign

    GET /networks/advertisers/campaigns/:id

**Response**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/medias/attributes>; rel="nwmedias"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 10786,//Campaign ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "Testing campaign",//Campaign Name
        "network_brand_id": 10213,//Network Brand ID
        "cost_type": "CNY",//The `cost_type` that was performed: “CNY” , “USD” or "None".
        "total_cost": 20000000,//Total cost of campaign
        "start_date": "2012-01-03",//Beginning date of campaign
        "end_date": "2012-06-23",//Final date of campaign
        "default_target": "http://www.admaster.com.cn"//Target Website
        "media_num": 8,//The number of media in the campaign 
        "placement_num": 258,//The number of placements in the campaign
        "target_audience":{//Target Audience
            "age": "19-25",//Age Groups
            "sex": "male"//Gender
        },
        "status": "midterm",//Status of campaign 
        "is_online": "yes",//If the current time is between `start_date` and `end_date plus seven days`, the data of `is_online` is "yes". 
        "created_at": "2012-09-06T20:39:23Z"//Creation time of campaign
    }


## Add the campaign to the given advertiser

    POST /networks/:network_id/advertisers/:advertiser_id/campaigns

**Parameters**

`name`
: _Required_ **string** - Campaign Name

`network_brand_id`
: _Required_ **integer** - Network Brand ID

`start_date`
: _Required_ **date** - Beginning date to retrieve data in format YYYY-MM-DD. 

`end_date`
: _Required_ **date** - Final date to retrieve data in format YYYY-MM-DD. 

`default_target`
: _Required_ **string** - Target Website.Example:http://www.admaster.com.cn/

`cost_type`
: _Optional_ **string** - Cost Type

  * `None` _Default_
  * `CNY` 
  * `USD` 

`target_audience`
: _Optional_ *Object* - Target Audience

{:.prettyprint}
    {
        "age": "19-25",//Age Groups
        "sex": "male"//Gender.The `sex` that was performed: “male”, “female”.
    }


**Request**

{:.prettyprint}
    {
        "name": "This is a testing campaign",//Campaign Name
        "network_brand_id": 10021,//Network Brand ID
        "start_date": "2012-01-31",//Beginning date
        "end_date": "2012-04-20",//Final date
        "default_target": "http://www.admaster.com.cn/",//Target Website
        "cost_type": "USD",//The `cost_type` that was performed: “CNY” , “USD” or "None".
        "target_audience": {//Target Audience
            "age": "16-30",//Age Groups
            "sex": "female"//Gender
        }
    }

**Response**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10786
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 10786,//Campaign Name
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "This is a testing campaign",//Campaign Name
        "network_brand_id": 10021,//Network Brand ID
        "cost_type": "USD",//The `cost_type` that was performed: “CNY” , “USD” or "None".
        "total_cost": 200000,//Total cost of campaign
        "start_date": "2012-01-31",//Beginning date
        "end_date": "2012-04-20",//Final date
        "default_target": "http://www.admaster.com.cn"
        "media_num": 4,//The number of media in the campaign 
        "placement_num": 7,//The number of placements in the campaign 
        "target_audience":{//Target Audience
            "age": "16-30",//Age Groups
            "sex": "female"//Gender
        },
        "status": "typing",//Status of campaign 
        "is_online": "no",
        "created_at": "2012-09-06T20:39:23Z"//Creation time of campaign
    }

**Field Description**

Get information near the bottom of the page.

## Modify details of the given campaign

    PATCH /networks/advertisers/campaigns/:id

**Parameters**

`name`
: _Optional_ **string** - Campaign Name

`network_brand_id`
: _Optional_ **integer** - Network Brand ID

`start_date`
: _Optional_ **date** - Beginning date to retrieve data in format YYYY-MM-DD. 

`end_date`
: _Optional_ **date** - Final date to retrieve data in format YYYY-MM-DD.

`default_target`
: _Optional_ **string** - Target Website.Example:http://www.admaster.com.cn/

`cost_type`
: _Optional_ **string** - Cost Type

  * `None`  _Default_
  * `CNY` 
  * `USD` 

`target_audience`
: _Optional_ *Object* - Target Audience

{:.prettyprint}
    {
        "age": "19-25",//Age Groups
        "sex": "male"//Gender
    }

**Request**

{:.prettyprint}
    {
        "name": "This is a testing campaign",//Campaign Name
        "network_brand_id": 10021,//Network Brand ID
        "start_date": "2012-01-31",//Beginning date
        "end_date": "2012-04-20",//Final date
        "default_target": "http://www.admaster.com.cn/",//Target Website
        "cost_type": "USD",//Cost Type
        "target_audience": {//Target Audience
            "age": "16-30",//Age Groups
            "sex": "female"//Gender
        }
    }

**Response**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999



## Delete the given campaign

    DELETE /networks/advertisers/campaigns/:id

When the campaign's status which you want to delete is not typing, the campaign's status will be changed as deleted.

When the campaign's status which you want to delete is typing, the campaign will be deleted.

**Response**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10282/campaigns
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## Field Description

Field         | Type | Description
id               | integer | Campaign ID
url              | string  | Request URL
name             | string  | Campaign Name
network_brand_id | integer | Network Brand ID
cost_type        | string  | Currency
total_cost       | integer | Total Cost
start_date       | date    | Beginning date
end_date         | date    | Final date
default_target   | date    | Target Website
media_num        | integer | The number of media
placement_num    | integer | The number of placements
status           | string  | Status
is_online        | string  | If the current time is between `start_date` and `end_date plus seven days`, the data of `is_online` is "yes". 
created_at       | date    | Creation

