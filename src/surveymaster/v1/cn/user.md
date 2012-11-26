---
weight: 10
layout: default
category: surveymaster
title: 用户相关
language: cn
---

* TOC
{:toc}

## 1. 获取所有用户列表
	GET /users

**响应**

    Status: 200 OK

{:.prettyprint}
    [
	    {
		    "user_id" : 1,
		    "url" : 'http://api.surveymaster.com.cn/users/1',
		    "username" : 'example',
		    "email" : 'example@admaster.com.cn',
		    "uuid" : "a7f8d684-e4ff-11e1-af03-00188b440125",
		    "expires_at" : 1353919645,
		    "created_at" : 1353317459,
	    }
    ]


## 2. 获取当前登录用户信息
	GET /user

**响应**

    Status: 200 OK

{:.prettyprint}
	{
		"user_id" : 1,
		"username" : 'example',
		"email" : 'example@admaster.com.cn',
		"uuid" : "a7f8d684-e4ff-11e1-af03-00188b440125",
		"expires_at" : 1353919645,
		"created_at" : 1353317459,
	}

## 3. 获取指定用户信息
	GET /users/:id

**响应**

    Status: 200 OK

{:.prettyprint}
	{
		"user_id" : 1,
		"url" : 'http://api.surveymaster.com.cn/users/1',
		"username" : 'example',
		"email" : 'example@admaster.com.cn',
		"uuid" : "a7f8d684-e4ff-11e1-af03-00188b440125",
		"expires_at" : 1353919645,
		"created_at" : 1353317459,
	}



## 4. 添加用户
	POST /users

**请求**

{:.prettyprint}
	{
		"username" : 'example',
		"email" : 'example@admaster.com.cn',
		"uuid" : "a7f8d684-e4ff-11e1-af03-00188b440125",
    	"access_token" : "4ca8cc1d9d6b6328401a4737904a8e367ecefad3"
	}

**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
	    "user_id" : 1,/* 用户id(自增) */
    }

## 5. 修改指定的用户
	PATCH /users/:id

**请求**

{:.prettyprint}
	{
		"username" : 'example',
		"email" : 'example@admaster.com.cn',
	}


**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 6. 删除指定的用户
	DELETE /users/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
