---
weight: 6
layout: default
category: sitemaster
subcategory: report
language: cn
title: 停留时间维度统计数据
---

# 停留时间维度统计数据

* TOC
{:toc}

维度

| 维度     | 说明     |
|----------|----------|
| stayTime | 停留时间 |

指标: [常规指标](/doc/sitemaster/v1/cn/site_report.html#常规指标)


##资源地址

    GET /sites/:site_id/reports/staytime

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
            stayTime: 22
            visits: 100,
            pageviews: 100,
            newVisits: 100,
            bounces: 100,
            entrances: 100,
            uniquePageViews: 100,
            timeOnPage: 100,
            exists: 100,
            pageLoadTime: 100,
            pageLoadSample: 100,
            newVisitsRatio: 0.99,
            bounceRatio: 0.1,
        },
        ...
    ]


| 字段            | 说明             |
|-----------------|------------------|
| stayTime        | 停留时间         |
| visits          | 总访次           |
| pageviews       | 总页面访问量     |
| newVisits       | 新访问次数       |
| bounces         | 总跳出次数       |
| entrances       | 进入总次数       |
| exits           | 总退出次数       |
| uniquePageviews | 页面唯一访问量   |
| timeOnPage      | 平均页面停留时间 |
| pageLoadTime    | 平均页面加载时间 |
| newVisitsRatio  | 新访比例         |
| bounceRatio     | 跳出比例         |
