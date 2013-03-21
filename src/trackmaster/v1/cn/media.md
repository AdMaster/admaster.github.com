---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 媒体
---

# 媒体

* TOC
{:toc}

## 获取系统媒体库列表

    GET /medias

**参数**

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照媒体 ID 排序
  * `name` - 按照媒体名称排序
  * `create_time` - 按照创建日期排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。


`per_page`
: _可选_ **integer** - 分页数量，默认每页30条

	`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      {
        "id": 400,//系统媒体 ID
        "url": "http://{{site.track_api_host}}/medias/1",
        "name": "新浪",//系统媒体名称
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "status": "enabled"//系统媒体状态
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
      }
    


## 获取指定系统媒体详细信息

    GET /medias/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 400,//系统媒体 ID
        "url": "http://{{site.track_api_host}}/medias/400",
        "name": "新浪",//系统媒体名称
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "status": "enabled"，//系统媒体状态
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
    }


## 获取指定工作网络下媒体库列表

    GET /networks/:network_id/medias

**参数**

`name`
: _可选_ **string** - 网络媒体名称，支持模糊查找


`domain`
: _可选_ **string** - 媒体域名，支持模糊查找。


`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照网络媒体 ID 排序
  * `name` - 按照网络媒体名称排序
  * `status` - 按照状态排序
  * `framework` - 按照框架排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页30条

	`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/1/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/1/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1305,//网络媒体 ID
        "url": "http://{{site.track_api_host}}/networks/1/medias/2",
        "name": "新浪",//网络媒体名称
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"//网络媒体状态
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//系统媒体 ID
        "framework": "no"
      }
    ]


## 获取指定工作网络下指定媒体信息

    GET /networks/:network_id/medias/:media_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1305,//网络媒体 ID
        "url": "http://{{site.track_api_host}}/networks/11/medias/1305",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//系统媒体 ID
        "framework": "no"
    }


## 给指定工作网络添加一个媒体

    POST /networks/:network_id/medias

如果在工作网络中请求添加的系统媒体状态为“disabled”，则无法在网络中添加该媒体。

**请求**

{:.prettyprint}
    {
        'media_id': 8982
    }

`media_id`: _必选_ **integer** - 系统媒体 ID

**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/11/medias/1305
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id":1305,//网络媒体 ID
        "url": "http://{{site.track_api_host}}/networks/11/medias/1305",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//系统媒体 ID
        "framework": "no"
    }


## 获取指定网络媒体 ID 信息

    GET /networks/medias/:network_media_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1305,//网络媒体 ID
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//系统媒体 ID
        "framework": "no"
    }

## 删除指定工作网络下的媒体

    DELETE /networks/medias/:id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/11/medias
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 修改指定工作网络下指定媒体属性

    PATCH /networks/:network_id/medias/:network_media_id

**请求**

{:.prettyprint}
    {
        "name": "新浪财经",
        "framework": "no",
        "status": "enabled"
    }

`name`
: _可选_ **string** - 网络媒体名称

`framework`
: _可选_ **enum** - 是否有框架 `yes`, `no`



**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1305,//网络媒体 ID
        "url": "http://{{site.track_api_host}}/networks/1/medias/1305",
        "name": "新浪财经",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 400//系统媒体 ID
        "framework": "no"
    }


## 获取指定项目下已添加的媒体属性列表

    GET /networks/advertisers/campaigns/:campaign_id/medias/attributes

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      {
        "id": 1314,//网络媒体 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/1314",
        "name": "新浪",//网络媒体名称
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "created_at": "2012-09-06T20:39:23Z",
      }


## 获取指定项目下指定媒体属性

    GET /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id/attributes

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,//网络媒体 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/1314",
        "name": "新浪",//网络媒体名称
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/sina.ico",
        "created_at": "2012-09-06T20:39:23Z",
    }

## 判断指定项目下是否有指定媒体

    GET /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

**响应**

指定媒体在指定项目下

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

指定媒体不在指定项目下

    Status: 404 Not Found
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


##为指定项目添加指定媒体

    PUT /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

如果在项目中添加的网络媒体的状态为“disabled”，则无法在项目中添加该媒体。

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/medias/2000/attributes
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 删除指定项目下指定的媒体

    DELETE /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

当该项目下媒体存在广告位时，不能删除媒体。

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/medias/attributes
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
