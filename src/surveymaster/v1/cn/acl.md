---
weight: 11
layout: default
category: surveymaster
title: 权限相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定问卷的权限列表
	GET /surveys/:survey_id/acls

**响应**

    Status: 200 OK

{:.prettyprint}
    [
	    {
		    "acl_id" : 1,
    	    "user_id" : 1,
		    "permisson" : 2,
	    }
    ]


## 2. 获取指定用户的权限列表
	GET /users/:user_id/acls

**响应**

    Status: 200 OK

{:.prettyprint}
    [
	    {
		    "acl_id" : 1,
		    "survey_id" : 1,
		    "permisson" : 2,
	    }
    ]


## 3. 给指定问卷添加用户权限
	POST /surveys/:survey_id/acls

**请求**

{:.prettyprint}
	{
		"user_id" : 1,
		"permisson" : 2,
	}


**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
	    "acl_id" : 1,/* id(自增) */
    }

## 4. 修改指定的权限
	PATCH /surveys/acls/:id

**请求**

{:.prettyprint}
    {
	    "acl_id" : 1,
	    "permission" : 1,
    }


**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 5. 删除指定的权限
	DELETE /surveys/acls/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
