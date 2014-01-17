---
weight: 8
layout: default
category: surveymaster
title: 后置逻辑相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定页的后置逻辑列表
    GET /surveys/:survey_id/pages/:page_id/postlogics

**响应**

    Status: 200 OK

{:.prettyprint}
    [ // 每一个数组元素就是一条逻辑，按先后顺序依次检查组内各逻辑，一旦存在符合条件的逻辑，检查即终止
        {
            "conditions": [
                {
                    "question_id": "52d7a76fe092377673000024",
                    "range": [
                        "0",
                        "2"
                    ],
                    "type": "any"
                }
            ],
            "goto": "52d7a76fe092377673000028",
            "is_filter": false,
            "order_num": 0,
            "page_id": "52d7a76fe092377673000023",
            "id": "52d8c222e09237421c000001"
        }
    ]


## 2. 获取指定的后置逻辑（页逻辑）
    GET /surveys/:survey_id/pages/:page_id/postlogics/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "conditions": [
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "0",
                    "2"
                ],
                "type": "any"
            }
        ],
        "goto": "52d7a76fe092377673000028",
        "is_filter": false,
        "order_num": 0,
        "page_id": "52d7a76fe092377673000023",
        "id": "52d8c222e09237421c000001"
    }


## 3. 添加后置逻辑
    POST /surveys/:survey_id/pages/:page_id/postlogics

**请求**

{:.prettyprint}
    {
        "conditions": [ // 每一个数组元素就是一个条件，组内各条件都是 AND 的关系
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "0",
                    "2"
                ],
                "type": "all/any/none/include/exclude/number/date"
                // all: 全部选中range范围内的选项, any: range范围内的选项任意选中一个, none: all取反
                // include: 包含range范围内的任何一个选项 exclude: 不包含range范围内的任何一个选项
                // number/date: 在range范围内
            }
        ],
        "goto": "52d7a76fe092377673000028",
        "is_filter": false, // 是否为过滤器的条件
        "order_num": 0,
        "page_id": "52d7a76fe092377673000023",
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d8c222e09237421c000001",
        // 后置逻辑详情
    }


## 4. 修改指定的后置逻辑
    PATCH /surveys/:survey_id/pages/:page_id/postlogics/:id

**请求**

{:.prettyprint}
    {
        "conditions": [ // 每一个数组元素就是一个条件，组内各条件都是 AND 的关系
            {
                "question_id": "52d7a76fe092377673000024",
                "range": [
                    "0",
                    "2"
                ],
                "type": "all/any/none/include/exclude/number/date"
                // all: 全部选中range范围内的选项, any: range范围内的选项任意选中一个, none: all取反
                // include: 包含range范围内的任何一个选项 exclude: 不包含range范围内的任何一个选项
                // number/date: 在range范围内
            }
        ],
        "goto": "52d7a76fe092377673000028",
        "is_filter": false, // 是否为过滤器的条件
        "order_num": 0,
        "page_id": "52d7a76fe092377673000023",
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d8c222e09237421c000001",
        // 后置逻辑详情
    }


## 5. 删除指定的后置逻辑
    DELETE /surveys/:survey_id/pages/:page_id/postlogics/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
