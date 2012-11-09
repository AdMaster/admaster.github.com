---
weight: 12
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 项目报告
---

# 项目报告

* TOC
{:toc}

## 获取指定项目下有操作权限的项目报告列表

    GET /campaigns/:campaign_id/reports

**参数**

`time`
: _必选_ **string** - 数据时间类型,与参数 `start_time` 和 `end_time` 共同使用。

  * `hourly` 获取小时数据
  * `daily` 获取日数据
  * `weekly` 获取周数据
  * `monthly` 获取月数据

`dims`
: _可选_ **string** - 数据聚合维度,多个选项之间用`,`分开。

  * `media` 按媒体维度聚合
  * `placement` 按广告位维度聚合
  * `keyword` 按关键字维度聚合
  * `creative` 按创意维度聚合
  * `geo` 按地域维度聚合
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
当参数 `time` 选择 `小时`，时间格式 YYYY-MM-DDThh:mmZ。例 2012-11-06T01:57Z。
当参数 `time` 选择 `天`，时间格式 YYYY-MM-DD。例 2012-11-06。
当参数 `time` 选择 `周`，时间格式 YYYY-Www。例 2005-W01。
当参数 `time` 选择 `月`，时间格式 YYYY-MM。例 2005-01。

`end_time`
: _可选_ **hour** - 结束时间，会列出日期小于等于此设定的项目，与参数`time`一起使用。
采用国际标准 ISO 8601 的日期和时间显示格式。
当参数 `time` 选择 `小时`，时间格式 YYYY-MM-DDThh:mmZ。例 2012-11-06T01:57Z。
当参数 `time` 选择 `天`，时间格式 YYYY-MM-DD。例 2012-11-06。
当参数 `time` 选择 `周`，例 2005-W01，表示选择 2005 年的第一周。
当参数 `time` 选择 `月`，时间格式 YYYY-MM。例 2005-01。

`sort`
: _可选_ **string** - 列表排序以什么排序，结合参数`direction`使用。

  * `time` - 按照时间排序
  * `imp` - 按照曝光排序
  * `clk` - 按照点击排序
  * `uimp` - 按照独立曝光排序
  * `uclk` - 按照独立点击排序


`direction`
: _可选_ **string** - 排序方式，结合参数`sort`使用。

  * `asc` 升序 (_默认_)
  * `desc` 降序


**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,//项目 ID
        "network_media_id": 1484,//媒体网络 ID
        "time": "2012-08-03",//此处 `time` 格式与参数 `start_time`、`end_time` 一致，例如当参数`time`为 daily，则此处时间为从 `start_time` 到 `end_time` 分天时间.
        "imp": 90,//曝光数
        "uimp": 60,//独立曝光数
        "ipuimp": 56,//独立曝光 IP 数
        "clk": 30,//点击数
        "uclk": 23,//独立点击数
        "ipuclk": 27//独立点击 IP 数
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

不是所有的属性都可以搭配获取数据，只有特定的组合才可以获取到相应数据。当选择了 dims=time 时，可以按时间粒度分开显示，当维度中未选择 time 时，将按时间分组聚合。

组合|说明
daily_campaign  |粒度为天，项目数据
daily_campaign_geo => time=daily&dims=geo  |粒度为天，项目分地域数据
daily_campaign_media  |粒度为天，项目分媒体数据
daily_campaign_media_geo => time=daily&dims=media,geo  |粒度为天，项目分媒体分地域数据
daily_campaign_media_placement  |粒度为天，项目分媒体分广告位数据
daily_campaign_media_placement_geo  |粒度为天，项目分媒体分广告位分地域数据
daily_campaign_media_placement_keyword  |粒度为天，项目分媒体分广告位分关键字数据
hourly_campaign  |粒度为小时，项目数据
hourly_campaign_creative  |粒度为小时，项目分创意数据
hourly_campaign_geo  |粒度为小时，项目分地域数据
hourly_campaign_media  |粒度为小时，项目分媒体数据
hourly_campaign_media_creative  |粒度为小时，项目分媒体分创意数据
hourly_campaign_media_geo  |粒度为小时，项目分媒体分地域数据
hourly_campaign_media_placement  |粒度为小时，项目分媒体分广告位数据
hourly_campaign_media_placement_creative  |粒度为小时，项目分媒体分广告位分创意数据
hourly_campaign_media_placement_geo  |粒度为小时，项目分媒体分广告位分地域数据
hourly_campaign_media_placement_keyword  |粒度为小时，项目分媒体分广告位分关键字数据
monthly_campaign  |粒度为月，项目数据
monthly_campaign_media  |粒度为月，项目分媒体数据
monthly_campaign_media_placement  |粒度为月，项目分媒体分广告位数据
monthly_campaign_media_placement_keyword  |粒度为月，项目分媒体分广告位分关键字数据
weekly_campaign  |粒度为周，项目数据
weekly_campaign_media  |粒度为周，项目分媒体数据
weekly_campaign_media_placement  |粒度为周，项目分媒体分广告位数据
weekly_campaign_media_placement_keyword  |粒度为周，项目分媒体分广告位分关键字数据


