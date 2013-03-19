---
weight: 6
layout: default
category: sitemaster
subcategory: report
language: cn
title: 事件维度统计数据
---

# 事件维度统计数据

* TOC
{:toc}

维度

| 维度     | 说明     |
|----------|----------|
| action   | 事件动作 |
| category | 事件分类 |
| label    | 事件标签 |


指标

| 指标         | 说明       |
|--------------|------------|
| totalEvents  | 事件总数   |
| uniqueEvents | 唯一事件数 |
| totalEvents  | 事件总值   |

## 统计结果查询

###资源地址

    GET /sites/:site_id/reports/event

### 参数


| 参数名 | 使用说明                         |
|--------|----------------------------------|
| query  | 可使用任意维度和指标做为查询条件 |

### 响应

| 字段         | 说明       |
|--------------|------------|
| totalEvents  | 事件总数   |
| uniqueEvents | 唯一事件数 |
| totalEvents  | 事件总值   |


### 示例

#### 请求

指定查询日期在2012-1-1至2013-1-1区间内，指定事件位的访问情况

    GET /sites/1/reports/event?query=from_date%3E%3D2012-1-1%3Bend_date%3C%3D2013-1-1%3Bplacement%3D%3D%E5%8C%97%E4%BA%AC

#### 响应

{:.prettyprint}
    {
        totalEvents: 100,
        uniqueEvents: 100,
        totalValue: 100
    }

## 数据明细查询

### 资源地址

    GET /sites/:site_id/reports/event/detail

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

| 字段         | 说明       |
|--------------|------------|
| action       | 动作       |
| category     | 事件分类   |
| label        | 事件标签   |
| totalEvents  | 事件总数   |
| uniqueEvents | 唯一事件数 |
| totalValue   | 事件价值   |


### 示例

#### 请求

定查询日期在2012-1-1至2013-1-1区间内，指定事件位的的访问明细

    GET /sites/1/reports/event/detail?query=date%3E%3D2012-1-1%3Bdate%3C%3D2013-1-1%3Bcity%3D%3D%E5%8C%97%E4%BA%AC&dim=action

#### 响应

{:.prettyprint}
    Status: 200 OK
    Link: <http://site.admasterapi.com/sites/12/reports/event?page=2>; rel="next",
          <http://site.admasterapi.com/sites/12/reports/event/detail?page=10>; rel="last"

{:.prettyprint}
    [
        {
            action: 'order',
            category: 'click',
            label: 'b2c',
            totalEvents: 100,
            uniqueEvents: 100,
            totalValue: 1000,
        },
        ...
    ]
