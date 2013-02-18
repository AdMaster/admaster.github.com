---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 品牌
---

# 品牌 #

* TOC
{:toc}


## 获取指定网络下指定广告主下的所有品牌

    GET /networks/:network_id/advertisers/:advertiser_id/brands

**参数**

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

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

    GET /networks/advertisers/brands/:id

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
        "url": "http://{{site.track_api_host}}/networks/advertisers/brands/30",
        "created_at": "2012-09-06T20:39:23Z"//品牌创建时间
    }


## 添加指定品牌到指定网络广告主下

    POST /networks/:network_id/advertisers/:advertiser_id/brands

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


## 修改指定的网络广告主下品牌名称

    PATCH /networks/advertisers/brands/:id

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


## 删除指定的网络广告主下品牌

    DELETE /networks/advertisers/brands/:id

当品牌下有关联项目时，不能删除。

**响应**

{:.prettyprint}
    Status: 204 No Content 
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
