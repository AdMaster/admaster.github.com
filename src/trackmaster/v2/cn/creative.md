---
weight: 6
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 创意
version: v2
---

# 创意

* TOC
{:toc}

## 获取指定项目所有创意

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/creatives

**响应**

{:.prettyprint}
    [{
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
    }]


## 获取项目下指定创意信息

    GET http://m.trackmaster.com.cn/api_v2/creatives/:id

**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
    }


## 在指定项目下添加创意

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/creatives

最多可以创建创意的数目为 20 个。

**参数**

{:.prettyprint}
    {
        "name": //必填，"创意名称",
        "shortName"://必填，创意短名称，2个字符之内
        "targetUrl"://选填，点击跳转地址
    }

**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
    }


## 修改指定的创意属性

    PATCH http://m.trackmaster.com.cn/api_v2/creatives/:id

注意：修改创意信息时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。

**参数**

{:.prettyprint}
    {
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
    }

**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
    }


## 删除指定的创意

    DELETE http://m.trackmaster.com.cn/api_v2/creatives/:id

删除创意后，创意变为默认创意，注意此时获取的监测代码会发生变化。

**响应**

    Status: 204 OK