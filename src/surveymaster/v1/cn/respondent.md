---
weight: 5
layout: default
category: surveymaster
title: 答题人相关
language: cn
version: v1
---

* TOC
{:toc}

## 1. 获取答题人列表
    GET /respondents

**响应**

    Status: 200

{:.prettyprint}
    [
        {
            "admckid": "1401151956201886732",
            "r_key": "cookie",
            "r_value": "1401151956201886732",
            "id": "52d8d670e092370259000009"
        }
    ]


## 2. 获取指定的答题人信息
    GET /respondents/:id

**响应**

    Status: 200

{:.prettyprint}
    {
        "admckid": "1401151956201886732",
        "r_key": "cookie",
        "r_value": "1401151956201886732",
        "id": "52d8d670e092370259000009"
    }

## 3. 修改指定的答题人信息
    PATCH /respondents/:id

**请求**

{:.prettyprint}
    {
        "admckid" : '1290',
    }


**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "admckid": "1401151956201886732",
        "r_key": "cookie",
        "r_value": "1401151956201886732",
        "id": "52d8d670e092370259000009"
    }

## 4. 删除指定的答题人
    DELETE /respondents/:id

**响应**

    Status: 204
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
