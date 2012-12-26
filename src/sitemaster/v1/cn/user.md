---
weight: 5
layout: default
category: sitemaster
language: cn
title: 站点
---

# 站点

* TOC
{:toc}

## 获取当前用户信息

    GET /user

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: xxx
        email: "email@admaster.com.cn"
        username: "your name"
        uuid: "xxxxxxxxxxxxxxxxxxxxx"
    }
