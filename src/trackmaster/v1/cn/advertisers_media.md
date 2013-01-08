---
weight: 4
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 媒体
---

# 媒体

* TOC
{:toc}

##获取广告主下的媒体列表

    GET /advertisers/:advertiser_id/medias

**响应**

    status: 200 ok

{:.prettyprint}
    [

        {
            id: 53,//系统媒体 ID
            name: "test media name",//系统媒体名称
            logo: "0"
            domain: "example.com"
            tag: "test tag"
            created_at: "2012-12-10T04:03:54Z"
        }
    ]

##获取广告主下媒体详情

    GET /advertisers/:advertiser_id/medias/:media_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 400,//系统媒体 ID
        "url": "http://{{site.track_api_host}}/medias/400",
        "name": "新浪",//系统媒体名称
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
    }


