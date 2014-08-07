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

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/advertisers?page=2>; rel="next",
          <http://{{site.track_api_host}}/advertisers?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
    {
        id: 10032,
        name_cn: "伊利",
        name_en: "Yili",
        alias: "伊利",
        fullName_cn: "内蒙古伊利实业集团股份有限公司",
        fullName_en: "",
        dutyNumber: "150117114124263",
        logo: null,
        industryId: 1,
        status: ""
    }
    ]


## 获取指定广告主信息

    GET http://lib.admasterapi.com/api_v1/advertisers/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: 10032,
        name_cn: "伊利",
        name_en: "Yili",
        alias: "伊利",
        fullName_cn: "内蒙古伊利实业集团股份有限公司",
        fullName_en: "",
        dutyNumber: "150117114124263",
        logo: null,
        industryId: 1,
        status: ""
    }


