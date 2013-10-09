---
weight: 6
layout: default
category: sitemaster
subcategory: site_admin
language: cn
title: 站点目标设置
---

# 站点目标

* TOC
{:toc}

## 获取指定站点的目标

    GET /sites/:site_id/goals

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/123456/goals?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites/123456/goals?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
			"id":"1",           // 目标 ID,值为 1-10
			"name":"",          // 设定的目标名称
			"type":"",          // 类型
			"status":"disabled",// 是否开启
			"condition":"",     // 条件
			"createdAt":"",     // 创建时间
			"updatedAt":""      // 最近修改时间
      }
      ...
    ]


## 获取指定站点下某个目标信息

    GET /sites/:site_id/goals/:goals_id

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/123456/goals/1>; rel="next",
          <http://{{site.site_api_host}}/sites/123456/goals/1>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
			"id":"1",           // 目标 ID,值为 1-10
			"name":"",          // 设定的目标名称
			"type":"",          // 类型
			"status":"disabled",// 是否开启
			"condition":"",     // 条件
			"createdAt":"",     // 创建时间
			"updatedAt":""      // 最近修改时间
      }


## 修改指定目标

敬请期待。