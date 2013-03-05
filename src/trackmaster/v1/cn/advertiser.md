---
weight: 3
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 广告主
---

# 广告主

* TOC
{:toc}

## 获取系统广告主列表

    GET /advertisers

**参数**

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照广告主 ID 排序
  * `create_time` - 按照创建日期排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/advertisers?page=2>; rel="next",
          <http://{{site.track_api_host}}/advertisers?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 10199,//广告主 ID
        "url": "http://{{site.track_api_host}}/advertisers/10199",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
      }
    ]


## 获取指定系统广告主信息

    GET /advertisers/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 10199,//广告主 ID
        "url": "http://{{site.track_api_host}}/advertisers/10199",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
    }


## 获取指定工作网络下所有广告主属性列表

    GET /networks/:network_id/advertisers

**参数**

`alias`
: _可选_ **string** - 网络广告主别名，支持模糊查找。


**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "network_id":11,//广告主所属工作网络 ID
        "advertiser_id": 10199,//广告主 ID
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10199",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "status": "enabled",//网络下广告主状态
        "alias": "腾讯",//网络下广告主别名
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
      }
    ]

## 获取指定网络下的指定广告主属性

    GET /networks/:network_id/advertisers/:advertiser_id

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10198/campaigns>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "network_id":11,//广告主所属工作网络 ID
        "advertiser_id": 10198,//广告主 ID
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10198",
        "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //广告主名称
        "status": "enabled",//网络下广告主状态
        "alias": "通用电器",//网络下广告主别名
        "logo": "http://www.trackmaster.com.cn/data/advIcon/GM.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z" //创建时间
        "creator":"name"//创建者
    }

## 添加指定系统广告主到指定工作网络下

    PUT /networks/:network_id/advertisers/:advertiser_id

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10198/campaigns>; rel="campaigns"
    Location: http://{{site.track_api_host}}/networks/11/advertisers/10198
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 修改指定网络下的指定广告主属性

    PATCH /networks/:network_id/advertisers/:advertiser_id

**请求**

{:.prettyprint}
    {
        "alias": "通用电器",//广告主别名
        "status": "enabled"//网络下广告主状态
    }


`alias`
: _可选_ **string** - 别名

`status`
: _可选_ `enabled`, `disabled`

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10198/campaigns>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "advertiser_id": 10198,//广告主 ID
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10198",
        "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //广告主名称
        "status": "enabled"//网络下广告主状态
        "alias": "通用电器",//网络下广告主别名
        "logo": "http://www.trackmaster.com.cn/data/advIcon/GM.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z" //创建时间
    }

## 删除指定工作网络下的指定广告主

    DELETE /networks/:network_id/advertisers/:advertiser_id

当指定工作网络的指定广告主下有项目时，不能删除。

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/networks/11/advertisers>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

