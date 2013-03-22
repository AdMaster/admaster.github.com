---
weight: 6
layout: default
category: sitemaster
subcategory: report
language: cn
title: 搜索维度统计数据
---

# 搜索维度统计数据

* TOC
{:toc}


## 可用维度和指标

维度

| 维度    | 说明         |
|---------|--------------|
| dm:domain  | 搜索引擎域名 |
| dm:keyword | 搜索关键词   |

指标: [常规指标](/doc/sitemaster/v1/cn/site_report.html#常规指标)


##资源地址

    GET /sites/:site_id/reports/search

### 参数

| 参数名      | 使用说明                                                     |
|-------------|--------------------------------------------------------------|
| filters     | 可使用维度和指标任意组合做为查询条件                         |
| dimensions  | 维度，多个用逗号开个，最多支持3个维度                        |
| sort        | 指定排序字段，可使用任意指标为排序字段，默认为自然排序       |
| start-index | 可选 integer -数据开始条目序号                               |
| max-results | 可选 integer -数据条目最大条目数(系统限制小于5000，否则异常) |


### 响应


| 字段                 | 说明             |
|----------------------|------------------|
| dm:domain            | 访问次数         |
| dm:keyword           | 关键词           |
| mt:visits            | 总访次           |
| mt:pageviews         | 总页面访问量     |
| mt:newVisits         | 新访问次数       |
| mt:bounces           | 总跳出次数       |
| mt:entrances         | 进入总次数       |
| mt:exits             | 总退出次数       |
| mt:mt:uniquePageviews   | 页面唯一访问量   |
| mt:timeOnPage        | 平均页面停留时间 |
| mt:pageLoadTime      | 平均页面加载时间 |
| mt:newVisitsRatio | 新访比例         |
| mt:bounceRatio       | 跳出比例         |
