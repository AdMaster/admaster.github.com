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

    GET /user/networks

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
       {
        "id": 11,//网络 ID
        "url": "https://{{site.track_api_host}}/networks/11",
        "name": "测试工作网络", //别名
        "created_at": "2012-09-06T20:39:23Z" //创建时间
        "account": {
            "status": "enabled", //`enabled` 可用, `disabled` 禁用, `unactive` 未激活
            "created_at": "2012-01-10T02:30:59Z", //当前用户加入网络的时间
            "role": {
                "id": 1,//角色 ID
                "name": "高级管理员(super admin)"//角色名称
             }
          }
       }
    ]

##第三步 获取指定工作网络下所有广告主属性列表 ##

    GET /networks/:network_id/advertisers

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "advertiser_id": 10933,//广告主 ID
        "url": "http://{{site.track_api_host}}/networks/11/advertisers/10933",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "status": "enabled",//网络下广告主当前状态
        "alias": "腾讯",//广告主别名
        "logo": "http://www.trackmaster.com.cn/data/advIcon/tencent.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
      }
    ]

##第四步 获取指定工作网络下某个广告主有操作权限的项目列表 ##

    GET /networks/:network_id/advertisers/:advertiser_id/campaigns

**参数**

`name`
: _可选_ **string** - 项目名称，支持模糊搜索，例如：名称为 “这是一个测试项目” 搜索 “一个”即可找到该项目

`network_brand_id`
: _可选_ **integer** - 项目所属网络品牌ID

`status`
: _可选_ *Enum* - 项目状态

  * `all` - 所有状态, (_默认_)
  * `typing` - 编辑中，当项目的属性、位置列表、点位等数据任意有值时，状态为编辑中。
  * `testing` - 测试中，当项目的监测代码已生成并已导出，且有数据进来，状态为测试中。
  * `kickoff` - 项目初期，项目上线的第一周为项目初期。
  * `midterm` - 项目中期，项目初期之后到项目结束一周前，为项目中期，小于一周的项目没有项目中期。
  * `teminal` - 项目末期，结束日期的前一周，为项目末期。小于一周的项目没有项目末期；大于一周且小于两周的项目没有项目中期，项目末期为开始日期一周后到结束的时间段。
  * `finished` - 已结束，当前时间在结束时间之后的，为已结束状态。

`start_date`
: _可选_ **date** - 项目开始时间，会列出项目开始日期小于等于此设定的项目。

`end_date`
: _可选_ **date** - 项目结束时间，会列出项目结束日期大于等于此设定的项目。

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照项目 ID 排序
  * `network_brand_id` - 按照品牌 ID 排序
  * `name` - 按照项目名称排序
  * `total_cost` - 按照总成本排序
  * `media_num` - 按照媒体数排序
  * `placement_num` - 按照广告位数排序
  * `start_date` - 按照开始日期排序
  * `end_date` - 按照结束日期排序
  * `est_imp` - 按照总预计曝光排序
  * `est_clk` - 按照总预计点击排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/11/advertisers/10774/campaigns?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/11/advertisers/10774/campaigns?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 10774,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10774",
        "name": "这是一个测试项目",//项目名称
        "network_brand_id": 290,//品牌 ID
        "cost_type": "CNY",
        "total_cost": 20000000,//总成本
        "start_date": "2012-01-03",//项目开始时间
        "end_date": "2012-06-23",//项目结束时间
        "default_target": "http://www.admaster.com.cn"//项目目标链接地址
        "survey_id": 1024,//如果关联了 SurveyMaster，则存在 survey_id。
        "media_num": 8,//项目下媒体数目
        "placement_num": 258,//项目下广告位数目
        "est_imp": 9183213,//项目的总预计曝光
        "est_clk": 12334,//项目的总预计点击
        "status": "kickoff",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间后 7 天内，返回值“yes”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
      }
    ]


# 其它信息 #

[概述](/doc/openmaster/v1/cn/index.html)  
[协议及请求说明](/doc/openmaster/v1/cn/verbs.html)




