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

**响应**

{:.prettyprint}
    [
        {
        "id": 999,
        "name": //"这个是广告位的名称",
        "mediaId": 999, //"关联系统媒体id",
        "campaignId": 999, //"关联项目id",
        "channelName": //频道名称
        "trackType": 'mobile','nonmobile','mixed', // track类型，移动，非移动，混合，三选一
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "targetGeos":999, //地域定向投放geoIds,多个用逗号隔开
        "targetAudiences"://目标受众定向，json存放      {        "age": [15, 18], // 年龄范围        "gender": ["male", "female"] // 性别白名单      }
        "targetWords"://内容定向投放的关键词, 每行一个
        "freqCtl"://控频设置，json格式      {        "by": "whole", // 控频方式 whole, day, week, month        "range": [0, 10] // 控频范围      }
        "pasterPosition":'unset','before','middle','after', //视频贴片位置，只有type=video时才有值
        "position":'left-top','center-top','right-top','left-middle','center-middle','right-middle','left-bottom','center-bottom','right-bottom','unset', //广告位所在页面位置
        "isDynamic":tinyint(1)默认值为0 //是否是动态广告
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
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
        "trackType": 'mobile','nonmobile','mixed', // track类型，移动，非移动，混合，三选一
        "targetUrl":sdf.com, //广告位点击跳转地址
        "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
        "targetGeos":999, //地域定向投放geoIds,多个用逗号隔开
        "targetAudiences"://目标受众定向，json存放      {        "age": [15, 18], // 年龄范围        "gender": ["male", "female"] // 性别白名单      }
        "targetWords"://内容定向投放的关键词, 每行一个
        "freqCtl"://控频设置，json格式      {        "by": "whole", // 控频方式 whole, day, week, month        "range": [0, 10] // 控频范围      }
        "pasterPosition":'unset','before','middle','after', //视频贴片位置，只有type=video时才有值
        "position":'left-top','center-top','right-top','left-middle','center-middle','right-middle','left-bottom','center-bottom','right-bottom','unset', //广告位所在页面位置
        "isDynamic":tinyint(1)默认值为0 //是否是动态广告
        "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
        "size":0x0 , //广告位尺寸，长x宽 单位像素
        "screen":1, //广告位在第几屏
        "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
        "estimateImp":999, //单位预估曝光
        "estimateClk":999, //单位预估点击
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
        }

## 在指定项目下添加一个广告位

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/placements

注意：同一个项目下广告位数目限制为 400 个

**参数**

{:.prettyprint} 
    {
    "name": //"这个是广告位的名称", //必填
    "mediaId": 999, //"关联系统媒体id",//必填，一旦设置，无法修改
    "campaignId": 999, // 必填，关联项目id
    "channelName": //选填，频道名称
    "targetUrl":sdf.com, //选填，广告位点击跳转地址
    "rollRate": 1, //选填，轮转播放率, 1 为固定，2为 1/2轮播，以此类推
    "targetGeos":999, //选填，地域定向投放geoIds,多个用逗号隔开
    "targetAudiences"://选填，目标受众定向，json存放      {        "age": [15, 18], // 年龄范围        "gender": ["male", "female"] // 性别白名单      }
    "targetWords"://选填，内容定向投放的关键词, 每行一个
    "freqCtl"://选填，控频设置，json格式      {        "by": "whole", // 控频方式 whole, day, week, month        "range": [0, 10] // 控频范围      }
    "pasterPosition":'unset','before','middle','after', //选填，视频贴片位置，只有type=video时才有值
    "position":'left-top','center-top','right-top','left-middle','center-middle','right-middle','left-bottom','center-bottom','right-bottom','unset', //选填，广告位所在页面位置
    "isDynamic":tinyint(1)默认值为0 //选填，是否是动态广告
    "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
    "size":0x0 , //选填，广告位尺寸，长x宽 单位像素
    "screen":1, //选填，广告位在第几屏
    "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //选填，购买类型
    "estimateImp":999, //选填，单位预估曝光
    "estimateClk":999 //选填，单位预估点击
    }
    
**响应**

{:.prettyprint}
    {
        "id": 200057486,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/200057486",
        "campaign_id": 10000,
        "name": "测试广告位",
        "network_media_id": 1314,    
        "rotation" : "1/1",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "units": 0,
        "other_requirement": "没有什么要求",
        "est_imp": 0,
        "est_clk": 0,
        "sp_imp": 0,
        "sp_clk" 0,
        "real_imp": 0,
        "real_clk": 0,
        "created_at": "2012-09-06T20:39:23Z",
        "is_online": 0,
        "page_url":"http://www.sina.com.cn/",
        "type": "webpage",
        "channel_id":1000,
        "channel_name": "首页",
        "screen": 3,       
        "material_type": "flash",
        "material_dimension": "400x300",
        "material_size": 30,
        "material_size_unit": "KB",  
    }

## 修改指定的广告位属性

    PATCH http://m.trackmaster.com.cn/api_v2/placements/:id

注意：修改广告位属性时只需 PATCH 提交需要修改的字段部分，不需要修改的字段不需要提交，所以以下参数都是可选的。

**请求**

{:.prettyprint}
    {
    "name": //"这个是广告位的名称",
    "channelName": //频道名称
    "targetUrl":sdf.com, //广告位点击跳转地址
    "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
    "targetGeos":999, //地域定向投放geoIds,多个用逗号隔开
    "targetAudiences"://目标受众定向，json存放      {        "age": [15, 18], // 年龄范围        "gender": ["male", "female"] // 性别白名单      }
    "targetWords"://内容定向投放的关键词, 每行一个
    "freqCtl"://控频设置，json格式      {        "by": "whole", // 控频方式 whole, day, week, month        "range": [0, 10] // 控频范围      }
    "pasterPosition":'unset','before','middle','after', //视频贴片位置，只有type=video时才有值
    "position":'left-top','center-top','right-top','left-middle','center-middle','right-middle','left-bottom','center-bottom','right-bottom','unset', //广告位所在页面位置
    "isDynamic":tinyint(1)默认值为0 //是否是动态广告
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
    "trackType": 'mobile','nonmobile','mixed', // track类型，移动，非移动，混合，三选一
    "targetUrl":sdf.com, //广告位点击跳转地址
    "rollRate": 1, //轮转播放率, 1 为固定，2为 1/2轮播，以此类推
    "targetGeos":999, //地域定向投放geoIds,多个用逗号隔开
    "targetAudiences"://目标受众定向，json存放      {        "age": [15, 18], // 年龄范围        "gender": ["male", "female"] // 性别白名单      }
    "targetWords"://内容定向投放的关键词, 每行一个
    "freqCtl"://控频设置，json格式      {        "by": "whole", // 控频方式 whole, day, week, month        "range": [0, 10] // 控频范围      }
    "pasterPosition":'unset','before','middle','after', //视频贴片位置，只有type=video时才有值
    "position":'left-top','center-top','right-top','left-middle','center-middle','right-middle','left-bottom','center-bottom','right-bottom','unset', //广告位所在页面位置
    "isDynamic":tinyint(1)默认值为0 //是否是动态广告
    "materialType":'flash','image','video','txt','other', //默认值为image//物料类型
    "size":0x0 , //广告位尺寸，长x宽 单位像素
    "screen":1, //广告位在第几屏
    "costType":'day','week','month','cpc','cpm','cpa','article','edm','other', //默认值为day //购买类型
    "estimateImp":999, //单位预估曝光
    "estimateClk":999, //单位预估点击
    "createdAt": "2012-01-10T02:30:59Z",
    "updatedAt": "2012-01-10T02:30:59Z"
    }
    
## 删除指定的广告位

    DELETE http://m.trackmaster.com.cn/api_v2/placements/:id

注意：当广告位下曾经获取到监测数据时，不能删除该广告位。

**响应**

    Status: 200 OK

