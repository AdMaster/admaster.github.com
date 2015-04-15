---
weight: 13
layout: default
category: trackmaster
subcategory: publisher
language: cn
title: 媒体报告
version: v2
---

# 媒体报告

* TOC
{:toc}

## 获取指定媒体下的项目

    GET http://m.trackmaster.com.cn/api_v2/medias/:media_id/campaigns

**响应**

    Status: 200 OK

{:.prettyprint}
      {
        "id": 10185,
        "name": "测试项目",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    

## 获取指定项目下的报告

    GET http://m.trackmaster.com.cn/api_v2/medias/:media_id/campaigns/:campaign_id/reports/basics

**参数**

* `startDate` 必填，开始日期或者时间
* `endDate` 必填，结束日期或者时间
* `dimensions` 选填，数据查询纬度，可以多个，多个之间用逗号分隔
* `metrics` 必填，数据查询指标，可以是多个，多个之间用逗号分隔
* `filters` 过滤条件，用分号(;) 分隔and逻辑，用逗号(,)分隔or逻辑filters=mediaId==1018;geoId==310021,placementId=50000012;imp>1000;clk>10
* `sort` 排序方式, 降序排列的时候需要在排序方式前加减号(-)
* `startIndex` 数据从第几条开始，默认为 0
* `maxResults` 最多返回多少条结果，默认为 30

报告结果的返回头部信息 X-Content-Record-Total 值为结果条目总数，如果需要控制翻页，请修改`startIndex` 和 `maxResults` 的值。

**响应**

    Status: 200 OK


{:.prettyprint}
      {
        "time": "2012-08-01", // 时间
        "imp": 23, //曝光
        "uimp": 20, //独立曝光
        "clk": 20, //点击
        "uclk": 10, //独立点击
      }
      

## 获取IES报告

	GET /medias/:mediaId/reports/ies

**参数**

`pub_id`
: _可选_ **string** - pub_id 指定后只获取该 pub_id 的数据

`date`
: _可选_ **date** - 日期，要查看的数据日期，YYYY-mm-dd 例如: 2012-06-08, 不指定则获取前一天的数据

`startIndex`
: _可选_ **integer** - 数据从第几条开始，默认为 0

`maxResults`
: _可选_ **integer** - 最多返回多少条结果，默认为 30,最大为 5000


{:.prettyprint}
	[{
  	"id": 30,
  	"mediaId":100,
  	"geoId": 1100000000,  		
  	"pubId": "PUB_IMloxn12345",
  	"imp": 12039423,
  	"clk": 43432
	}]


**字段说明**

返回值字段 | 字段类型     | 字段说明
imp      | integer     | 曝光
uimp     | integer     | 独立曝光
clk      | integer     | 点击
uclk     | integer     | 独立点击

**获取数据组合说明**

不是所有的属性都可以搭配获取数据，只有特定的组合才可以获取到相应数据。当选择了 dims=time 时，显示内容按时间分组聚合。


组合|说明
time=daily  |粒度为天，指定媒体指定项目数据
time=daily&dims=province|粒度为天，指定媒体指定项目分省级地域数据
time=daily&dims=creative |粒度为天，指定媒体指定项目分创意数据
time=daily&dims=placement|粒度为天，指定媒体指定项目分广告位数据
time=daily&dims=placement,province|粒度为天，指定媒体指定项目分广告位分省级地域数据
time=daily&dims=placement,keyword|粒度为天，指定媒体指定项目分广告位分关键字数据
time=daily&dims=placement,creative |粒度为天，指定媒体指定项目分广告位分创意数据
time=hourly|粒度为小时，指定媒体指定项目数据
time=hourly&dims=creative |粒度为小时，指定媒体指定项目分创意数据
time=hourly&dims=province|粒度为小时，指定媒体指定项目分省级地域数据
time=hourly&dims=placement|粒度为小时，指定媒体指定项目分广告位数据
time=hourly&dims=placement,creative |粒度为小时，指定媒体指定项目分广告位分创意数据
time=hourly&dims=placement,province|粒度为小时，指定媒体指定项目分广告位分省级地域数据



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
