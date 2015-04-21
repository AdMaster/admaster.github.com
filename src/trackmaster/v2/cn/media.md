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

{:.prettyprint}
    [{
        id: 440,
        name_cn: "腾讯网",
        status: "normal",
        domain: "qq.com"
    }]
    


## 获取指定系统媒体详细信息

    GET http://lib.admasterapi.com/api_v1/medias/:id

**响应**

{:.prettyprint}
    {
        id: 440,
        name_cn: "腾讯网",
        status: "normal",
        domain: "qq.com"
    }