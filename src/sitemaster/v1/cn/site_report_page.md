---
weight: 6
layout: default
category: sitemaster
subcategory: site_report
language: cn
title: 页面维度统计数据
version: v1
---

# 页面维度统计数据

* TOC
{:toc}


## 可用维度和指标

维度

| 维度         | 说明     |
|--------------|----------|
| dm:host      | 主机     |
| dm:pageTitle | 页面标题 |
| dm:pagePath  | 页面URL  |

指标

| 指标               | 说明               |
|--------------------|--------------------|
| mt:pageviews       | PV页面浏览量       |
| mt:bounces         | 跳出次数           |
| mt:entrances       | 进入次数           |
| mt:timeOnPage      | 平均停留时间       |
| mt:exits           | 退出次数           |
| mt:pageLoadTime    | 平均加载时间       |
| mt:pageLoadSample  | 页面加载时间样本数 |
| mt:uniquePageViews | 平均唯一页面浏览量 |

## 资源地址

    GET /sites/:site_id/reports/page

### 参数

| 参数名      | 使用说明                                                     |
|-------------|--------------------------------------------------------------|
|start-date   |数据时间范围的起始时间 start-date=2013-09-03|
|end-date     |数据时间范围的结束时间 end-date=2013-09-09|
| filters     | 可使用维度和指标任意组合做为查询条件                         |
| dimensions  | 维度，多个用逗号开个，最多支持3个维度                        |
| sort        | 指定排序字段，可使用任意指标为排序字段，默认为自然排序       |
| start-index | 可选 integer -数据开始条目序号                               |
| max-results | 可选 integer -数据条目最大条目数(系统限制小于5000，否则异常) |

### 响应


{:.prettyprint}
    Status: 200 OK

{:.prettyprint}
    [
        {
            dm:host: 'http://google.com',
            dm:pageTitle: 'Test',
            dm:pagePath: '/test',
            mt:pageviews: 100
            mt:bounces: 100
            mt:entrances: 100
            mt:uniquePageViews: 100
            mt:timeOnPage: 100
            mt:exits: 100
            mt:pageLoadTime: 100
            mt:pageLoadSample: 100
        },
        ...
    ]

