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

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/:placement_id/spots?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/:placement_id/spots?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [{
        id: 14,
        campaignId: 50000,
        date: "2014-07-22T00:00:00.000Z",
        placementId: 1,
        creativeId: 8,
        num: 30,
        creatorId: 1,
        createdAt: "2014-07-16T03:34:33.000Z",
        updatedAt: "2014-07-23T06:50:43.000Z"
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
        num: 30,
        creatorId: 1,
    }

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/:placement_id/spots?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/:placement_id/spots?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

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

`units`
: _必选_ **float** - 购买量，不上线可以设置为 0，支持小数录入

`creative_id`
: _可选_ **integer** - 创意 ID

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
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

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
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

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999    