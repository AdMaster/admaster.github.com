---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 媒体
version: v2
---

# 媒体

* TOC
{:toc}

## 获取系统媒体库列表

    GET http://lib.admasterapi.com/api_v1/medias


**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [{
        id: 440,
        name_cn: "腾讯网",
        name_en: "",
        status: "normal",
        fullName_cn: "",
        fullName_en: "",
        category: "domain",
        type: "mixed",
        logo: "http://qq.com/favicon.ico",
        domain: "qq.com",
        parentId: 0,
        tag: "时事政治"
    }]
    


## 获取指定系统媒体详细信息

    GET http://lib.admasterapi.com/api_v1/medias/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: 440,
        name_cn: "腾讯网",
        name_en: "",
        status: "normal",
        fullName_cn: "",
        fullName_en: "",
        category: "domain",
        type: "mixed",
        logo: "http://qq.com/favicon.ico",
        domain: "qq.com",
        parentId: 0,
        tag: "时事政治"
    }