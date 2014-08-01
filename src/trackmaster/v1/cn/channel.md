---
weight: 8
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 频道
version: v1
---

# 频道

* TOC
{:toc}


## 获取指定媒体频道列表

    GET /medias/:media_id/channels

**参数**

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/channels?page=2>; rel="next",
          <http://{{site.track_api_host}}/channels?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       {
            //频道ID，全局唯一
            "id": 1025,
            //频道名称
            "name": "体育新闻",
        }

## 获取指定频道详细信息

    GET /medias/channels/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //频道ID，全局唯一
        "id": 1025,
        //频道名称
        "name": "体育新闻",
    }



