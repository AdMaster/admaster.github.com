---
weight: 8
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 频道
---

# 频道

* TOC
{:toc}


## 获取指定媒体频道列表

    GET /medias/:media_id/channels

**参数**

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/channels?page=2>; rel="next",
          <http://{{site.track_api_host}}/channels?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
       {
            //频道ID，全局唯一
            "id": 1025,
            //频道名称
            "name": "体育新闻",
            //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
            "type": "web",
            //广告位在第几屏幕
            "screen": 3,
            //频道地址
            "home": "http://www.admaster.com.cn/",
            //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
            "material_type": 'flash',
            //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
            "material_dimension": "400x300",
            //物料文件大小，单位由 material_size_unit 指定
            "material_size": 200,
            //物料文件大小单位，B K M 默认：`K`
            "material_size_unit": "B"
        }
    ]

## 获取指定频道详细信息

    GET /medias/channels/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //频道ID，全局唯一
        "id": 1025,
        //频道名称
        "name": "体育新闻",
        //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "web",
        //广告位在第几屏幕
        "screen": 3,
        //频道地址
        "home": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": 'flash',
        //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B K M 默认：`K`
        "material_size_unit": "B"
    }



