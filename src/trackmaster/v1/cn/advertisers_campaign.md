---
weight: 5
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 项目
---

# 项目

* TOC
{:toc}

##获取指定广告主的项目

	GET /advertisers/:advertiser_id/campaigns

**响应**
    
    Status: 200 OK

{:.prettyprint}
    [

      {
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "测试项目",//项目名称
        "network_brand_id": 10213,//项目网络品牌 ID
        "cost_type": "CNY",//媒体预算货币类型
        "total_cost": 20000000,//项目总费用
        "start_date": "2012-01-03",//项目开始时间
        "end_date": "2012-06-23",//项目结束时间
        "default_target": "http://www.admaster.com.cn"//项目默认点击目标地址
        "media_num": 8,//项目中媒体数目
        "placement_num": 258,//项目中广告位数目
        "target_audience":{//目标受众人群
            "age": "19-25",//目标受众人群年龄范围
            "sex": "male"//目标受众人群性别
        },
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
      }
    ]

## 获取指定项目信息
	
	GET /advertisers/:advertiser_id/campaigns/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    [

	{
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "测试项目",//项目名称
        "network_brand_id": 10213,//项目网络品牌 ID
        "cost_type": "CNY",//媒体预算货币类型
        "total_cost": 20000000,//项目总费用
        "start_date": "2012-01-03",//项目开始时间
        "end_date": "2012-06-23",//项目结束时间
        "default_target": "http://www.admaster.com.cn"//项目默认点击目标地址
        "media_num": 8,//项目中媒体数目
        "placement_num": 258,//项目中广告位数目
        "target_audience":{//目标受众人群
            "age": "19-25",//目标受众人群年龄范围
            "sex": "male"//目标受众人群性别
        },
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
    }
	]