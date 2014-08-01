---
weight: 6
layout: default
category: sitemaster
subcategory: site_databank
language: cn
title: 数据银行事件分析
version: v1
---

# 数据银行事件分析

* TOC
{:toc}


## 可用维度和指标

维度

| 维度                      | 说明                                     |
|---------------------------|------------------------------------------|
| dm:language               | 语言                                     |
| dm:continent              | 大州                                     |
| dm:continent              | 大洲                                     |
| dm:country                | 国家                                     |
| dm:province               | 省份                                     |
| dm:city                   | 城市                                     |
| dm:latitude               | 纬度                                     |
| dm:longitude              | 经度                                     |
| dm:landingPagePath        | 登陆路径                                 |
| dm:exitPagePath           | 退出页路径                               |
| dm:pageDepth              | 浏览页数                                 |
| dm:visitorType            | 访问类型：`new` or `return`              |
| dm:visitCount             | 第几次访问                               |
| dm:daysSinceLastVisit     | 距上次访问天数                           |
| dm:referralPath           | 访次来源路径                             |
| dm:sourceType             | 来源类型（推广、社交、搜索、引荐、直接） |
| dm:campaign               | 项目                                     |
| dm:medium                 | 媒体                                     |
| dm:placement              | 广告位                                   |
| dm:creative               | 创意                                     |
| dm:keyword                | 关键字                                   |
| dm:cookieSourceType       | 引导类型，点击引导或曝光引导             |
| dm:cookieCampaign         | 项目                                     |
| dm:cookieMedium           | 媒体                                     |
| dm:cookiePlacement        | 广告位                                   |
| dm:cookieCreative         | 创意                                     |
| dm:cookieKeyword          | 关键字（目前为空，暂留）                 |
| dm:browser                | 浏览器                                   |
| dm:browserVersion         | 浏览器版本                               |
| dm:operatingSystem        | 操作系统                                 |
| dm:operatingSystemVersion | 操作系统版本                             |
| dm:flashVersion           | Flash版本                                |
| dm:javaEnabled            | Java支持与否 `yes` or `no`               |
| dm:screenColors           | 屏幕颜色                                 |
| dm:screenResolution       | 屏幕分辨率                               |
| dm:isMobile               | 是否移动设备 `yes` or `no`               |
| dm:mobileDeviceBranding   | 移动设备品牌                             |
| dm:mobileDeviceModel      | 移动设备型号                             |
| dm:mobileDeviceInfo       | 品牌 + 型号                              |
| dm:mobileInputSelector    | 是否触屏                                 |
| dm:date                   | 日期                                     |
| dm:month                  | 月份                                     |
| dm:week                   | 周                                       |
| dm:dayOfWeek              | 周几                                     |
| dm:hour                   | 小时                                     |
| dm:host                   | 主机名                                   |
| dm:pagePath               | 路径                                     |
| dm:pageTitle              | 页面标题                                 |
| dm:eventCategory          | 事件类别                                 |
| dm:eventAction            | 事件动作                                 |
| dm:eventLabel             | 事件标签                                 |


指标:

| 维度             | 说明         |
|------------------|--------------|
| mt:totalEvents   | 时间总数     |
| mt:uniqueEvents  | 唯一事件数   |
| mt:visitors      | 触发事件人数 |
| mt:eventValue    | 事件总价值   |
| mt:avgEventValue | 事件平均价值 |

## 接口

    POST /sites/:site_id/databank/event

### 请求参数


| 参数名      | 使用说明                                                     |
|-------------|--------------------------------------------------------------|
| start-date  |必选 格式例如：2013-04-02|
| end-date    |必选 格式例如：2013-04-16|
| filters     | 可使用维度和指标任意组合做为查询条件                         |
| segment     | 高级细分, 可根据页面和事件的维度作为查询条件来筛选访问                 |
| dimensions  | 维度，多个用逗号隔开，最多支持3个维度                        |
| metrics     | 指标，多个用逗号隔开                                         |
| sort        | 指定排序字段，可使用任意指标为排序字段，默认为自然排序       |
| start-index | 可选 integer -数据开始条目序号                               |
| max-results | 可选 integer -数据条目最大条目数(系统限制小于5000，否则异常) |

### 响应

    Status: 201 Created
    Location: http://{{site.site_api_host}}/databank/:id
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: "xxxxx", //数据银行查询id
        url: "http://{{site.site_api_host}}/databank/:id",//资源地址
        name: "测试名称", //测试名称
        dimensions: "dm:date,dm:province",//维度
        metrics: "mt:visits,mt:pageviews",//指标
        filters: "isMobile==yes",//过滤条件
        segment: "dm:eventCategory==tag1",//高级细分
        sort: "-mt:pageviews",//排序
        created_at: "2012-08-08 10:54:21"//站点添加时间
        start-date:"2012-08-07",//查询起始时间
        end-date:"2012-08-07"//查询终止时间
    }
