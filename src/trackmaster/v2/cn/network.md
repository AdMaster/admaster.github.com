---
weight: 1
layout: default
category: trackmaster
subcategory: agency
language: cn
version: v2
title: 工作网络
---

# 工作网络

* TOC
{:toc}

## 获取当前授权用户有权操作的所有工作网络

    GET /users/:userId/networks

**响应**

{:.prettyprint}
    [
      {
        "id": 999, //资源id
        "name":牛逼工作网络, //"这个是工作网络的名称",
        "creator": zhaoxiongfei@admaster.com.cn, //"工作网络创建者的email地址",
        "status": enabled或者disabled,// 默认值为enabled,
        "campaigns": 999, //该工作网络下已有的项目数,
        "campaignLimit":999, //该工作网络下已有可以创建的项目总数,
        "users": 999, //该工作网络下已有的用户数,
        "switchs": {"campaign":true,
                    "user":true,
                    "privilege":true},
        "userLimit": 999, //该工作网络下已有可以添加的用户总数,
        "expiredAt": 2080-09-19 00:00:00 //该工作网络的过期日期，过期后工作网络不可用,
        "isDelete": yes或者no, //是否被删除,
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
      }
    ]

## 获取指定 ID 工作网络信息

    GET /networks/:id

**响应**

{:.prettyprint}
      {
        "id": 999, //资源id
        "name":牛逼工作网络, //"这个是工作网络的名称",
        "creator": zhaoxiongfei@admaster.com.cn, //"工作网络创建者的email地址",
        "status": enabled或者disabled,// 默认值为enabled,
        "campaigns": 999, //该工作网络下已有的项目数,
        "campaignLimit":999, //该工作网络下已有可以创建的项目总数,
        "users": 999, //该工作网络下已有的用户数,
        "switchs": {"campaign":true,
                    "user":true,
                    "privilege":true},
        "userLimit": 999, //该工作网络下已有可以添加的用户总数,
        "expiredAt": 2080-09-19 00:00:00 //该工作网络的过期日期，过期后工作网络不可用,
        "isDelete": yes或者no, //是否被删除,
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
      }
      
## 修改指定 ID 工作网络信息

    PATCH /networks/:id

**请求**

{:.prettyprint}
      {
        "id": 999, //资源id
        "name":牛逼工作网络, //"这个是工作网络的名称",
        "creator": zhaoxiongfei@admaster.com.cn, //"工作网络创建者的email地址",
        "status": enabled或者disabled,// 默认值为enabled,
        "campaigns": 999, //该工作网络下已有的项目数,
        "campaignLimit":999, //该工作网络下已有可以创建的项目总数,
        "users": 999, //该工作网络下已有的用户数,
        "switchs": {"campaign":true,
                    "user":true,
                    "privilege":true},
        "userLimit": 999, //该工作网络下已有可以添加的用户总数,
        "expiredAt": 2080-09-19 00:00:00 //该工作网络的过期日期，过期后工作网络不可用,
        "isDelete": yes或者no, //是否被删除,
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
      }


**响应**

    {:.prettyprint}
      {
        "id": 999, //资源id
        "name":牛逼工作网络, //"这个是工作网络的名称",
        "creator": zhaoxiongfei@admaster.com.cn, //"工作网络创建者的email地址",
        "status": enabled或者disabled,// 默认值为enabled,
        "campaigns": 999, //该工作网络下已有的项目数,
        "campaignLimit":999, //该工作网络下已有可以创建的项目总数,
        "users": 999, //该工作网络下已有的用户数,
        "switchs": {"campaign":true,
                    "user":true,
                    "privilege":true},
        "userLimit": 999, //该工作网络下已有可以添加的用户总数,
        "expiredAt": 2080-09-19 00:00:00 //该工作网络的过期日期，过期后工作网络不可用,
        "isDelete": yes或者no, //是否被删除,
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
      }

  
      
## 删除指定工作网络

    GET /networks/:id

**响应**

    Status: 200 OK

  