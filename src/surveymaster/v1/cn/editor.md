---
weight: 11
layout: default
category: surveymaster
title: 权限相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定问卷的编辑列表
    GET /surveys/:survey_id/editors

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "role": "owner",
            "survey_id": "52d7a76fe092377673000021",
            "user_id": "52cfa8cde092372bf6000001",
            "id": "52d7a76f1ab852356722adb6"
        }
    ]


## 2. 给指定问卷添加编辑
    POST /surveys/:survey_id/editors


**请求**

{:.prettyprint}
    {
        "role": "owner",
        "user_id": "52cfa8cde092372bf6000001",
    }


**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "role": "owner",
        "survey_id": "52d7a76fe092377673000021",
        "user_id": "52cfa8cde092372bf6000001",
        "id": "52d7a76f1ab852356722adb6"
    }
