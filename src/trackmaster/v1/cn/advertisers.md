---
weight: 15
layout: default
category: trackmaster
language: cn
title: 广告主
version: v1
---


# 广告主对接指南

* TOC
{:toc}


TrackMaster™ 所有 API 的访问都是通过 HTTP 执行的，所有被发送和接收的数据都是 JSON。

TrackMaster™ 使用 OAuth2.0 对用户进行验证，保障用户的隐私和安全性。

请在开发前先阅读 [快速入门](http://dev.admaster.com.cn/doc/openmaster/v1/cn/get_started.html)、[OAuth 认证](http://dev.admaster.com.cn/doc/openmaster/v1/cn/oauth.html)、[协议及请求方式](http://dev.admaster.com.cn/doc/openmaster/v1/cn/verbs.html)、[接口定义-通用说明](http://dev.admaster.com.cn/doc/openmaster/v1/cn/common.html)。


## 第一步 获取访问令牌

    POST http://open.admaster.com.cn/oauth/access_token

**参数**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "password",
      "email": "yourmailaddress@email.com",
      "password": "***"
    }

**响应**

    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "18000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }

`access_token`在`expires_in`秒内有效，超期后请重新访问该接口获取新的访问令牌，携带参数：

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## 第二步 获取广告主项目列表

    GET http://track.admasterapi.com/advertisers/:advertiser_id/campaigns

**参数**

第一步中获取到的`access_token`

    access_token=***

**响应**

    [
      {
        "id": 1,
        "name": "测试项目",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 第三步 获取项目报告

    GET /advertisers/campaigns/:campaign_id/reports

**参数**

`time`
: _必选_ **string** - 数据时间类型,与参数 `start_time` 和 `end_time` 共同使用。

  * `hourly` 获取小时数据
  * `daily` 获取日数据

`dims`
: _可选_ **string** - 数据聚合维度,多个选项之间用`,`分开

  * `media` 按媒体维度聚合
  * `placement` 按广告位维度聚合
  * `keyword` 按关键字维度聚合
  * `creative` 按创意维度聚合
  * `province` 按省级地域维度聚合
  * `time` 按时间维度聚合    

`network_media_id`
: _可选_ **integer** - 网络媒体 ID

`placement_id`
: _可选_ **integer** - 广告位 ID

`keyword_id`
: _可选_ **integer** - 关键字 ID

`creative_id`
: _可选_ **integer** - 创意 ID

`geo_id`
: _可选_ **integer** - 地域 ID

`start_time`
: _可选_ **hour** - 开始时间，会列出日期大于等于此设定的项目，与参数`time`一起使用。  
采用国际标准 ISO 8601 的日期和时间显示格式。


  * 当参数 `time` 选择 `小时`，时间格式 YYYY-MM-DDThh:mm:ss+08:00。例 2012-11-06T01:00:00+08:00。仅支持北京时间的时区表示，输出格式同样为 YYYY-MM-DDThh:mm:ss+08:00。

  * 当参数 `time` 选择 `天`，时间格式 YYYY-MM-DD。例 2012-11-06。



`end_time`
: _可选_ **hour** - 结束时间，会列出日期小于等于此设定的项目，与参数`time`一起使用。  
采用国际标准 ISO 8601 的日期和时间显示格式。

  * 当参数 `time` 选择 `小时`，时间格式 YYYY-MM-DDThh:mm:ss+08:00。例 2012-11-06T01:00:00+08:00。仅支持北京时间的时区表示，输出格式同样为 YYYY-MM-DDThh:mm+08:00。

  * 当参数 `time` 选择 `天`，时间格式 YYYY-MM-DD。例 2012-11-06。



`sort`
: _可选_ **string** - 列表排序以什么排序

  * `time` - 按照时间排序
  * `imp` - 按照曝光排序
  * `clk` - 按照点击排序
  * `uimp` - 按照独立曝光排序
  * `uclk` - 按照独立点击排序
  * `network_media_id` - 按照网络媒体 ID 排序
  * `placement_id` - 按照广告位 ID 排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序


**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/campaigns/10185/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/campaigns/10185/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,//项目 ID
        "network_media_id": 1484,//媒体网络 ID
        "time": "2012-08-03",//此处 `time` 格式与参数 `start_time`、`end_time` 一致，例如当参数`time`为 daily，则此处时间为从 `start_time` 到 `end_time` 分天时间.
        "imp": 90,//曝光数
        "uimp": 60,//独立曝光数
        "clk": 30,//点击数
        "uclk": 23,//独立点击数
      }
    ]



**详情参见**

[广告主项目报告](/doc/trackmaster/v1/cn/advertisers_report.html)    
[协议及请求说明](/doc/openmaster/v1/cn/verbs.html)

