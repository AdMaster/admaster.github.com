---
weight: 9
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 广告位
---

#广告位

* TOC
{:toc}

## 获取指定项目下的广告位列表

    GET /networks/advertisers/campaigns/:campaign_id/placements

**参数**

`name`
: _可选_ **string** - 广告位名称，支持模糊搜索

`network_media_id`
: _可选_ **integer** - 工作网络媒体 ID

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      [{
        //广告位 ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1",
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
        //物料的显示尺寸，单位像素。格式如 400x300 宽度为400px 高度为300px。如果物料类型选择为`textlink`，请填写物料尺寸为1x1
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B KB MB。如果物料类型选择为`textlink`，请填写物料文件大小单位为`B`。
        "material_size_unit": "KB"
      }]


## 获取指定广告位信息

    GET /networks/advertisers/campaigns/placements/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //广告位 ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1",
        //广告位位置名称
        "name": "测试广告位",
        //工作网络下媒体 ID
        "network_media_id": 1314,
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
        //物料的显示尺寸，单位像素格式:400x300,宽度为 400px 高度为 300px
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B KB MB
        "material_size_unit": "KB",
        //note 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，依次类推
        "rotation" : "1/4",
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
        "created_at": "2012-09-06T20:39:23Z"
     }

## 添加一个广告位在指定项目下

    POST /networks/advertisers/campaigns/:campaign_id/placements

注意：同一个项目下广告位数目限制为 400 个

**参数**

`name`
: _必选_ **string** - 广告位位置名称，字符串，长度为 3 - 100个字符

`network_media_id`
: _必选_ **string** - 广告位所属工作网络媒体 ID

`page_url`
: _必选_ **string** - 广告所在位置 URL，例"http://www.admaster.com.cn/"

`channel_id`
: _可选_ **integer** - 广告位所属媒体频道 ID

`type`
: _可选_ **string** - 广告位所属类型

  * `webpage` 网页 _默认值_
  * `video` 视频广告
  * `client` 客户端
  * `se` 搜索引擎
  * `email` 邮件
  * `other` 其他

`screen`:
: _可选_ **integer** - 广告位在第几屏幕


`material_type`
: _可选_ **string** - 物料类型 

  * `flash` _默认值_
  * `image`
  * `video`
  * `textlink`
  * `other` 

`material_dimension`
: _可选_ **string** - 物料的显示尺寸，单位像素 格式如 400x300 宽度为 400px 高度为 300px

`material_size`
: _可选_ **integer** -物料文件大小，单位由 material_size_unit 指定 
 
`material_size_unit`  
: _可选_ **string** -物料文件大小单位

  * `B`
  * `KB`_默认值_
  * `MB`    

`rotation`
: _可选_ **string** 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，依次类推，默认: `1/1`

`target_url`
: _可选_ **string** 点击目标地址, 默认为空，继承项目的点击目标地址。请保证此参数的正确性，因为点击监测代码会按照此地址进行跳转。

`payment_type`
: _可选_ **string** - 支付类型

  * `purchase` 购买 _默认值_
  * `offering` 配送
  * `framework` 框架
  * `compensation` 补偿
  * `other` 其他

`cost_type`
: _可选_ **string** - 单位收费类型

  * `day` 天 _默认值_
  * `week` 周
  * `month` 月
  * `cpc` 每次点击成本
  * `cpm` 千人展示成本
  * `cpa` 每次行动成本
  * `article` 文章
  * `kmail` 千封邮件
  * `other` 其他 

`cost_per_unit`
: _可选_ **float** - 单位成本

`est_imp_per_unit`
: _可选_ **integer** - 单位预估曝光数

`est_clk_per_unit`
: _可选_ **integer** - 单位预估点击

`other_requirement`
: _可选_ **string** - 其他要求

**请求**

{:.prettyprint} 
    {
        "name": "测试广告位",
        "network_media_id": 1314,
        "channel_id":1000,
        "channel_name": "首页",
        "type": "webpage",
        "screen": 3,
        "page_url":"http://www.sina.com.cn/"
        "material_type": "flash",
        "material_dimension": "400x300",
        "material_size": 30,
        "material_size_unit": "KB",    
        "rotation" : "1/1",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "没有什么要求",
    }
    
**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/200057486
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

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

## 删除指定的广告位

    DELETE /networks/advertisers/campaigns/placements/:id

注意：当广告位下曾经获取到监测数据时，不能删除该广告位。

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10786/placements
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 修改指定的广告位属性

    PATCH /networks/advertisers/campaigns/placements/:id

**请求**

`name`
: _可选_ **string** - 广告位位置名称，字符串，长度为 3 - 100个字符

`channel_id`
: _可选_ **integer** - 广告位频道 ID

`type`
: _可选_ **string** - 广告位所属类型

  * `webpage` 网页 _默认值_
  * `video` 视频广告
  * `client` 客户端
  * `se` 搜索引擎
  * `email` 邮件
  * `other` 其他

`screen`:
: _可选_ **integer** - 广告位在第几屏幕

`page_url`
: _可选_ **string** - 广告位所在位置 URL，例"http://www.admaster.com.cn/"

`material_type`
: _可选_ **string** - 物料类型 

  * `flash` _默认值_
  * `image`
  * `video`
  * `textlink`
  * `other` 

`material_dimension`
: _可选_ **string** - 物料的显示尺寸，单位像素 格式如 400x300 宽度为 400px 高度为 300px

`material_size`
: _可选_ **integer** -物料文件大小，单位由 material_size_unit 指定 
 
`material_size_unit`  
: _可选_ **string** -物料文件大小单位

  * `B`
  * `KB`_默认值_
  * `MB`    

`rotation`
: _可选_ **string** 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推，默认: `1/1`

`target_url`
: _可选_ **string** 点击目标地址, 默认为空，继承项目的点击目标地址

`payment_type`
: _可选_ **string** - 支付类型

  * `purchase` 购买 _默认_
  * `offering` 配送
  * `framework` 框架
  * `compensation` 补偿
  * `other` 其他 

`cost_type`
: _可选_ **string** - 单位收费类型 

  * `day` 天 _默认_
  * `week` 周
  * `month` 月
  * `cpc` 每次点击成本
  * `cpm` 千人展示成本
  * `cpa` 每次行动成本
  * `article` 文章
  * `kmail` 千封邮件
  * `other` 其他 

`cost_per_unit`
: _可选_ **float** - 单位成本

`est_imp_per_unit`
: _可选_ **integer** - 单位预估曝光数

`est_clk_per_unit`
: _可选_ **integer** - 单位预估点击

`other_requirement`
: _可选_ **string** - 其他要求

**请求**

{:.prettyprint}
    {
        "name": "测试广告位",
        "network_media_id": 1314,
        "channel_id":1000,
        "channel_name": "首页",
        "type": "webpage",
        "screen": 3,
        "page_url":"http://www.sina.com.cn/"
        "material_type": "flash",
        "material_dimension": "400x300",
        "material_size": 30,
        "material_size_unit": "KB",    
        "rotation" : "1/1",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "没有什么要求",
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
