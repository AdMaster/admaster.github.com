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
      {
        // Creative ID
        "creative_id": 0,

        // Creative Name
        "creative_name": "默认创意",

        // Click Code
        "clktag": "http://c.admaster.com.cn/c/a10111,b200050000,c2000,i0,m202,h",

        // Impression Code
        "imptag": "http://v.admaster.com.cn/i/a10111,b200050000,c2000,i0,m202,h",

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
      }


