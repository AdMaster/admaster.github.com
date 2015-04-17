---
weight: 1
layout: default
category: trackmaster
subcategory: agency
language: en
title: code
version: v2
---

# Code

* TOC
{:toc}

## List codes

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:id/codes

**Paremeters**

`placementId`
: _Optional_  Placement ID to filter by.

`placementIds`
: _Optional_  Several placements to filter by. Separator:`,`.

`mediaId`
: _Optional_  Media ID to filter by.

`mediaIds`
: _Optional_  Several media to filter by. Separator:`,`.


**Response**

{:.prettyprint}
    [
        {
            placementId: 50001,// Placement ID
            creativeId: 0,//Creative ID
            mediaId: 1238,//Media ID
            view: "http://v.admaster.com.cn/i/a50014,b50001,c1238,i0,m202,h", // Impression Code
            click: "http://c.admaster.com.cn/c/a50014,b50001,c1238,i0,m101,h" // Click Code
        },
        {
            placementId: 50000,
            creativeId: 0,
            mediaId: 12,
            view: "http://v.admaster.com.cn/i/a5000,b50000,c12,i0,m202,h",
            click: "http://c.admaster.com.cn/c/a5000,b50000,c12,i0,m101,h"
        }
    ]

