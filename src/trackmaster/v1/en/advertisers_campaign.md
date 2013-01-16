---
weight: 5
layout: default
category: trackmaster
subcategory: advertisers
language: en
title: Campaign
---

# Campaign

* TOC
{:toc}

##List campaigns of the given advertiser

	GET /advertisers/:advertiser_id/campaigns

**Response**
    
    Status: 200 OK

{:.prettyprint}
    [

      {
        "id": 10786,//Campaign ID
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
    ]

## Get details of the given campaign 
	
	GET /advertisers/campaigns/:id

**Response**

    Status: 200 OK

{:.prettyprint}
    [

	{
        "id": 10786,//Campaign ID
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
	]