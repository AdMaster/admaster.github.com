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
| dm:eventAction   | 事件动作 |
| dm:eventCategory | 事件分类 |
| dm:eventLabel    | 事件标签 |


指标

| 指标            | 说明       |
|-----------------|------------|
| mt:totalEvents  | 事件总数   |
| mt:uniqueEvents | 唯一事件数 |
| mt:eventValue   | 事件总值   |

## 资源地址

    GET /sites/:site_id/event

## 请求参数

| 参数名      | 使用说明                                                     |
|-------------|--------------------------------------------------------------|
| filters     | 可使用维度和指标任意组合做为查询条件                         |
| dimensions  | 维度，多个用逗号开个，最多支持3个维度                        |
| sort        | 指定排序字段，可使用任意指标为排序字段，默认为自然排序       |
| start-index | 可选 integer -数据开始条目序号                               |
| max-results | 可选 integer -数据条目最大条目数(系统限制小于5000，否则异常) |

## 响应

{:.prettyprint}
    [
        {
            dm:eventAction: 'order',
            dm:eventCategory: 'click',
            dm:eventLabel: 'b2c',
            mt:totalEvents: 100,
            mt:uniqueEvents: 100,
            totalValue: 1000,
        },
        ...
    ]


| 字段            | 说明       |
|-----------------|------------|
| mt:totalEvents  | 事件总数   |
| mt:uniqueEvents | 唯一事件数 |
| mt:eventValue   | 事件总值   |
