---
weight: 10
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 点位
---

# 点位

* TOC
{:toc}

## 获取指定项目下指定时间段内的点位

    GET /advertisers/:advertiser_id/campaigns/placements/:placement_id/spots

**参数**

`start_date`
: _必选_ **date** - 开始日期 格式为: yyyy-mm-dd 例如: 2012-04-12

`end_date`
: _必选_ **date** - 结束日期 格式为: yyyy-mm-dd 例如: 2012-04-30

`page`
: _可选_ **integer** - 显示页码

`per_page`
: _可选_ **integer** - 分页数量，默认每页30条

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        /*广告位 ID*/
        "placement_id": 200019261,
        /*排期日期*/
        "online_date": "2012-04-13",
        //创意ID
        "creative_id": 200019827,
        //购买量
        "units": 23,
      }
    ]


