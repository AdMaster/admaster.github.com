---
weight: 4
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 品牌
version: v1
---

# 品牌 #

* TOC
{:toc}

##获取指定广告主下的品牌列表

    GET /advertisers/:advertiser_id/brands

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


{:.prettyprint}
    [
      {
        "id": 30,//网络品牌 ID
        "name": "巧乐兹",//品牌名称
        "created_at": "2012-09-06T20:39:23Z"//品牌创建时间
      }
    ]



##获取广告主下指定 ID 品牌详细信息
    
    GET /advertisers/:advertiser_id/brands/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 30,//网络品牌 ID
        "network_id": 11,//工作网络 ID
        "advertiser_id": 10231,//广告主 ID
        "name": "巧乐兹",//品牌名称
        "created_at": "2012-09-06T20:39:23Z"//品牌创建时间
    }