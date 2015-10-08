---
weight: 5
layout: default
category: sitemaster_hide!!!!!
language: cn
### title: 数据银行数据分析接口
version: v1
---

# 数据银行数据分析接口

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


## API 目录

* [数据银行访次分析](/doc/sitemaster/v1/cn/site_databank_visit.html)
* [数据银行页面浏览分析](/doc/sitemaster/v1/cn/site_databank_pageview.html)
* [数据银行事件触发分析](/doc/sitemaster/v1/cn/site_databank_event.html)
* [数据银行结果查看](/doc/sitemaster/v1/cn/site_databank_result.html)
