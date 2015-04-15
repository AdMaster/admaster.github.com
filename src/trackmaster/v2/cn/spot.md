---
weight: 8
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 点位
version: v2
---

# 点位

* TOC
{:toc}

## 获取指定项目下的点位

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:id/spots

**响应**

{:.prettyprint}
    [{
    "id": 999,
    "campaignId": 999, // 关联项目id
    "placementId": 999, // 关联广告位id
    "creativeId": 999, // 关联创意id
    "date": "2014-05-10", // 对应的日期
    "num": 888, // 购买的单位量
    "creatorId": 999, // 创建者id
    "createdAt": "2012-01-10T02:30:59Z",
    "updatedAt": "2012-01-10T02:30:59Z"
    }]

## 给某个项目添加排期

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/spots

**请求**

{:.prettyprint}
    {
        campaignId: 50000,//必填，项目 ID
        date: "2014-07-22T00:00:00.000Z",//必填，排期日期
        placementId: 1,//必填，广告位 ID
        creativeId: 8,//必填，创意 ID
        num: 30//必填，购买量，必须为大于 0 的整数
    }

**响应**

{:.prettyprint}
    {
        id: 14,
        campaignId: 50000,
        date: "2014-07-22T00:00:00.000Z",
        placementId: 1,
        creativeId: 8,
        num: 30,
        creatorId: 1,
        createdAt: "2014-07-16T03:34:33.000Z",
        updatedAt: "2014-07-23T06:50:43.000Z"
    }

## 修改指定点位

    PATCH http://m.trackmaster.com.cn/api_v2/spots/:id

注意：online_date必须在项目起止时间范围内，修改点位信息时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。

**请求**

{:.prettyprint}
    {
    "campaignId": 999, // 关联项目id
    "placementId": 999, // 关联广告位id
    "creativeId": 999, // 关联创意id
    "date": "2014-05-10", // 对应的日期
    "num": 888, // 购买的单位量
    }

**响应**

{:.prettyprint}
    {
        id: 14,
        campaignId: 50000,
        date: "2014-07-22T00:00:00.000Z",
        placementId: 1,
        creativeId: 8,
        num: 30,
        creatorId: 1,
        createdAt: "2014-07-16T03:34:33.000Z",
        updatedAt: "2014-07-23T06:50:43.000Z"
    }

## 获取某个排期

    GET http://m.trackmaster.com.cn/api_v2/spots/:id

**响应**

{:.prettyprint}
    {
        id: 14,
        campaignId: 50000,
        date: "2014-07-22T00:00:00.000Z",
        placementId: 1,
        creativeId: 8,
        num: 30,
        creatorId: 1,
        createdAt: "2014-07-16T03:34:33.000Z",
        updatedAt: "2014-07-23T06:50:43.000Z"
    }
    
## 删除某个排期

    DELETE http://m.trackmaster.com.cn/api_v2/spots/:id

**响应**

    Status: 204 OK 