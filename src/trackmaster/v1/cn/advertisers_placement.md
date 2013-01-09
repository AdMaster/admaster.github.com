---
weight: 9
layout: default
category: trackmaster
subcategory: advertisers
language: cn
title: 广告位
---

#广告位

* TOC
{:toc}

##广告主下广告位列表

    GET /advertisers/campaigns/:campaign_id/placements


**参数**

`advertiser_id`
: _必选_ **integer** - 广告主 ID

`name`
: _可选_ **string** - 广告位名称，支持模糊搜索

`page`
: _可选_ **integer** - 显示页码

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

**响应**

    Status: 200 OK

{:.prettyprint}
    [

      {
        //广告位 ID，全局唯一
        "id": 100000,
        //广告位位置名称
        "name": "测试广告位",
        //频道信息
        "channel": {
            //频道名称
            "name": "体育新闻",
            //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
            "type": "webpage",
            //广告位在第几屏幕
            "screen": 3,
            //频道地址
            "home": "http://www.admaster.com.cn/",
            //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
            "material_type": "flash",
            //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
            "material_dimension": "400x300",
            //物料文件大小，单位由 material_size_unit 指定
            "material_size": 200,
            //物料文件大小单位，B K M
            "material_size_unit": "B"
    },
        //点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
        //广告位所属项目 ID
        "campaign_id":1000
      }
    ]

## 获取指定广告位信息

    GET /advertisers/campaigns/placements/:placements_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
    //广告位ID，全局唯一
    "id": 1000000,
    //广告位位置名称
    "name": "测试广告位",
    //工作网络下媒体ID
    "network_media_id": 1314,
    //频道信息
    "channel": {
        //频道ID，全局唯一
        "id": 1025,
        //频道名称
        "name": "体育新闻",
        //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "webpage",
        //广告位在第几屏幕
        "screen": 3,
        //频道地址
        "home": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": "flash",
        //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B K M
        "material_size_unit": "B"
    },
    	//note 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，依次类推
   		 "rotation" : "1/4",
    	//点击目标地址
   		 "target_url": "http://www.admaster.com.cn/",
    	//支付类型 `purchase` 购买，`offering` 配送，`framework` 框架，`Compensation` 补偿，`other` 其他
   		 "payment_type": "purchase",
    	//单位收费类型 `day` 天，`week` 周，`month` 月，`cpc`，`cpm`，`cpa`，`article` 文章，`kmail` 千封邮件，`other` 其他
   		 "cost_type": "day"
    	//单位成本
   		 "cost_per_unit": 873.12,
    	//单位预估曝光数
   		 "est_imp_per_unit": 239,
    	//单位预估点击
   		 "est_clk_per_unit": 3,
    	//购买量
   		 "units": 58,
    	//其他要求
   		 "other_requirement": "没有什么要求",
    	//预估曝光
   		 "est_imp": 871821,
    	//预估点击
   		 "est_clk": 1231,
    	//预估同期曝光
   		 "sp_imp": 61821,
    	//预估同期点击
   		 "sp_clk": 300,
    	//实际总曝光
   		 "real_imp": 71821,
    	//实际总点击
   		 "real_clk": 400,
    	//创建时间
   		 "created_at": "2012-09-06T20:39:23Z"
    }