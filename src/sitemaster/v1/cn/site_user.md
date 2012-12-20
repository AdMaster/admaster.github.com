---
weight: 5
layout: default
category: sitemaster
language: cn
title: 站点用户
---

# 站点用户

* TOC
{:toc}

## 获取指定站点下的用户

    GET /sites/:site_id/users

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/xxxx/users?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites/xxxx/users?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          id: 245
          email: "zhaoxiongfei@admaster.com.cn",
          username: "zhaoxiongfei",
          type: "admin",//用户类型 `founder` 创始人 `admin` 管理员 `user` 普通用户
          created_at: "2012-12-12 16:00:08",//添加时间
      }
    ]

## 获取指定用户

    GET /sites/users/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
          id: 245
          email: "zhaoxiongfei@admaster.com.cn",
          username: "zhaoxiongfei",
          type: "admin",//用户类型 `founder` 创始人 `admin` 管理员 `user` 普通用户
          created_at: "2012-12-12 16:00:08",//添加时间
    }

## 修改用户信息

    PATCH /sites/users/:id

**参数**

`type`
: _必选_ **enum** - 用户类型 `admin` `user` 


**请求**

{:.prettyprint}
    {
        "type": "admin", //用户类型
    }

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
          id: 245
          email: "zhaoxiongfei@admaster.com.cn",
          username: "zhaoxiongfei",
          type: "admin",//用户类型 `founder` 创始人 `admin` 管理员 `user` 普通用户
          created_at: "2012-12-12 16:00:08",//添加时间
    }

## 添加站点用户

    POST /sites/:site_id/users

**参数**

`email`
: _必选_ **email** - 用户email地址

`type`
: _必选_ **enum** - 用户类型 `admin` `user` 


**请求**

{:.prettyprint}
    {
        "email": "zhaoxiongfei@admaster.com.cn",//用户email地址
        "type": "admin", //用户类型
    }

**响应**

    Status: 201 Created
    Location: http://{{site.site_api_host}}/site/xxxxx
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
          id: 245
          email: "zhaoxiongfei@admaster.com.cn",
          username: "zhaoxiongfei",
          type: "admin",//用户类型 `founder` 创始人 `admin` 管理员 `user` 普通用户
          created_at: "2012-12-12 16:00:08",//添加时间
    }

## 删除用户

    DELETE /sites/users/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 字段说明

返回值字段         | 字段类型 | 字段说明
id               | integer | 用户 ID
email            | email   | 用户email地址
username         | string  | 用户名
type             | enum    | 用户类型 `founder` `admin` `user`
created_at       | date    | 创建时间
