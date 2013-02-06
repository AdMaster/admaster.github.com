---
weight: 6
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 创意
---

# 创意

* TOC
{:toc}

##获取指定广告主项目下的创意列表

    GET /advertisers/campaigns/:campaign_id/creatives

**响应**

    Status: 200 OK

{:.prettyprint}
    [

      {
        //创意ID，全局唯一
        "id": 1,
        //创意名称
        "name": "创意 A",
        //创意名缩写
        "shortname": "GO",
        //创意描述
        "description": "此创意针对20-30岁人群",
        //创意颜色标识
        "color": "#ff00ff",
        //创意附属文件
        "file": {
            "id": 293,
            "name": "创意.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //创意点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]

##获取指定广告主项目下的创意详情

    GET /advertisers/campaigns/creatives/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //创意ID，全局唯一
        "id": 1,
        //创意名称
        "name": "创意 A",
        //创意名缩写
        "shortname": "GO",
        //创意描述
        "description": "此创意针对20-30岁人群",
        //创意颜色标识
        "color": "#ff00ff",
        //创意附属文件
        "file": {
            "id": 293,
            "name": "创意.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //创意点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
    }
