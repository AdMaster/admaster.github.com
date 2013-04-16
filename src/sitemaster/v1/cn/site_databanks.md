---
weight: 5
layout: default
category: sitemaster
subcategory: site_databank
language: cn
title: 获取任务列表
---

# 获取任务列表

* TOC
{:toc}

## 接口

    POST /sites/:site_id/databank/visit

### 请求参数

### 请求参数
无


### 响应

    Status: 201 Created
    Location: http://{{site.site_api_host}}/databank/:id
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: "xxxxx", //数据银行查询id
        url: "http://{{site.site_api_host}}/databank/:id",//资源地址
        status: "ready",
        name: "测试名称", //测试名称
        dimensions: "dm:date,dm:province",//维度
        metrics: "mt:visits,mt:pageviews",//指标
        filters: "dm:date>=2012-09-12;dm:date<=2012-12-12",//过滤条件
        segment: "dm:eventCategory==tag1",//访问细查
        sort: "-mt:pageviews",//排序        
    }
