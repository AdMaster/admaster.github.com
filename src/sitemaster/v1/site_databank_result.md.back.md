---
weight: 6
layout: default
category: sitemaster
subcategory: site_databank
language: cn
### title: 数据银行分析结果查看
version: v1
---

# 数据银行分析结果查看

* TOC
{:toc}


## 接口

    GET /databank/:id

### 响应

    Status: 200
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        id: "xxxxx", //数据银行查询id
        url: "http://{{site.site_api_host}}/site/xxxxx/databank/:id",//资源地址
        name: "测试名称", //测试名称
        status: "doing",//当前状态 `ready`, `doing`, `error`, `done`
        dimensions: "dm:date,dm:province",//维度
        metrics: "mt:visits,mt:pageviews",//指标
        filters: "dm:date>=2012-09-12;dm:date<=2012-12-12",//过滤条件
        segment: "dm:eventCategory==tag1",//访问细查
        sort: "-mt:pageviews",//排序
        created_at: "2012-08-08 10:54:21"//站点添加时间
    }

# 数据银行结果下载

## 接口

    GET /databank/:id/file

### 响应

    Status: 200
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
