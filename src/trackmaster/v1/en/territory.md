---
weight: 13
layout: default
category: trackmaster
subcategory: agency
language: en
title: Territory
version: v1
---

# Territory #

* TOC
{:toc}


## Get territory details of the given ID

    GET /geos/:id

**Parameters**   
 
`language=en`    
: _Optional_  - English Name

**Response**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


{:.prettyprint}
     [
            {
            "id":1
            "name":China
            }
        ]

