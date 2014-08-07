---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 品牌
version: v2
---

# 品牌 #

* TOC
{:toc}


## 获取工作网络下品牌

    GET /networks/:networkId/brands

**参数**

`page`
: _可选_ **advertiserId** - 广告主 ID

以 GET 方式传递广告主 ID


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


## 获取指定 ID 品牌详细信息

    GET /brands/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 999, // 资源id
        "name":品牌 // 品牌名称
        "networkId": 999, //关联网络用户ID
        "advertiserId": 999, //关联广告主ID
        "creatorId": 999, //创建着id
        "isDelete": yes或者no, //是否被删除,
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
    }

## 添加指定品牌到指定网络广告主下

    POST /networks/:networkId/brands

**请求**

    {
        "name": "巧乐兹"
    }

`name`
: _必填_ **string** - 品牌名称

**响应**

    Status: 201 Created 
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 30,//网络品牌 ID
        "network_id": 11,//工作网络 ID
        "advertiser_id": 10231,//广告主 ID
        "name": "巧乐兹",//品牌名称
        "url": "http://{{site.track_api_host}}/networks/advertisers/brands/30",
        "created_at": "2012-09-06T20:39:23Z"//品牌创建时间
    }


## 修改指定品牌

    PATCH /brands/:id

**请求**

{:.prettyprint}
    {
        "name": "巧乐鸡"
    }

`name`
: _必选_ **string** - 品牌名称


**响应**

    Status: 204 No Content 
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 删除指定品牌

    DELETE /brands/:id

当品牌下有关联项目时，不能删除。

**响应**

{:.prettyprint}
    Status: 204 No Content 
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
