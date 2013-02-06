---
weight: 5
layout: default
category: surveymaster
title: 答题人相关
language: cn
---

* TOC
{:toc}

## 1. 获取答题人列表
	GET /respondents

**响应**

    Status: 200 OK

{:.prettyprint}
    [
	    {
		    "respondent_id" : 1,
		    "admckid" : '1337002',
		    "cross_uid" : '1290',
	    }
    ]


## 2. 获取指定的答题人信息
	GET /respondents/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
	    "admckid" : '1337002',
	    "cross_uid" : '1290',
    }

## 3. 修改指定的答题人信息
	PATCH /respondents/:id

**请求**

{:.prettyprint}
    {
	    "cross_uid" : '1290',
    }


**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 4. 删除指定的答题人
	DELETE /respondents/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
