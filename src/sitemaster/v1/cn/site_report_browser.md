---
weight: 6
layout: default
category: sitemaster
subcategory: site_report
language: cn
title: 浏览器维度统计数据
---

# 浏览器维度统计数据

* TOC
{:toc}


## 可用维度和指标

维度

| 维度                      | 说明             |
|---------------------------|------------------|
| dm:browser                | 浏览器名称       |
| dm:browserVersion         | 浏览器版本       |
| dm:operatingSystem        | 操作系统名称     |
| dm:operatingSystemVersion | 操作系统版本     |
| dm:isMobile               | 是否移动设备     |
| dm:wifiEnabled            | 是否启用Wifi     |
| dm:mobileDeviceBranding   | 移动设备品牌     |
| dm:mobileDeviceModel      | 移动设备型号     |
| dm:mobileInputSelector    | 移动设备输入方式 |

指标: [常规指标](/doc/sitemaster/v1/cn/site_report.html#section-2)


## 资源地址

    GET /sites/:site_id/reports/ua

### 参数


| 参数名      | 使用说明                                                     |
|-------------|--------------------------------------------------------------|
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
            dm:browser: 'Chrome',
            dm:browserVersion: '1.0.0',
            dm:operatingSystem: 'Mac OSX',
            dm:operatingSystemVersion: '10.8.4',
            mt:visits: 100,
            mt:pageviews: 100,
            mt:newVisits: 100,
            mt:bounces: 100,
            mt:entrances: 100,
            mt:uniquePageViews: 100,
            mt:timeOnPage: 100,
            mt:exits: 100,
            mt:pageLoadTime: 100,
            mt:newVisitsRate: 0.99,
            mt:bounceRate: 0.1,
        },
        ...
    ]
