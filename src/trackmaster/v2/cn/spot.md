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

    GET /campaigns/:id/spots

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

    POST /campaigns/:campaignId/spots

**请求**

{:.prettyprint}
    {
        campaignId: 50000,
        date: "2014-07-22T00:00:00.000Z",
        placementId: 1,
        creativeId: 8,
        num: 30
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

    PUT /spots/:id

注意：online_date必须在项目起止时间范围内

**请求**

{:.prettyprint}
    {
    "id": 999,
    "campaignId": 999, // 关联项目id
    "placementId": 999, // 关联广告位id
    "creativeId": 999, // 关联创意id
    "date": "2014-05-10", // 对应的日期
    "num": 888, // 购买的单位量
    "creatorId": 999, // 创建者id
    "createdAt": "2012-01-10T02:30:59Z",
    "updatedAt": "2012-01-10T02:30:59Z"
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

    GET /spots/:id

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

    DELETE /spots/:id

**响应**

    Status: 200 OK 