---
weight: 3
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 项目
version: v2
---

# 项目

* TOC
{:toc}

## 获取网络下项目列表

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


## 获取指定项目信息

    GET /campaigns/:id

**响应**

{:.prettyprint}
    {
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
    }

## 添加项目

    POST /networks/:networkId/campaigns

注意：同广告主下项目名称不允许重名

**参数**

{:.prettyprint}   
    {
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
    }

	


**响应**

{:.prettyprint}
    {
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "测试项目",//项目名称
        "network_brand_id": 10021,//项目网络品牌 ID
        "cost_type": "USD",//媒体预算货币类型
        "total_cost": 20000,//项目总费用
        "start_date": "2012-01-31",//项目开始日期
        "end_date": "2012-04-20",//项目结束日期
        "default_target": "http://www.admaster.com.cn"
        "media_num": 2,//项目中媒体数目
        "placement_num": 4,//项目中广告位数目
        "target_audience":{//目标受众人群
            "age": "16-30",//目标受众人群年龄范围
            "sex": ["female"]//目标受众人群性别
        },
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
    }

**字段说明**

参见页面底部说明

## 修改指定项目属性

    PATCH /campaigns/:id

**参数**

{:.prettyprint}
    {
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "测试项目",//项目名称
        "network_brand_id": 10021,//项目网络品牌 ID
        "cost_type": "USD",//媒体预算货币类型
        "total_cost": 20000,//项目总费用
        "start_date": "2012-01-31",//项目开始日期
        "end_date": "2012-04-20",//项目结束日期
        "default_target": "http://www.admaster.com.cn"
        "media_num": 2,//项目中媒体数目
        "placement_num": 4,//项目中广告位数目
        "target_audience":{//目标受众人群
            "age": "16-30",//目标受众人群年龄范围
            "sex": ["female"]//目标受众人群性别
        },
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
    }
**响应**

    Status: 200 OK

{:.prettyprint}
    {
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
    }


## 删除指定项目

    DELETE /campaigns/:id

注意：当项目下有广告位时不允许删除项目；如需删除请先删除该项目下的广告位。

**响应**

    Status: 200 OK
