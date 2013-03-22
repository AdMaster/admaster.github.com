---
weight: 5
layout: default
category: custom_report
language: cn
title: 自定义报告接口
---

# 自定义报告

* TOC
{:toc}

## 获取指定站点下所有自定义报告

    GET /sites/:site_id/customAnalytics/all

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          id: 245
          name: '这是一自定义报告',
          dimensions: 'dm:date,dm:city',
          metrics: 'mt:visits,mt:visitors,mt:pageviews',
          filters: 'dm:city==北京;mt:visits>1000',
          sort: '-mt:pageviews',
          created_at: "2012-12-12 16:00:08",//添加时间
      }
    ]


## 添加站点自定义报告

    POST /sites/:site_id/customAnalytics

**参数**

`name`
: _必选_ **string** - 自定义报告名称

`metrics`
: _必选_ **string** - 指标，多个用逗号隔开，指标有那些可以参考页面底部指标列表

`dimensions`
: _可选_ **string** - 维度，多个用逗号开个，最多支持3个维度 参考页面底部维度列表

`filters`
: _可选_ **string** - 过滤条件，可以对指标或者维度过滤，具体的过滤规则查看页面底部filter的说明

`segment`
: _可选_ **string** - 高级细分，设置对访次的细分过滤，具体查看页面底部segment的说明


**请求**

{:.prettyprint}
    {
          name: '这是一自定义报告',
          dimensions: 'dm:date,dm:city',
          metrics: 'mt:visits,mt:visitors,mt:pageviews',
          filters: 'dm:city==北京;mt:visits>1000',
          sort: '-mt:pageviews',
    }

**响应**

    Status: 201 Created
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
          id: 245
          name: '这是一自定义报告',
          dimensions: 'dm:date,dm:city',
          metrics: 'mt:visits,mt:visitors,mt:pageviews',
          filters: 'dm:city==北京;mt:visits>1000',
          sort: '-mt:pageviews',
          created_at: "2012-12-12 16:00:08",//添加时间
    }

## 修改站点自定义报告

    PATCH /sites/customAnalytics/:id

**参数**

`name`
: _必选_ **string** - 自定义报告名称

`metrics`
: _必选_ **string** - 指标，多个用逗号隔开，指标有那些可以参考页面底部指标列表

`dimensions`
: _可选_ **string** - 维度，多个用逗号开个，最多支持3个维度 参考页面底部维度列表

`filters`
: _可选_ **string** - 过滤条件，可以对指标或者维度过滤，具体的过滤规则查看页面底部filter的说明

`segment`
: _可选_ **string** - 高级细分，设置对访次的细分过滤，具体查看页面底部segment的说明


**请求**

{:.prettyprint}
    {
          name: '这是一自定义报告',
          dimensions: 'dm:date,dm:city',
          metrics: 'mt:visits,mt:visitors,mt:pageviews',
          filters: 'dm:city==北京;mt:visits>1000',
          sort: '-mt:pageviews',
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
          id: 245
          name: '这是一自定义报告',
          dimensions: 'dm:date,dm:city',
          metrics: 'mt:visits,mt:visitors,mt:pageviews',
          filters: 'dm:city==北京;mt:visits>1000',
          sort: '-mt:pageviews',
          created_at: "2012-12-12 16:00:08",//添加时间
    }

## 删除站点自定义报告

    DELETE /sites/customAnalytics/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
