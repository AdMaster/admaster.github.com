---
weight: 12
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 项目报告
version: v2
---

# 项目报告

* TOC
{:toc}

## 获取指定项目下有操作权限的项目报告列表

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:campaign_id/reports/basics

**参数**

* `startDate` 必填，开始日期或者时间
* `endDate` 必填，结束日期或者时间
* `dimensions` 选填，数据查询纬度，可以多个，多个之间用逗号分隔
* `metrics` 必填，数据查询指标，可以是多个，多个之间用逗号分隔
* `filters` 过滤条件，用分号(;) 分隔and逻辑，用逗号(,)分隔or逻辑filters=mediaId==1018;geoId==310021,placementId=50000012;imp>1000;clk>10
* `sort` 排序方式, 降序排列的时候需要在排序方式前加减号(-)
* `startIndex` 数据从第几条开始，默认为 0
* `maxResults` 最多返回多少条结果，默认为 10，最大为 5000

报告结果的返回头部信息 X-Content-Record-Total 值为结果条目总数，如果需要控制翻页，请修改`startIndex` 和 `maxResults` 的值。

**响应**

  {:.prettyprint}
	  [{
	  "date": "2014-07-11",
	  "media": 1018
	  "imp": 12133323,
	  "clk": 7832
		}]


**可用 dimensions （维度）**

* media 媒体
* placement 广告位
* keyword 关键词
* creative 创意
* province 省
* city  市
* os  操作系统
* app 应用
* network 设备网络类型
* deviceType 设备类型
* factory 设备生产厂商
* model 设备机型
* date 日期
* hour 小时

**维度所有可能的组合, 每行一个组合**

* media
* placement
* creative
* province
* city
* os
* app
* network
* deviceType
* factory
* model
* date
* hour

* media, placement
* media, creative
* media, province
* media, city
* media, os
* media, app
* media, network
* media, deviceType
* media, factory
* media, model

* placement, keyword
* placement, creative
* placement, province
* placement, city
* placement, os
* placement, app
* placement, network
* placement, deviceType
* placement, factory
* placement, model

* media, placement, keyword
* media, placement, creative
* media, placement, province
* media, placement, city
* media, placement, os
* media, placement, app
* media, placement, network
* media, placement, deviceType
* media, placement, factory
* media, placement, model

* date, media
* date, placement
* date, creative
* date, province
* date, city
* date, os
* date, app
* date, network
* date, deviceType
* date, factory
* date, model

* date, media, placement
* date, media, creative
* date, media, province
* date, media, city
* date, media, os
* date, media, app
* date, media, network
* date, media, deviceType
* date, media, factory
* date, media, model

* date, placement, keyword
* date, placement, creative
* date, placement, province
* date, placement, city
* date, placement, os
* date, placement, app
* date, placement, network
* date, placement, deviceType
* date, placement, factory
* date, placement, model

* date, media, placement, keyword
* date, media, placement, creative
* date, media, placement, province
* date, media, placement, city
* date, media, placement, os
* date, media, placement, app
* date, media, placement, network
* date, media, placement, deviceType
* date, media, placement, factory
* date, media, placement, model

* hour, media
* hour, placement
* hour, creative
* hour, province
* hour, city

* hour, placement, keyword
* hour, placement, creative
* hour, placement, province
* hour, placement, city

* hour, media, placement, keyword
* hour, media, placement, creative
* hour, media, placement, province
* hour, media, placement, city




**filters**

* 过滤的条件必须和查询的纬度必须是可以的维度组合
* 过滤的指标必须是已选择的指标

sort 可以以某个纬度或者指标来排序


**字段说明**

* imp 曝光数
* clk 点击数
* uimp 唯一曝光数
* uclk 唯一点击数

**示例**

维度参数包括 time，显示内容按时间分组聚合。

{:.prettyprint}
    [
        {
            "campaign_id": 10116,
            "time": "2012-11-01",
            "imp": 3,
            "uimp": 3,
            "clk": 7,
            "uclk": 7,
        },
        {
            "campaign_id": 10116,
            "time": "2012-11-02",
        …
    ]

维度参数不选择 time

{:.prettyprint}
    [
        {
            "campaign_id": 10116,
            "imp": 28,
            "uimp": 27,
            "clk": 72,
            "uclk": 39,
        }
    ]

