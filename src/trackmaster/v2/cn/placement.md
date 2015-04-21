---
weight: 5
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 广告位
version: v2
---

#广告位

* TOC
{:toc}

## 获取指定项目下的广告位列表

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/placements

**参数**

* `startIndex` 数据从第几条开始，默认为 0
* `maxResults` 最多返回多少条结果，默认为 10，最大为 5000

返回头部信息 X-Content-Record-Total 值为结果条目总数，如果需要控制翻页，请修改`startIndex` 和 `maxResults` 的值。

**响应**

{:.prettyprint}
    [
        {
        "id": 999,
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        }
    ]


## 获取指定广告位信息

    GET http://m.trackmaster.com.cn/api_v2/placements/:id

**响应**

{:.prettyprint}
        {
        "id": 999,
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        }
    
## 在指定项目下添加一个广告位

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/placements

注意：同一个项目下广告位数目限制为 400 个

**参数**

{:.prettyprint}
        {
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        }
    
**响应**

{:.prettyprint}
        {
        "id": 999,
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        }

## 修改指定的广告位属性

    PATCH http://m.trackmaster.com.cn/api_v2/placements/:id

注意：修改广告位属性时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。

**请求**

{:.prettyprint}
        {
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        }

**响应**

{:.prettyprint}
        {
        "id": 999,
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        }
    
## 删除指定的广告位

    DELETE http://m.trackmaster.com.cn/api_v2/placements/:id

注意：当广告位下曾经获取到监测数据时，不能删除该广告位。

**响应**

    Status: 204 OK

