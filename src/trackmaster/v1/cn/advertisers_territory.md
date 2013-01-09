---
weight: 13
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 地域
---

# 地域 #

* TOC
{:toc}


## 获取指定 ID 的地域信息

    GET /geos/:id

**参数**   
 
`language=en`    
: _可选_  - 地域名称为英文

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


{:.prettyprint}
     [
            {
            "id":1
            "name":中国
            }
        ]

