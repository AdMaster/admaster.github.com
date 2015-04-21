---
weight: 2
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 广告主
version: v2
---

# 广告主

* TOC
{:toc}

## 获取广告主列表

    GET http://lib.admasterapi.com/api_v1/advertisers


**响应**

{:.prettyprint}
    [
    {
        id: 10032,
        name_cn: "伊利",
    }
    ]


## 获取指定广告主信息

    GET http://lib.admasterapi.com/api_v1/advertisers/:id

**响应**

{:.prettyprint}
    {
        id: 10032,
        name_cn: "伊利",
    }


