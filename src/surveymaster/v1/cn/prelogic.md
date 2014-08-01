---
weight: 7
layout: default
category: surveymaster
title: 前置逻辑相关
language: cn
version: v1
---

* TOC
{:toc}

## 1. 获取指定页的前置逻辑列表
    GET /surveys/:survey_id/pages/:page_id/prelogics

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "conditions": [
                {
                    "question_id": "52d7a76fe092377673000024",
                    "range": [
                        "2"
                    ],
                    "type": "any"
                }
            ],
            "order_num": 0,
            "page_id": "52d7a76fe092377673000028",
            "question_id": null,
            "id": "52d8c841e09237421c000005"
        }
    ]

## 2. 获取指定页的前置逻辑
    GET /surveys/:survey_id/pages/:page_id/prelogics/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "2"
                ],
                "type": "any"
            }
        ],
        "order_num": 0,
        "page_id": "52d7a76fe092377673000028",
        "question_id": null,
        "id": "52d8c841e09237421c000005"
    }

## 3. 添加指定页的前置逻辑
    POST /surveys/:survey_id/pages/:page_id/prelogics

**请求**

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "2"
                ],
                "type": "any"
            }
        ],
        "order_num": 0
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d8c841e09237421c000005",
        /* 前置逻辑详情 */
    }

## 4. 修改指定页的前置逻辑
    PATCH /surveys/:survey_id/pages/:page_id/prelogics/:id

**请求**

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "2"
                ],
                "type": "any"
            }
        ],
        "order_num": 0
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d8c841e09237421c000005",
        /* 前置逻辑详情 */
    }

## 5. 删除指定页的前置逻辑
    DELETE /surveys/:survey_id/pages/:page_id/prelogics/:id

**响应**

    Status: 204
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 6. 获取指定问题的前置逻辑列表
    GET /surveys/:survey_id/questions/:question_id/prelogics

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "conditions": [
                {
                    "question_id": "52d7a76fe092377673000024",
                    "range": [
                        "2"
                    ],
                    "type": "any"
                }
            ],
            "order_num": 0,
            "question_id": "52d7a76fe092377673000028",
            "page_id": null,
            "id": "52d8c841e09237421c000005"
        }
    ]

## 7. 获取指定问题的前置逻辑
    GET /surveys/:survey_id/questions/:question_id/prelogics/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "2"
                ],
                "type": "any"
            }
        ],
        "order_num": 0,
        "question_id": "52d7a76fe092377673000028",
        "page_id": null,
        "id": "52d8c841e09237421c000005"
    }

## 8. 添加指定问题的前置逻辑
    POST /surveys/:survey_id/questions/:question_id/prelogics

**请求**

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "2"
                ],
                "type": "any"
            }
        ],
        "order_num": 0
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d8c841e09237421c000005",
        /* 前置逻辑详情 */
    }

## 9. 修改指定问题的前置逻辑
    PATCH /surveys/:survey_id/questions/:question_id/prelogics/:id

**请求**

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "2"
                ],
                "type": "any"
            }
        ],
        "order_num": 0
    }


**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d8c841e09237421c000005",
        /* 前置逻辑详情 */
    }

## 10. 删除指定问题的前置逻辑
    DELETE /surveys/:survey_id/questions/:question_id/prelogics/:id

**响应**

    Status: 204
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
