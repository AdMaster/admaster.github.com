---
weight: 14
layout: default
category: trackmaster
language: cn
title: 媒体
version: v2
---


# 媒体对接指南

* TOC
{:toc}


TrackMaster™ 所有API的访问都是通过 HTTP 执行的，所有被发送和接收的数据都是 JSON。

TrackMaster™ 使用 OAuth2.0 对用户进行验证，保障用户的隐私和安全性。

请在开发前先阅读 [快速入门](http://dev.admaster.com.cn/doc/openmaster/v1/cn/get_started.html)、[OAuth 认证](http://dev.admaster.com.cn/doc/openmaster/v1/cn/oauth.html)、[协议及请求方式](http://dev.admaster.com.cn/doc/openmaster/v1/cn/verbs.html)、[接口定义-通用说明](http://dev.admaster.com.cn/doc/openmaster/v1/cn/common.html)。


## 第一步 获取访问令牌

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


## 第二步 获取媒体项目列表

    GET http://m.trackmaster.com.cn/api_v2/medias/:mediaId/campaigns

**参数**

第一步中获取到的`access_token`

    access_token=***

**响应**

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


## 第三步 获取项目媒体报告

    GET http://m.trackmaster.com.cn/api_v2/medias/:mediaId/campaigns/:campaignId/reports/basics

**参数**

`media_id`   
: _必选_ **Integer** - TrackMaster 分配的媒体 ID

`campaign_id`    
: _必选_ **Integer** - 项目 ID

`access_token=***`     

`start_time`    
: _可选_ **Date** - 项目开始日期，例如2012-08-01，会列出项目开始日期大于等于此设定的项目
    
`end_time`     
: _可选_ **Date** -项目结束日期，例如2012-08-02，会列出项目结束日期小于等于此设定的项目
    
`sort`    
: _可选_ **String** - 列表排序以什么排序

`direction`    
: _可选_ **String** - 排序方式


**响应**

    Status: 200 OK

{:.prettyprint}
    [

      {
        "time": "2012-08-01", // 时间
        "imp": 23, //曝光
        "uimp": 20, //独立曝光
        "clk": 20, //点击
        "uclk": 10, //独立点击
      }
    ]



**详情参见**

[媒体报告](/doc/trackmaster/v1/cn/media_report.html)   
[协议及请求说明](/doc/openmaster/v1/cn/verbs.html)

