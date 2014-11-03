---
weight: 14
layout: default
category: trackmaster
language: cn
title: 代理
version: v2
---


# 广告代理 #

* TOC
{:toc}

TrackMaster™ 所有 API 的访问都是通过 HTTP 执行的，所有被发送和接收的数据都是 JSON。请在开发前先阅读 [快速入门](http://dev.admaster.com.cn/doc/openmaster/v1/cn/get_started.html)、[OAuth 认证](http://dev.admaster.com.cn/doc/openmaster/v1/cn/oauth.html)、[协议及请求方式](http://dev.admaster.com.cn/doc/openmaster/v1/cn/verbs.html)、[接口定义-通用说明](http://dev.admaster.com.cn/doc/openmaster/v1/cn/common.html)。

TrackMaster™ 使用 OAuth2.0 对用户进行验证，保障用户的隐私和安全性。在您阅读本文进行开发时，您应当已经取得了您的帐号。如果没有，请至 [AdMaster 官网](http://www.admaster.com.cn) 申请帐号。

当您已经拥有 TrackMaster 账号并且刚开始准备进行 API 访问，请先至
[申请应用](http://dev.admaster.com.cn/doc/openmaster/v1/cn/index.html#clientid--client-secret-key) 申请获取 ClientID 与 Client Secret Key。

TrackMaster API 结构与业务逻辑一致，请访问 [帮助中心](http://help.admaster.com.cn/trackmaster/) 获取相关业务知识，您也可以从 [概述](/doc/trackmaster/v1/cn/index.html) 简单了解。



# 开发示例 #

## 第一步 获取访问令牌 ##

    POST http://open.admaster.com.cn/oauth/access_token

**参数**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "password",
      "email": "yourmailaddress@email.com",
      "password": "***"
    }

**响应**

    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "18000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }

`access_token`在`expires_in`秒内有效，超期后请重新访问该接口获取新的访问令牌，携带参数：

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## 第二步 获取当前授权用户有权操作的所有工作网络 ##

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


##第三步 获取指定工作网络下有操作权限的项目列表 ##

    GET /networks/:networkId/campaigns

**响应**

{:.prettyprint}
    [{
    "id": 999,
    "name": "这个是项目名称",
    "advertiserId": 999, // 关联广告主id
    "agencyId": 999, // 关联代理id
    "brandId": 999, // 关联品牌id
    "industryId": 999, //
    "networkId": 999, // 关联工作网络id
    "creatorId": 999, // 创建者id
    "trackType": 'mobile','nonmobile','mixed', //track类型，移动，非移动，混合，三选一
    "startDate": 2014-06-25, // 项目开始日期
    "endDate": 2014-06-25, //项目结束日期
    "mediaIds":440,1118,40 // 项目下媒体的列表，多个用逗号隔开, 有顺序
    "status": enabled或者disabled, //默认值为enabled
    "costType": 'cny','usd','none', //媒介计划预算结算货币，none为不录入
    "siteMasterId": 999, //项目关联siteMaster 站点id,多个用逗号隔开
    "smtbStatus": 'enabled','disabled', //smtb跟踪状态,enabled为开启，disabled 为关闭
    "defaultTarget": "www.ui168.com", //项目默认点击跳转地址
    "isDelete":  yes或者no, //是否被删除,
    "party_name":zhaoxiongfei, //项目甲方联系人名称
    "party_gender":'male','female', //项目甲方联系人性别
    "party_email"://项目甲方联系人邮箱
    "placements":999, //项目下目前广告位总数, 每个项目下广告位总数有限制
    "createdAt": "2012-01-10T02:30:59Z",
    "updatedAt": "2012-01-10T02:30:59Z"
    }]


# 其它信息 #

[概述](/doc/openmaster/v1/cn/index.html)  
[协议及请求说明](/doc/openmaster/v1/cn/verbs.html)




