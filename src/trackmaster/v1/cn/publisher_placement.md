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

`media_id`
: _必选_ **integer** - 系统媒体 ID

`name`
: _可选_ **string** - 广告位名称，支持模糊搜索

`page`
: _可选_ **integer** - 显示页码

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/100/placements?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/100/placements?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //广告位ID，全局唯一
        "id": 1,
        //广告位位置名称
        "name": "这是一个测试广告位",
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


## 获取指定媒体指定广告位的信息

    GET /medias/:media_id/placements/:placement_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
    //广告位ID，全局唯一
    "id": 1,
    //广告位位置名称
    "name": "这是一个测试广告位",
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
