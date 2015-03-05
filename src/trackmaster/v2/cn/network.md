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

    GET http://m.trackmaster.com.cn/api_v2/session

**响应**

其中 `networks` key 下为当前用户有权操作的所有工作网络

{:.prettyprint}
    {
        "id": 1, 
        "name": "xxx", 
        "role": "user", 
        "email": "xxx@admaster.com.cn", 
        ... 
        "networks": {
            "11": {
                "id": 72, 
                "networkId": 11, 
                "userId": 1, 
                "roleId": 11, 
                "expiredAt": "2020-11-18T00:00:00.000Z", 
                "status": "enabled", 
                "isOwnAllCampaign": "no", 
                "isDelete": "no", 
                "createdAt": "2014-11-18T08:31:29.000Z", 
                "updatedAt": "2014-12-18T08:52:16.000Z", 
                "network": {
                    ...
                    "id": 11, 
                    "name": "AdMaster", 
                    "creator": "xxx@admaster.com.cn", 
                    "status": "enabled", 
                    "campaigns": 168, 
                    "campaignLimit": 10000, 
                    "users": 88, 
                    "userLimit": 100, 
                    "expiredAt": "2020-11-29T00:00:00.000Z", 
                    "isDelete": "no", 
                    "createdAt": "2014-10-29T02:23:25.000Z", 
                    "updatedAt": "2015-03-05T09:02:45.000Z"
                }, 
                ...
            }, 
            "70": {
                "id": 0, 
                "networkId": 70, 
                "network": {
                    ...
                    "id": 70, 
                    "name": "Name xxx", 
                    "creator": "xxx@admaster.com.cn", 
                    "status": "enabled", 
                    "campaigns": 0, 
                    "campaignLimit": 5000, 
                    "users": 6, 
                    "userLimit": 200, 
                    "expiredAt": "2025-01-01T00:00:00.000Z", 
                    "isDelete": "no", 
                    "createdAt": "2014-08-01T10:15:31.000Z", 
                    "updatedAt": "2015-02-26T04:06:02.000Z"
                }
            }
        }
    }

## 获取指定 ID 工作网络信息

    GET http://m.trackmaster.com.cn/api_v2/networks/:id

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

    PATCH http://m.trackmaster.com.cn/api_v2/networks/:id

注意：修改网络信息时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。

**请求**

{:.prettyprint}
      {
        "name":牛逼工作网络, //"这个是工作网络的名称",
        "status": enabled或者disabled,// 默认值为enabled,
        "campaignLimit":999, //该工作网络下已有可以创建的项目总数,
        "users": 999, //该工作网络下已有的用户数,
        "switchs": {"campaign":true,
                    "user":true,
                    "privilege":true},
        "userLimit": 999, //该工作网络下已有可以添加的用户总数,
        "expiredAt": 2080-09-19 00:00:00 //该工作网络的过期日期，过期后工作网络不可用,
        "isDelete": yes或者no, //是否被删除,
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

    GET http://m.trackmaster.com.cn/api_v2/networks/:id

**响应**

    Status: 200 OK

  