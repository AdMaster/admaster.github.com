---
weight: 10
layout: default
category: surveymaster
title: 用户相关
language: cn
version: v1
---

* TOC
{:toc}

## 1. 获取所有用户列表
    GET /admin/users

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `expires_at` - 到期时间

`direction`
: _可选_ **String** - 排序方式

  * `asc`  - 升序
  * `desc` - 降序 (_默认_)

`keyword`
: _可选_ **String** - 排序方式

  * `username`  - 根据用户名查找
  * `email`     - 根据email查找

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "created_at": "2014-01-10T16:01:17+08:00",
            "email": "example@admaster.com.cn",
            "expires_at": "2014-01-14T11:08:17+08:00",
            "ip": "127.0.0.1",
            "is_admin": true,
            "login_at": "2014-01-14T10:38:50+08:00",
            "username": "example",
            "uuid": "feed0f10-9113-0130-17c7-00188b440125",
            "id": "52cfa8cde092372bf6000001"
        }
    ]


## 2. 获取当前登录用户信息
    GET /user

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "created_at": "2014-01-10T16:01:17+08:00",
        "email": "example@admaster.com.cn",
        "expires_at": "2014-01-14T11:08:17+08:00",
        "ip": "127.0.0.1",
        "is_admin": true,
        "login_at": "2014-01-14T10:38:50+08:00",
        "username": "example",
        "uuid": "feed0f10-9113-0130-17c7-00188b440125",
        "id": "52cfa8cde092372bf6000001"
    }


## 3. 获取指定用户信息
    GET /admin/users/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "created_at": "2014-01-10T16:01:17+08:00",
        "email": "example@admaster.com.cn",
        "expires_at": "2014-01-14T11:08:17+08:00",
        "ip": "127.0.0.1",
        "is_admin": true,
        "login_at": "2014-01-14T10:38:50+08:00",
        "username": "example",
        "uuid": "feed0f10-9113-0130-17c7-00188b440125",
        "id": "52cfa8cde092372bf6000001"
    }


## 4. 添加用户
    POST /admin/users

**请求**

{:.prettyprint}
    {
        "email": "example@admaster.com.cn",
        "username": "example",
        "uuid": "feed0f10-9113-0130-17c7-00188b440125",
        "access_token": "4ca8cc1d9d6b6328401a4737904a8e367ecefad3"
    }

**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "created_at": "2014-01-10T16:01:17+08:00",
        "email": "example@admaster.com.cn",
        "expires_at": "2014-01-14T11:08:17+08:00",
        "ip": "127.0.0.1",
        "is_admin": true,
        "login_at": "2014-01-14T10:38:50+08:00",
        "username": "example",
        "uuid": "feed0f10-9113-0130-17c7-00188b440125",
        "id": "52cfa8cde092372bf6000001"
    }


## 5. 修改指定的用户信息
    PATCH /admin/users/:id

**请求**

{:.prettyprint}
    {
        "email": "example@admaster.com.cn",
        "username": "example"
    }


**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "created_at": "2014-01-10T16:01:17+08:00",
        "email": "example@admaster.com.cn",
        "expires_at": "2014-01-14T11:08:17+08:00",
        "ip": "127.0.0.1",
        "is_admin": true,
        "login_at": "2014-01-14T10:38:50+08:00",
        "username": "example",
        "uuid": "feed0f10-9113-0130-17c7-00188b440125",
        "id": "52cfa8cde092372bf6000001"
    }


## 5. 修改当前登录用户信息
  PATCH /users

**请求**

{:.prettyprint}
    {
        "email": "example@admaster.com.cn",
        "username": "example"
    }


**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "created_at": "2014-01-10T16:01:17+08:00",
        "email": "example@admaster.com.cn",
        "expires_at": "2014-01-14T11:08:17+08:00",
        "ip": "127.0.0.1",
        "is_admin": true,
        "login_at": "2014-01-14T10:38:50+08:00",
        "username": "example",
        "uuid": "feed0f10-9113-0130-17c7-00188b440125",
        "id": "52cfa8cde092372bf6000001"
    }


## 6. 删除指定的用户
    DELETE /admin/users/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
