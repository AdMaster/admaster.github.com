---
weight: 6
layout: default
category: sitemaster
subcategory: site_report
language: cn
title: 广告维度统计数据
version: v1
---

# 广告维度统计数据

* TOC
{:toc}

## 可用维度和指标

维度

| 维度                | 说明                                    |
|---------------------|-----------------------------------------|
| dm:campaign         | 项目                                    |
| dm:medium           | 媒体                                    |
| dm:placement        | 广告位                                  |

指标: [常规指标](/doc/sitemaster/v1/cn/site_report.html#section-2)

除常规指标以外，广告维度数据会返回 `目标` 相关的数据，以 mt:goal\_(n)\_completions、 mt:goal\_(1)\_visits 的名称返回（n 为 1 - 10）。

mt:goal\_(n)\_completions 为指定目标的完成次数，mt:goal\_(1)\_visits 为指定目标完成的访问数。

目标需要再 SiteMaster 的后台进行设定，可以为完成指定事件和到达指定页面两种类型，具体设置请参照 SiteMaster 的帮助中心。

## 资源地址

    GET /sites/:site_id/reports/ad

### 参数


| 参数名      | 使用说明                                                     |
|-------------|--------------------------------------------------------------|
|start-date   |数据时间范围的起始时间 start-date=2013-09-03|
|end-date     |数据时间范围的结束时间 end-date=2013-09-09|
| dimensions  | 维度，多个用逗号开个，最多支持3个维度                        |
| filters     | 可使用维度和指标任意组合做为查询条件                         |
| sort        | 指定排序字段，可使用任意指标为排序字段，默认为自然排序       |
| start-index | 可选 integer -数据开始条目序号                               |
| max-results | 可选 integer -数据条目最大条目数(系统限制小于5000，否则异常) |

### 响应

{:.prettyprint}
    [
        {
            dm:placement: 'ad3',//广告位
            dm:creative: 'intel',//创意
            mt:visits: 100, // 访问次数
            mt:pageviews: 100,//浏览量
            mt:newVisits: 100,//新访问次数
            mt:bounces: 100,//跳出次数
            mt:uniquePageViews: 100,//唯一身份浏览量
            mt:visitDuration: 100,//访问持续时间
            mt:pageLoadTime: 100,//页面加载时间
            mt:pageLoadSample: 100,//页面加载时间样本
            mt:dailyVisitors  //天独立 UV
            mt:goal_1_completions: "12" //目标 1 的完成次数
            mt:goal_1_visits: "10"      //目标 1 的完成的访问数
            mt:goal_2_completions: "120" //目标 2 的完成次数
            mt:goal_2_visits: "112"      //目标 2 的完成的访问数
            mt:goal_3_completions: "0" //目标 3 的完成次数
            mt:goal_3_visits: "0"      //目标 3 的完成的访问数
            ...
        },
        ...
    ]
