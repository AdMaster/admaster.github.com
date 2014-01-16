---
weight: 3
layout: default
category: surveymaster
title: 页相关
language: cn
---

* TOC
{:toc}

## 1. 获取页列表

    GET /surveys/:survey_id/pages

{:.prettyprint}
    [
        {
            "description": "",
            "number": 1,
            "survey_id": "52d4b062e092371da5000001",
            "title": "",
            "id": "52d4b066e092371da5000003"
        }
    ]

## 2. 获取指定页前面的所有页列表

    GET /surveys/:survey_id/pages/:page_id/higher_siblings

{:.prettyprint}
    [
        {
            "description": "",
            "number": 1,
            "survey_id": "52d4b062e092371da5000001",
            "title": "",
            "id": "52d4b066e092371da5000003"
        }
    ]

## 3. 获取指定页后面的所有页列表

    GET /surveys/:survey_id/pages/:page_id/lower_siblings

{:.prettyprint}
    [
        {
            "description": "",
            "number": 1,
            "survey_id": "52d4b062e092371da5000001",
            "title": "",
            "id": "52d4b066e092371da5000003"
        }
    ]

## 4. 获取指定页详情

    GET /surveys/:survey_id/pages/:id

{:.prettyprint}
    {
        "description": "",
        "number": 1,
        "survey_id": "52d4b062e092371da5000001",
        "title": "",
        "id": "52d4b066e092371da5000003"
    }


## 5. 创建页

    POST /surveys/:survey_id/pages

**请求**

{:.prettyprint}
    {
        "description": "xxx",
        "title": "xxx"
    }

**响应**

    Status: 201

{:.prettyprint}
    {
        "description": "",
        "number": 1,
        "survey_id": "52d4b062e092371da5000001",
        "title": "",
        "id": "52d4b066e092371da5000003"
    }


## 6. 修改指定页

    PATCH /surveys/:survey_id/pages/:id

**请求**

{:.prettyprint}
    {
        "description": "xxx",
        "title": "xxx"
    }

**响应**

    Status: 201

{:.prettyprint}
    {
        "description": "",
        "number": 1,
        "survey_id": "52d4b062e092371da5000001",
        "title": "",
        "id": "52d4b066e092371da5000003"
    }

## 7. 删除指定页

    DELETE /surveys/:survey_id/pages/:id

**响应**

    Status: 204

## 8. 移动指定页

    PATCH /surveys/:survey_id/pages/:page_id/move

**请求**

{:.prettyprint}
    {
        "position": "up/down/top/bottom/above/below",
        "other_id": "52d4b066e092371da5000003"
    }

**响应**

    Status: 201

{:.prettyprint}
    {
        "description": "",
        "number": 1,
        "survey_id": "52d4b062e092371da5000001",
        "title": "",
        "id": "52d4b066e092371da5000003"
    }

## 9. 在指定页进行分页

    PATCH /surveys/:survey_id/pages/:page_id/split

**请求**

{:.prettyprint}
    {
        "separate_id": "52d4b075e092371da5000004" // 需要分页的question_id
    }

**响应**

    Status: 201

{:.prettyprint}
    {
        "description": "",
        "number": 1,
        "survey_id": "52d4b062e092371da5000001",
        "title": "",
        "id": "52d4b066e092371da5000003"
    }
