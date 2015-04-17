---
weight: 2
layout: default
category: trackmaster
subcategory: agency
language: en
title: Advertiser
version: v2
---

# Advertiser

* TOC
{:toc}

## List advertisers##

    GET http://lib.admasterapi.com/api_v1/advertisers


**Response**

{:.prettyprint}
    [
    {
        id: 10032,
        name_cn: "伊利",
    }
    ]


## Advertiser details

    GET http://lib.admasterapi.com/api_v1/advertisers/:id

**Response**

{:.prettyprint}
    {
        id: 10032,
        name_cn: "伊利",
    }


