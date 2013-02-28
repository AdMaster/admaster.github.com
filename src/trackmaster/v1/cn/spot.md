---
weight: 10
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 点位
---

# 点位

* TOC
{:toc}

## 获取指定广告位下指定时间段内的点位

    GET /networks/advertisers/campaigns/placements/:placement_id/spots

**参数**

`start_date`
: _必选_ **date** - 开始日期 格式为: YYYY-MM-DD 例如: 2012-04-12

`end_date`
: _必选_ **date** - 结束日期 格式为: YYYY-MM-DD 例如: 2012-04-30

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/:placement_id/spots?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/:placement_id/spots?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //广告位 ID
        "placement_id": 200019261,
        //排期日期
        "online_date": "2012-04-13",
        //创意ID
        "creative_id": 200019827,
        //购买量
        "units": 23,
      }
    ]

## 修改指定点位

    PUT /networks/advertisers/campaigns/placements/:placement_id/spots/:online_date

**请求**

`units`
: _必选_ **integer** - 购买量，不上线可以设置为 0

`creative_id`
: _可选_ **integer** - 创意 ID

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 批量修改广告位下的点位

    POST /networks/advertisers/campaigns/placements/:placement_id/spots

**请求**

`online_date`
: _必选_ **date** - 需求修改点位的排期日期，格式为: YYYY-MM-DD 例如: 2012-04-12

`units`
: _必选_ **integer** - 购买量，不上线可以设置为 0

`creative_id`
: _可选_ **integer** - 创意 ID


**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [{
        //需求修改点位的排期日期
        "online_date": 2013-01-01,
        //购买量
        "units": 1,
        //创意 ID
        "creative_id": 200019827,
      },
     {...},
     ...
     {...}]
