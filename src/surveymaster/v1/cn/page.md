---
weight: 3
layout: default
category: surveymaster
title: 页相关
language: cn
---

* TOC
{:toc}

## 1. 创建页

    POST /surveys/:survey_id/pages

**响应**

    Status: 201 Created
    Location: http://api.surveymaster.com.cn/surveys/123/pages

{:.prettyprint}
    {
      "id" : 1,
      "url" : 'http://api.surveymaster.com.cn/surveys/pages/1',
      "survey_id" : 112,    /* 问卷ID */
      "order_num" : 1,   /* 显示顺序 */
      "is_deleted" : "no"
    }


## 2. 获取指定页详情

    GET /surveys/pages/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "id" : 1,
        "url" : 'http://api.surveymaster.com.cn/surveys/pages/1',
        "survey_id" : 112,
        "order_num" : 1,   /* 显示顺序 */
        "is_deleted" : "no"
    }


## 3. 修改指定页

    PATCH /surveys/pages/:id

**请求**

{:.prettyprint}
    {
        "order_num" : 1,   /* 显示顺序 */
        "is_deleted" : "no"
    }


**响应**

    Status: 204 No Content
