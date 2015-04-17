---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: en
title: media
version: v2
---

# Media

* TOC
{:toc}

## List media

    GET http://lib.admasterapi.com/api_v1/medias


**Response**

{:.prettyprint}
    [{
        id: 440,
        name_cn: "腾讯网",
        status: "normal",
        domain: "qq.com"
    }]
    


## Media details

    GET http://lib.admasterapi.com/api_v1/medias/:id

**Response**

{:.prettyprint}
    {
        id: 440,
        name_cn: "腾讯网",
        status: "normal",
        domain: "qq.com"
    }