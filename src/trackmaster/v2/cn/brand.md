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

    GET http://m.trackmaster.com.cn/api_v2/networks/:networkId/brands

**参数**

`advertiserId`
: _可选_ 广告主 ID

以 GET 方式传递广告主 ID，传递此参数后只返回该广告主下的品牌。


**响应**

{:.prettyprint}
    [{
        "id": 999, // 资源id
        "name":品牌 // 品牌名称
        "networkId": 999, //关联网络ID
        "advertiserId": 999, //关联广告主ID
        "isDelete": yes或者no, //是否被删除,
    }]


## 获取指定 ID 品牌详细信息

    GET http://m.trackmaster.com.cn/api_v2/brands/:id

**响应**

{:.prettyprint}
    {
        "id": 999, // 资源id
        "name":品牌 // 品牌名称
        "networkId": 999, //关联网络ID
        "advertiserId": 999, //关联广告主ID
        "isDelete": yes或者no //是否被删除,
    }

## 添加指定品牌到指定网络广告主下

    POST http://m.trackmaster.com.cn/api_v2/networks/:networkId/brands

**请求**

    {
        "name": "巧乐兹" //必填，品牌名称
        "advertiserId": 999, //必填，关联广告主ID
    }

**响应**

{:.prettyprint}
    {
        "name":品牌 // 品牌名称
        "networkId": 999, //关联网络ID
        "advertiserId": 999, //关联广告主ID
        "creatorId": 999, //创建者id
        "isDelete": yes或者no, //是否被删除,
    }


## 修改指定品牌

    PATCH http://m.trackmaster.com.cn/api_v2/brands/:id
    
注意：修改品牌时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。    

**请求**

{:.prettyprint}
    {
        "name":品牌 // 品牌名称
        "advertiserId": 999, //关联广告主ID
    }

`name`
: _必选_ **string** - 品牌名称


**响应**

{:.prettyprint}
    {
        "id": 999, // 资源id
        "name":品牌 // 品牌名称
        "networkId": 999, //关联网络ID
        "advertiserId": 999, //关联广告主ID
        "isDelete": yes或者no, //是否被删除,
    }


## 删除指定品牌

    DELETE http://m.trackmaster.com.cn/api_v2/brands/:id

当品牌下有关联项目时，不能删除。

**响应**

{:.prettyprint}
    Status: 204 OK

