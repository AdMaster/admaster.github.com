---
weight: 6
layout: default
category: sitemaster
subcategory: report
language: cn
title: 访问频次维度统计数据
---

# 访问频次维度统计数据

* TOC
{:toc}

维度

| 维度      | 说明       |
|-----------|------------|
| times     | 访问次数   |

指标: [常规指标](/doc/sitemaster/v1/cn/site_report.html#常规指标)

## 统计结果查询

###资源地址

    GET /sites/:site_id/reports/freq

### 参数


| 参数名 | 使用说明                             |
|--------|--------------------------------------|
| query  | 可使用维度和指标任意组合做为查询条件 |

### 响应


| 字段            | 说明             |
|-----------------|------------------|
| visits          | 总访问次数       |
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


### 示例

#### 请求

指定查询日期在2012-1-1至2013-1-1区间内的统计数据

    GET /sites/1/reports/freq?query=from_date%3E%3D2012-1-1%3Bend_date%3C%3D2013-1-1%3Btimes%3D%3D3

#### 响应

{:.prettyprint}
    {
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
    }

## 数据明细查询

### 资源地址

    GET /sites/:site_id/reports/freq/detail

### 请求参数


| 参数名   | 使用说明                                                       |
|----------|----------------------------------------------------------------|
| query    | 可使用维度和指标任意组合做为查询条件                           |
| dim      | 可使用任意维度做为显示维度                                     |
| sort     | 指定排序字段，可使用的可使用任意指标为排序字段，默认为自然排序 |
| page     | 指定显示页面数，默认为1                                        |
| per_page | 指定单页显示个数，默认为20                                     |

### 响应

以数组形式返回多个以下规格的对象

| 字段            | 说明             |
|-----------------|------------------|
| times           | 访问次数         |
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


### 示例

#### 请求

定查询日期在2012-1-1至2013-1-1区间内，指定访问频次位的的访问明细

    GET /sites/1/reports/freq/detail?query=date%3E%3D2012-1-1%3Bdate%3C%3D2013-1-1&dim=times

#### 响应

{:.prettyprint}
    Status: 200 OK
    Link: <http://site.admasterapi.com/sites/12/reports/freq?page=2>; rel="next",
          <http://site.admasterapi.com/sites/12/reports/freq/detail?page=10>; rel="last"

{:.prettyprint}
    [
        {
            times: 3
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





















---
weight: 5
layout: default
category: sitemaster
subcategory: report
language: cn
title: 站点分析报告
---

# 报表

* TOC
{:toc}

## 访问频次API

### 资源地址

    GET /sites/:site_id/report/freq

### 参数


| 参数名 | 使用说明                                                                                                                                                                                                |
|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| query  | 查询字串，可按不同条件自定义组合。可使用的查询字段为date，times
| fields | 查询字段，至少从以下字段中选择一个：visits，pageviews，newVisits，bounces，entrances，uniquePageviews，timeOnPage，exists，pageLoadTime，pageLoadSample。默认查询所有字段，多个字段使用“,”半角逗号分隔 |

#### Query可用字段说明

| 字段     | 说明                                                              |
|----------|-------------------------------------------------------------------|
| date     | 查询日期区间                                                      |
| times    | 访问次数                                                          |

### 响应


| 字段            | 说明             |
|-----------------|------------------|
| visits          | 访问次数         |
| pageviews       | 页面访问量       |
| newVisits       | 新访问次数       |
| bounces         | 跳出次数         |
| entrances       | 进入次数         |
| uniquePageviews | 页面唯一访问量   |
| timeOnPage      | 平均页面停留时间 |
| exists          | 退出次数         |
| pageLoadTime    | 页面加载时间     |


### 示例

#### 请求

    GET /sites/1/report/freq?query=date%3E%3D2012-1-1%3Bdate%3C%3D2013-1-1%times%3D%3D5

#### 响应

    {
        visits: 100,
        pageviews: 100,
        newVisits: 100,
        bounces: 100,
        entrances: 100,
        uniquePageViews: 100,
        timeOnPage: 100,
        exists: 100,
        pageLoadTime: 100,
        pageLoadSample: 100
    }
