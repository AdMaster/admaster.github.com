---
weight: 1
layout: default
category: trackmaster
subcategory: agency
language: cn
version: v2
title: 代码
---

# 代码

* TOC
{:toc}

## 获取指定项目的监测代码

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:id/codes

**参数**

* placementId：选填，广告位 id，指定该参数后只返回该广告位下的监测代码
* placementIds：选填，广告位 id　列表，指定该参数后只返回这些广告位下的监测代码，多个 id 之间用 `,` 分割
* mediaId：选填，媒体 id，指定该参数后只返回该媒体下的监测代码
* mediaIds：选填，媒体 id，指定该参数后只返回这些媒体下的监测代码，多个 id 之间用 `,` 分割

**响应**

{:.prettyprint}
    [
        {
            placementId: 500001,//广告位 id
            creativeId: 0,//创意 id
            mediaId: 1238,//媒体 id
            view: "http://vfs.admaster.com.cn/i/a50014,b500054,c1238,i0,m202,zzoocdni,h", // 曝光代码
            click: "http://c.admaster.com.cn/c/a50014,b500054,c1238,i0,m101,zzoocdni,h" // 点击代码
        },
        {
            placementId: 500001,
            creativeId: 0,
            mediaId: 1238,
            view: "http://vfs.admaster.com.cn/i/a50014,b500055,c1238,i0,m202,zzoocdni,h",
            click: "http://c.admaster.com.cn/c/a50014,b500055,c1238,i0,m101,zzoocdni,h"
        }
    ]

