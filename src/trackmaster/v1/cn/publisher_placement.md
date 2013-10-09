---
weight: 10
layout: default
category: trackmaster
subcategory: publisher
language: cn
title: 广告位
---

#广告位

* TOC
{:toc}

## 获取指定媒体的广告位列表

    GET /medias/:media_id/placements

**参数**

`campaign_id`
: _可选_ **integer** - 项目 ID

`name`
: _可选_ **string** - 广告位名称，支持模糊搜索

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/100/placements?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/100/placements?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //广告位 ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/20000006",
        //广告位所属项目 ID
        "campaign_id": 10000,
        //广告位位置名称
        "name": "测试广告位",
        //工作网络下媒体 ID
        "network_media_id": 1314, 
        //note 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，依次类推
        "rotation" : "1/1",
        //点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //支付类型 `purchase` 购买，`offering` 配送，`framework` 框架，`compensation` 补偿，`other` 其他
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
        "created_at": "2012-09-06T20:39:23Z",
        //广告位所属频道 ID
        "channel_id": "1000",
        //广告位所属频道名称
        "channel_name": "首页",
        //广告位类型-`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "webpage",
        //广告位在第几屏幕
        "screen": 3,
        //广告位地址
        "page_url": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": "flash",
        //物料的显示尺寸，单位像素。格式如 400x300 宽度为400px 高度为300px。
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B KB MB。
        "material_size_unit": "KB"
      }
    ]


## 获取指定媒体指定广告位的信息

    GET /medias/placements/:placement_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //广告位 ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/20000006",
        //广告位所属项目 ID
        "campaign_id": 10000,
        //广告位位置名称
        "name": "测试广告位",
        //工作网络下媒体 ID
        "network_media_id": 1314, 
        //note 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，依次类推
        "rotation" : "1/1",
        //点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //支付类型 `purchase` 购买，`offering` 配送，`framework` 框架，`compensation` 补偿，`other` 其他
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
        "created_at": "2012-09-06T20:39:23Z",
        //广告位所属频道 ID
        "channel_id": 1000,
        //广告位所属频道名称
        "channel_name": "首页",
        //广告位类型-`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "webpage",
        //广告位在第几屏幕
        "screen": 3,
        //广告位地址
        "page_url": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": "flash",
        //物料的显示尺寸，单位像素。格式如 400x300 宽度为400px 高度为300px。
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B KB MB。
        "material_size_unit": "KB"
    }
