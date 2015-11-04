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

    GET http://m.trackmaster.com.cn/api_v2/networks/:networkId/campaigns

**参数**

* `startIndex` 数据从第几条开始，默认为 0
* `maxResults` 最多返回多少条结果，默认为 10，最大为 5000

返回头部信息 X-Content-Record-Total 值为结果条目总数，如果需要控制翻页，请修改`startIndex` 和 `maxResults` 的值。

**响应**

{:.prettyprint}
    [{
        "id": 999,
        "name": "这个是项目名称",
        "advertiserId": 999, // 关联广告主id
        "brandId": 999, // 关联品牌id
        "networkId": 999, // 关联工作网络id
        "trackType": 'mobile','nonmobile' //track类型，移动，非移动，二选一
        "startDate": 2014-06-25, // 项目开始日期
        "endDate": 2014-06-25, //项目结束日期
        "mediaIds":440,1118,40 // 项目下媒体的列表，多个用逗号隔开, 有顺序
        "status": enabled或者disabled, //默认值为enabled
        "costType": 'cny','usd','none', //媒介计划预算结算货币，none为不录入
        "siteMasterId": 999, //项目关联siteMaster 站点id,多个用逗号隔开
        "defaultTarget": "www.ui168.com", //项目默认点击跳转地址
        "isDelete":  yes或者no, //是否被删除,
        "party_name":zhaoxiongfei, //项目甲方联系人名称
        "party_email"://项目甲方联系人邮箱
        "placements":999 //项目下目前广告位总数, 每个项目下广告位总数有限制
    }]


## 获取指定项目信息

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:id

**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": "这个是项目名称",
        "advertiserId": 999, // 关联广告主id
        "brandId": 999, // 关联品牌id
        "networkId": 999, // 关联工作网络id
        "trackType": 'mobile','nonmobile' //track类型，移动，非移动，二选一
        "startDate": 2014-06-25, // 项目开始日期
        "endDate": 2014-06-25, //项目结束日期
        "mediaIds":440,1118,40 // 项目下媒体的列表，多个用逗号隔开, 有顺序
        "status": enabled或者disabled, //默认值为enabled
        "costType": 'cny','usd','none', //媒介计划预算结算货币，none为不录入
        "siteMasterId": 999, //项目关联siteMaster 站点id,多个用逗号隔开
        "defaultTarget": "www.ui168.com", //项目默认点击跳转地址
        "isDelete":  yes或者no, //是否被删除,
        "party_name":zhaoxiongfei, //项目甲方联系人名称
        "party_email"://项目甲方联系人邮箱
        "placements":999 //项目下目前广告位总数, 每个项目下广告位总数有限制
    }

## 添加项目

    POST http://m.trackmaster.com.cn/api_v2/networks/:networkId/campaigns

注意：同广告主下项目名称不允许重名

**参数**

{:.prettyprint}   
    {
        "name": "这个是项目名称", //必填，项目名称
        "advertiserId": 999, // 必填，关联广告主id
        "brandId": 999, // 必填，关联品牌id
        "industryId": 999, // 选填，关联行业id
        "networkId": 999, // 必填，关联工作网络id
        "trackType": 'mobile','nonmobile', //track类型，移动，非移动，二选一
        "startDate": 2014-06-25, // 必填，项目开始日期
        "endDate": 2014-06-25, // 必填，项目结束日期
        "mediaIds":440,1118,40 // 选填，项目下媒体的列表，多个用逗号隔开, 有顺序
        "costType": 'cny','usd','none', //选填，媒介计划预算结算货币，none为不录入
        "siteMasterId": 999, //选填，项目关联siteMaster 站点id,多个用逗号隔开
        "defaultTarget": "www.ui168.com", //必填，项目默认点击跳转地址
        "party_name":zhaoxiongfei, //选填，项目甲方联系人名称
        "party_email"://选填，项目甲方联系人邮箱
    }

	


**响应**


{:.prettyprint}
    {
        "id": 999,
        "name": "这个是项目名称",
        "advertiserId": 999, // 关联广告主id
        "brandId": 999, // 关联品牌id
        "networkId": 999, // 关联工作网络id
        "trackType": 'mobile','nonmobile' //track类型，移动，非移动，二选一
        "startDate": 2014-06-25, // 项目开始日期
        "endDate": 2014-06-25, //项目结束日期
        "mediaIds":440,1118,40 // 项目下媒体的列表，多个用逗号隔开, 有顺序
        "status": enabled或者disabled, //默认值为enabled
        "costType": 'cny','usd','none', //媒介计划预算结算货币，none为不录入
        "siteMasterId": 999, //项目关联siteMaster 站点id,多个用逗号隔开
        "defaultTarget": "www.ui168.com", //项目默认点击跳转地址
        "isDelete":  yes或者no, //是否被删除,
        "party_name":zhaoxiongfei, //项目甲方联系人名称
        "party_email"://项目甲方联系人邮箱
        "placements":999 //项目下目前广告位总数, 每个项目下广告位总数有限制
    }

## 修改指定项目属性

    PATCH http://m.trackmaster.com.cn/api_v2/campaigns/:id

注意：修改项目属性时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。

**参数**

{:.prettyprint}
    {
        "name": "这个是项目名称",
        "agencyId": 999, // 关联代理id
        "brandId": 999, // 关联品牌id
        "industryId": 999, //
        "startDate": 2014-06-25, // 项目开始日期
        "endDate": 2014-06-25, //项目结束日期
        "mediaIds":440,1118,40 // 项目下媒体的列表，多个用逗号隔开, 有顺序
        "status": enabled或者disabled, //默认值为enabled
        "costType": 'cny','usd','none', //媒介计划预算结算货币，none为不录入
        "siteMasterId": 999, //项目关联siteMaster 站点id,多个用逗号隔开
        "defaultTarget": "www.ui168.com", //项目默认点击跳转地址
        "party_name":zhaoxiongfei, //项目甲方联系人名称
        "party_email"://项目甲方联系人邮箱
    }
    
    
**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": "这个是项目名称",
        "advertiserId": 999, // 关联广告主id
        "brandId": 999, // 关联品牌id
        "networkId": 999, // 关联工作网络id
        "trackType": 'mobile','nonmobile' //track类型，移动，非移动，二选一
        "startDate": 2014-06-25, // 项目开始日期
        "endDate": 2014-06-25, //项目结束日期
        "mediaIds":440,1118,40 // 项目下媒体的列表，多个用逗号隔开, 有顺序
        "status": enabled或者disabled, //默认值为enabled
        "costType": 'cny','usd','none', //媒介计划预算结算货币，none为不录入
        "siteMasterId": 999, //项目关联siteMaster 站点id,多个用逗号隔开
        "defaultTarget": "www.ui168.com", //项目默认点击跳转地址
        "isDelete":  yes或者no, //是否被删除,
        "party_name":zhaoxiongfei, //项目甲方联系人名称
        "party_email"://项目甲方联系人邮箱
        "placements":999 //项目下目前广告位总数, 每个项目下广告位总数有限制
    }