---
weight: 11
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 代码
---

# 代码

* TOC
{:toc}

## 获取指定广告位下的代码

    GET /networks/advertisers/campaigns/placements/:placement_id/codes

**参数**

无

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
     [ {
        // 创意 ID
        "creative_id": 0,

        // 创意名称
        "creative_name": "默认创意",

        // 点击代码
        "clktag": "http://c.admaster.com.cn/c/a10111,b200050000,c2000,i0,m101,h",

        // 曝光代码
        "imptag_video": "http://v.admaster.com.cn/i/a10111,b200050000,c2000,i0,m202,h",

        // 曝光Flash AS2代码
        "imptag_flash_as2": "if(_root[\"adCnt\"]!=\"ldd\") {\n_root[\"adCnt\"]=\"ldd\";var hstr=\"\",u3rd=\"\";\nloadMovie(\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m202,h\"+escape(hstr)+\",d\"+escape(_url)+\",u\"+escape(u3rd),createEmptyMovieClip(\"MSd\",this.getNextHighestDepth()));\n}",

        // 曝光Flash AS3代码
        "imptag_flash_as3": "if(root[\"adCnt\"]!=\"ldd\") {\nroot[\"adCnt\"]=\"ldd\"; var hstr=\"\",u3rd=\"\";\nvar MSd=new Loader();MSd.load(new URLRequest(\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m202,h\"+escape(hstr)+\",d\"+escape(loaderInfo.loaderURL)+\",u\"+escape(u3rd)));this.addChild(MSd);\n}",

        // 曝光图片代码
        "imptag_img": "<img src=\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m202,h\" width=\"1\" height=\"1\" \/>",

        // 曝光JavaScript代码
        "imptag_js": "<script language=\"javascript\">var actId=10111,sptId=200050000,medId=2000,invId=0,hstr=\"\";<\/script>\n<script language=\"javascript\" src=\"http:\/\/v.admaster.com.cn\/sodv3\/admTracker.js\"><\/script>",

        // 曝光Flash代码
        "imptag_flash": "<object classid=\"clsid:d27cdb6e-ae6d-11cf-96b8-444553540000\" id=\"TrackMasterBeacon\" align=\"middle\" width=\"1\" height=\"1\"><param name=\"movie\" value=\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m204,h\" \/><param name=\"allowScriptAccess\" value=\"always\" \/><param name=\"quality\" value=\"high\" \/>\n<embed src=\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m204,h\" quality=\"high\" swLiveConnect=true id=\"TrackMasterBeacon\" name=\"TrackMasterBeacon\" width=\"1\" height=\"1\" align=\"middle\" allowScriptAccess=\"always\" type=\"application\/x-shockwave-flash\" \/><\/object>"
      },
      {...},
      ...
      {...}]

## 获取指定广告位下的关键字监测代码

	GET /networks/advertisers/campaigns/placements/:placement_id/keywords_codes

**参数**

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认每页 30 条

	返回数据的数目。当不指定`per_page` 时，默认最大返回 30 条数据。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       [{
            //关键字 ID
            "keyword_id":1
            //关键字名称
            "keyword_name": Example
            "codes": [
                {
                    //创意 ID
                    "creative_id": 0,
                    //创意名称
                    "creative_name": "默认创意"，
                    //点击代码
                    "clktag": "http://c.admaster.com.cn/c/a10111,b200050000,c2000,i0,m101,h,k9"
                }
            ]
        },
        {...},
        ...
        {...}]

## 获取指定项目下的监测代码

	GET /networks/advertisers/campaigns/:campaign_id/placements/codes

如广告位下有关键字，请调用“获取指定广告位下的关键字监测代码”接口获取广告位下的关键字监测代码。

**参数**

`page`
: _可选_ **integer** - 显示页码

	默认显示页码为 ‘1’，起始页为 ‘1’ 而不是 ‘0’。`page` 和 `per_page`一起使用，例如当返回的数据超过 30 条时，可以通过设定 `page`显示 30 条之后的数据。

`per_page`
: _可选_ **integer** - 分页数量，默认返回 10 个广告位的监测代码

	返回数据的数目。当不指定`per_page` 时，默认最大返回 10 个广告位的监测代码。`per_page` 和 `page` 一起使用显示一系列数据或者单独使用限制

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       [{
            //广告位 ID
            "placement_id":1
            //广告位名称
            "placement_name": Example
            "codes": [
                {
                    //创意 ID
                    "creative_id": 0,
                    //创意名称
                    "creative_name": "默认创意"，
                    //点击代码
                    "clktag": "http://c.admaster.com.cn/c/a10111,b200050000,c2000,i0,m101,h"
                    ...
                },
				{...},
				...
				{...}
            ]
        },
        {...},
        ...
        {...}]