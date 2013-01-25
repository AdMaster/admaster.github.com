---
weight: 13
layout: default
category: trackmaster
subcategory: publisher
language: cn
title: 媒体报告
---

# 媒体报告

* TOC
{:toc}

## 获取指定媒体下的项目

    GET /medias/:media_id/campaigns

**响应**

    Status: 200 OK

{:.prettyprint}
    [
      {
        "id": 10185,
        "name": "这是一个测试项目",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]

## 获取指定项目下的日报告

    GET /medias/:media_id/campaigns/:campaign_id/daily_reports

**参数**

`start_time`
: _可选_ **date** - 项目开始日期，例如 2012-08-01，会列出项目开始日期大于等于此设定的项目

`end_time`
: _可选_ **date** - 项目结束日期，例如 2012-08-02，会列出项目结束日期小于等于此设定的项目

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `time` - 按照时间排序
  * `imp` - 按照曝光排序
  * `clk` - 按照点击排序
  * `uimp` - 按照独立曝光排序
  * `uclk` - 按照独立点击排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

**响应**

    Status: 200 OK


{:.prettyprint}
    [
      {
        "time": "2012-08-01", // 时间
        "imp": 23, //曝光
        "uimp": 20, //独立曝光
        "clk": 20, //点击
        "uclk": 10, //独立点击
      }
    ]


## 获取指定监测代码下的项目日报告

    GET /medias/campaigns/daily_reports/codes

**参数**

`code`
: _必选_ **string** - 项目监测代码

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/medias/1308/campaigns/10256/daily_reports
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 获取指定监测代码下的项目报告

    GET /medias/campaigns/reports/codes

**参数**

`code`
: _必选_ **string** - 项目监测代码

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/medias/1308/campaigns/10256/reports
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 媒体用户获取 iab 数据

    GET /medias/:id/ies

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/1/ies?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/1/ies?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

**参数**

`pubid`
: _可选_ **string** - pubid 指定后只获取该 pubid 的数据

`date`
: _可选_ **date** - 日期，要查看的数据日期，YYYY-mm-dd 例如: 2012-06-08 ,不指定则获取头一天的数据

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。

{:.prettyprint}
    [
      {
        "date_hour": 2012061015,
        "pubid": "IYK_IMloxnwepMEqlx",
        "city": "北京",
        "geoid": 110000,
        "impression": 12039423,
        "click": 43432,
      }
    ]

## 获取指定媒体项目报告列表

    GET /medias/:media_id/campaigns/:campaign_id/reports

**参数**

`time`
: _必选_ **string** - 数据时间类型,与参数 `start_time` 和 `end_time` 共同使用。

  * `hourly` 获取小时数据
  * `daily` 获取日数据
  * `weekly` 获取周数据
  * `monthly` 获取月数据

`dims`
: _可选_ **string** - 数据聚合维度,多个选项之间用`,`分开

  * `placement` 按广告位维度聚合
  * `keyword` 按关键字维度聚合
  * `creative` 按创意维度聚合
  * `geo` 按地域维度聚合
  * `time` 按时间维度聚合    


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

  * 当参数 `time` 选择 `小时`，时间格式 YYYY-MM-DDThh:mm:ss+08:00。例 2012-11-06T01:57:10+08:00。仅支持北京时间的时区表示，输出格式同样为 YYYY-MM-DDThh:mm:ss+08:00。

  * 当参数 `time` 选择 `天`，时间格式 YYYY-MM-DD。例 2012-11-06。

  * 当参数 `time` 选择 `周`，时间格式 YYYY-Www。例 2005-W01。

  * 当参数 `time` 选择 `月`，时间格式 YYYY-MM。例 2005-01。

`end_time`
: _可选_ **hour** - 结束时间，会列出日期小于等于此设定的项目，与参数`time`一起使用。  
采用国际标准 ISO 8601 的日期和时间显示格式。

  * 当参数 `time` 选择 `小时`，时间格式 YYYY-MM-DDThh:mm:ss+08:00。例 2012-11-06T01:57:10+08:00。仅支持北京时间的时区表示，输出格式同样为 YYYY-MM-DDThh:mm:ss+08:00。

  * 当参数 `time` 选择 `天`，时间格式 YYYY-MM-DD。例 2012-11-06。

  * 当参数 `time` 选择 `周`，时间格式 YYYY-Www。例 2005-W01，表示选择 2005 年的第一周。

  * 当参数 `time` 选择 `月`，时间格式 YYYY-MM。例 2005-01。

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `time` - 按照时间排序
  * `imp` - 按照曝光排序
  * `clk` - 按照点击排序
  * `uimp` - 按照独立曝光排序
  * `uclk` - 按照独立点击排序
  * `placement_id` - 按照广告位 ID 排序

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
    Link: <http://{{site.track_api_host}}/medias/1/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/1/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,
        "time": "2012-08-03",
        "imp": 9,
        "uimp": 6,
        "ipuimp": 6,
        "clk": 3,
        "uclk": 3,
        "ipuclk": 2
      }
    ]

**字段说明**

返回值字段 | 字段类型     | 字段说明
imp      | integer     | 曝光
uimp     | integer     | 独立曝光
ipuimp   | integer     | IP独立曝光
clk      | integer     | 点击
uclk     | integer     | 独立点击
ipuclk   | integer     | IP独立点击

**获取数据组合说明**

不是所有的属性都可以搭配获取数据，只有特定的组合才可以获取到相应数据。当选择了 dims=time 时，显示内容按时间分组聚合。


组合|说明
time=daily  |粒度为天，指定媒体指定项目数据
time=daily&dims=geo|粒度为天，指定媒体指定项目分地域数据
time=daily&dims=creative |粒度为天，指定媒体指定项目分创意数据
time=daily&dims=placement|粒度为天，指定媒体指定项目分广告位数据
time=daily&dims=placement,geo|粒度为天，指定媒体指定项目分广告位分地域数据
time=daily&dims=placement,keyword|粒度为天，指定媒体指定项目分广告位分关键字数据
time=daily&dims=placement,creative |粒度为天，指定媒体指定项目分广告位分创意数据
time=hourly|粒度为小时，指定媒体指定项目数据
time=hourly&dims=creative |粒度为小时，指定媒体指定项目分创意数据
time=hourly&dims=geo|粒度为小时，指定媒体指定项目分地域数据
time=hourly&dims=placement|粒度为小时，指定媒体指定项目分广告位数据
time=hourly&dims=placement,creative |粒度为小时，指定媒体指定项目分广告位分创意数据
time=hourly&dims=placement,geo|粒度为小时，指定媒体指定项目分广告位分地域数据
time=hourly&dims=placement,keyword|粒度为小时，指定媒体指定项目分广告位分关键字数据
time=monthly|粒度为月，指定媒体指定项目数据
time=monthly&dims=placement|粒度为月，指定媒体指定项目分广告位数据
time=monthly&dims=placement,keyword|粒度为月，指定媒体指定项目分广告位分关键字数据
time=weekly|粒度为周，指定媒体指定项目数据
time=weekly&dims=placement|粒度为周，指定媒体指定项目分广告位数据
time=weekly&dims=placement,keyword |粒度为周，指定媒体指定项目分广告位分关键字数据

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
            "ipuimp": 3,
            "ipuclk": 4
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
            "ipuimp": 27,
            "ipuclk": 24
        }
    ]
