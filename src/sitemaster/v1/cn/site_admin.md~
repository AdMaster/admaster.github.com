---
weight: 5
layout: default
category: sitemaster_hide
language: cn
title: 站点
---

# 站点

* TOC
{:toc}

## 获取有权操作的站点列表

    GET /sites

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          id: "xxxxx", //站点id
          url: "http://{{site.site_api_host}}/sites/xxxxx",//站点接口地址
          name: "测试站点名称", //测试站点名称
          homePage: "http://www.test.com/",//站点首页地址
          founder: "wangwei@admaster.com.cn",//站点创始人
          created_at: "2012-08-08 10:54:21"//站点添加时间
      }
    ]


## 获取指定站点信息

    GET /sites/:id

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/xxxxx/analytics>; rel="analytics"
          <http://{{site.site_api_host}}/sites/xxxxx/users>; rel="users"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: "xxxxx", //站点id
        url: "http://{{site.site_api_host}}/sites/xxxxx",//站点接口地址
        name: "测试站点名称", //测试站点名称
        homePage: "http://www.test.com/",//站点首页地址
        founder: "wangwei@admaster.com.cn",//站点创始人
        created_at: "2012-08-08 10:54:21"//站点添加时间
    }


## 添加站点

    POST /sites

**参数**

`name`
: _必选_ **string** - 站点名称，长度范围 3 - 100 个字符

`homePage`
: _必选_ **string** - 首页地址


**请求**

{:.prettyprint}
    {
        "name": "这是一个测试项目",//项目名称
        "homePage": "http://www.test.com/", //站点首页地址
    }

**响应**

    Status: 201 Created
    Location: http://{{site.site_api_host}}/site/xxxxx
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: "xxxxx", //站点id
        url: "http://{{site.site_api_host}}/sites/xxxxx",//站点接口地址
        name: "测试站点名称", //测试站点名称
        homePage: "http://www.test.com/",//站点首页地址
        founder: "wangwei@admaster.com.cn",//站点创始人
        created_at: "2012-08-08 10:54:21"//站点添加时间
    }

**字段说明**

参见页面底部说明

## 修改指定站点属性

    PATCH /sites/:id

**参数**

`name`
: _可选_ **string** - 站点名称，长度范围 3 - 100 个字符

`homePage`
: _可选_ **string** - 站点首页地址

`founder`
: _可选_ **email** - 创始人email，只有系统管理人员或者创始人可以修改此信息


**请求**

{:.prettyprint}
    {
        name: "测试站点名称", //测试站点名称
        homePage: "http://www.test.com/",//站点首页地址
        founder: "wangwei@admaster.com.cn",//站点创始人
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 删除站点

    DELETE /sites/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 字段说明

返回值字段         | 字段类型 | 字段说明
id               | integer | 项目 ID
url              | string  | 请求URL
homePage         | string  | 站点首页地址
founder          | string  | 站点创始人
created_at       | date    | 创建时间

