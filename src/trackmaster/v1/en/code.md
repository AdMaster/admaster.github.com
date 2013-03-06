---
weight: 10
layout: default
category: trackmaster
subcategory: agency
language: en
title: Code
---

# Code

* TOC
{:toc}

## Get code of the given placement

    GET /networks/advertisers/campaigns/placements/:placement_id/codes

**Parameters**

Null

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
      [{
        // Creative ID
        "creative_id": 0,

        // Creative Name
        "creative_name": "默认创意",

        // Click Code
        "clktag": "http://c.admaster.com.cn/c/a10111,b200050000,c2000,i0,m202,h",

        // Impression Code
        "imptag_video": "http://v.admaster.com.cn/i/a10111,b200050000,c2000,i0,m202,h",

        // Impression Code-Flash AS2
        "imptag_flash_as2": "if(_root[\"adCnt\"]!=\"ldd\") {\n_root[\"adCnt\"]=\"ldd\";var hstr=\"\",u3rd=\"\";\nloadMovie(\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m202,h\"+escape(hstr)+\",d\"+escape(_url)+\",u\"+escape(u3rd),createEmptyMovieClip(\"MSd\",this.getNextHighestDepth()));\n}",

        // Impression Code-Flash AS3
        "imptag_flash_as3": "if(root[\"adCnt\"]!=\"ldd\") {\nroot[\"adCnt\"]=\"ldd\"; var hstr=\"\",u3rd=\"\";\nvar MSd=new Loader();MSd.load(new URLRequest(\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m202,h\"+escape(hstr)+\",d\"+escape(loaderInfo.loaderURL)+\",u\"+escape(u3rd)));this.addChild(MSd);\n}",

        // Impression Code-Img
        "imptag_img": "<img src=\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m202,h\" width=\"1\" height=\"1\" \/>",

        // Impression Code-JavaScript
        "imptag_js": "<script language=\"javascript\">var actId=10111,sptId=200050000,medId=2000,invId=0,hstr=\"\";<\/script>\n<script language=\"javascript\" src=\"http:\/\/v.admaster.com.cn\/sodv3\/admTracker.js\"><\/script>",

        // Impression Code-Flash
        "imptag_flash": "<object classid=\"clsid:d27cdb6e-ae6d-11cf-96b8-444553540000\" id=\"TrackMasterBeacon\" align=\"middle\" width=\"1\" height=\"1\"><param name=\"movie\" value=\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c14,i0,m204,h\" \/><param name=\"allowScriptAccess\" value=\"always\" \/><param name=\"quality\" value=\"high\" \/>\n<embed src=\"http:\/\/v.admaster.com.cn\/i\/a10111,b200050000,c2000,i0,m204,h\" quality=\"high\" swLiveConnect=true id=\"TrackMasterBeacon\" name=\"TrackMasterBeacon\" width=\"1\" height=\"1\" align=\"middle\" allowScriptAccess=\"always\" type=\"application\/x-shockwave-flash\" \/><\/object>"
      },
      {...},
      ...
      {...}]

## Get keywords code of the given placement

	GET /networks/advertisers/campaigns/placements/:placement_id/keywords/codes

**Parameters**

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 30 entries.

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       [{
            //Keyword ID
            "keyword_id":1
            //Keyword Namw
            "keyword_name": Example
            "codes": [
                {
                    //Creative ID
                    "creative_id": 0,
                    //Creative Name
                    "creative_name": "默认创意"，
                    //Click Code
                    "clktag": "http://c.admaster.com.cn/c/a10111,b200050000,c2000,i0,m101,h"
                }
            ]
        },
        {...},
        ...
        {...}]

## Get codes of the given campaign ID

	GET /networks/advertisers/campaigns/:campaign_id/placements/codes

If the placement contians keywords, please call 'Get keywords code of the given placement'.


**Parameters**

`page`
: _Optional_ **integer** - the start index

	If not supplied, the page is 1. (Feed pages are 1-based. That is, the first entry is entry 1, not entry 0.) Use this parameter as a pagination mechanism along with the per_page parameter for situations when totalResults exceeds 30 and you want to retrieve entries indexed at 31 and beyond.

`per_page`
: _Optional_ **integer** - the max-results

	You can use this in combination with page to retrieve a subset of elements, or use it alone to restrict the number of returned elements, starting with the first. If you do not use the per_page parameter in your query, your feed returns the default maximum of 10 placements' codes.

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
       [{
            //Placement ID
            "placement_id":1
            //Placement Name
            "placement_name": Example
            "codes": [
                {
                    //Creative ID
                    "creative_id": 0,
                    //Creative Name
                    "creative_name": "默认创意"，
                    //Click Code
                    "clktag": "http://c.admaster.com.cn/c/a10000,b200000000,c2000,i0,m101,h"
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