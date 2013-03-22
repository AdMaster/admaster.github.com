---
weight: 6
layout: default
category: sitemaster
subcategory: site_report
language: cn
title: 广告维度统计数据
---

# 广告维度统计数据

* TOC
{:toc}

## 可用维度和指标

维度

| 维度                | 说明                                    |
|---------------------|-----------------------------------------|
| dm:campaign         | 活动                                    |
| dm:medium           | 媒体                                    |
| dm:placement        | 广告位                                  |
| dm:creative         | 创意                                    |
| dm:keyword          | 关键词                                  |
| dm:cookieSourceType | 来源类型，可选值view(曝光)，click(点击) |

指标: [常规指标](/doc/sitemaster/v1/cn/site_report.html#section-2)

## 资源地址

    GET /sites/:site_id/reports/ad

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
    [
        {
            ...
            dm:placement: 'ad3',
            dm:creative: 'intel',
            mt:visits: 100,
            mt:pageviews: 100,
            mt:newVisits: 100,
            mt:bounces: 100,
            mt:entrances: 100,
            uniquePageViews: 100,
            mt:timeOnPage: 100,
            mt:exits: 100,
            mt:pageLoadTime: 100,
            pageLoadSample: 100,
            mt:newVisitsRatio: 0.99,
            mt:bounceRatio: 0.1,
        },
        ...
    ]
