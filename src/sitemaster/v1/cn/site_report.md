---
weight: 5
layout: default
category: sitemaster
language: cn
title: 标准数据接口
---

# 标准数据接口

* TOC
{:toc}

## 概述

本API主要提供离线分析数据获取功能，为非实时数据源，数据具有一定延时。

## API 说明

每个接口均以filters做为查询参数。filters可提供丰富的自定义查询条件组合功能，以实现灵活和自由的查询功能。详见 [filters查询语法](#filters)

## filters查询语法

filters查询用法及说明如下


| 用法                                       | 说明                                                                                                         |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| start-date==2012-1-1                       | 指定start-date查询条件“等于”2012-1-1                                                                         |
| start-date==2012-1-1;end-date==2013-1-1    | 指定start-date“等于”2012-1-1，“且”end-date“等于”2013-1-1。<br />该条件指定查询2012-1-1至2013-1-1间的统计数据 |
| dm:domain==google.com,dm:domain==baidu.com | 指定来源域名为google.com“或 ”baidu.com“或”apple.com                                                          |

### 查询语法

| 操作符 | 描述             | URL编码格式 | 举例                                                              |
|--------|------------------|-------------|-------------------------------------------------------------------|
| ==     | 等于             | %3D%3D      | filters=mt:timeOnPage%3D%3D10，返回页面停留时间等于10秒的结果     |
| !=     | 不等于           | !%3D        | filters=mt:timeOnPage!%3D10,返回页面停留时间不等于10秒的结果      |
| >      | 大于             | %3E         | filters=mt:timeOnPage%3E10，返回页面停留时间大于10秒的结果        |
| <      | 小于             | %3C         | filters=mt:timeOnPage%3C10，返回页面停留时间小于10秒的结果        |
| >=     | 大于等于         | %3E%3D      | filters=mt:timeOnPage%3E%3D10，返回页面停留时间大于等于10秒的结果 |
| <=     | 小于等于         | %3C%3       | filters=mt:timeOnPage%3C%3D10，返回页面停留时间小于等于10秒的结果 |
| =@     | 包含子串         | %3D@        | filters=dm:city%3D@York，返回城市名中包含 York 字符的统计指标数据    |
| !@     | 不包含子串       | !@          | filters=dm:city!@York，返回城市名中不包含 York 字符的统计指标数据    |
| =~     | 和后面语法匹配   | %3D~        | filters=dm:city%3D~%5ENew.* ，返回城市名以 New 开头的统计指标数据    |
| !~     | 和后面语法不匹配 | !~          | filters=dm:city!~%5ENew.* ，返回城市名不以 New 开头的统计指标数据    |


### 常规指标和维度

除非特别说明，所有报表接口均支持在filters查询中使用常规指标和常规维度做为查询条件。

常规维度：


| 维度         | 说明                                   |
|--------------|----------------------------------------|
| dm:date      | 日期，格式为YYYY-MM-DD                 |
| dm:month     | 月                                     |
| dm:week      | 周                                     |
| dm:dayOfWeek | 一周中的第几天，如0表示周日，1表示周一 |
| dm:year      | 年                                     |


常规指标：

| 字段               | 说明             |
|--------------------|------------------|
| mt:visits          | 访次数           |
| mt:pageviews       | 总页面访问量     |
| mt:newVisits       | 新访问次数       |
| mt:bounces         | 总跳出次数       |
| mt:entrances       | 进入总次数       |
| mt:exits           | 总退出次数       |
| mt:uniquePageviews | 页面唯一访问量   |
| mt:timeOnPage      | 平均页面停留时间 |
| mt:pageLoadTime    | 平均页面加载时间 |
| mt:newVisitsRate  | 新访比例         |
| mt:bounceRate     | 跳出比例         |

## API 目录

* [地区维度统计数据](/doc/sitemaster/v1/cn/site_report_region.html)
* [广告维度统计数据](/doc/sitemaster/v1/cn/site_report_ad.html)
* [事件维度统计数据](/doc/sitemaster/v1/cn/site_report_event.html)
* [访问频次统计数据](/doc/sitemaster/v1/cn/site_report_freq.html)
* [页面统计数据](/doc/sitemaster/v1/cn/site_report_page.html)
* [访问深度统计数据](/doc/sitemaster/v1/cn/site_report_page_depth.html)
* [页面事件统计数据](/doc/sitemaster/v1/cn/site_report_page_event.html)
* [流量来源统计数据](/doc/sitemaster/v1/cn/site_report_referral.html)
* [搜索引擎统计数据](/doc/sitemaster/v1/cn/site_report_search.html)
* [社交媒体统计数据](/doc/sitemaster/v1/cn/site_report_social.html)
* [停留时间统计数据](/doc/sitemaster/v1/cn/site_report_staytime.html)
* [浏览器统计数据](/doc/sitemaster/v1/cn/site_report_browser.html)
