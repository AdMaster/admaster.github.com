---
weight: 4
layout: default
category: trackmaster
subcategory: agency
language: en
title: brand
version: v2
---

# Brand #

* TOC
{:toc}


## List brands

    GET http://m.trackmaster.com.cn/api_v2/networks/:networkId/brands

**Paremeters**

`advertiserId`
: _Optional_ Advertiser ID



**Response**

{:.prettyprint}
    [{
        "id": 999, //Brand ID
        "name":"Test", // Brand Name
        "networkId": 999, //Network ID
        "advertiserId": 999, //Advertiser ID
        "isDelete": "no", //`yes`,`no`
    }]


## Brand details

    GET http://m.trackmaster.com.cn/api_v2/brands/:id

**Response**

{:.prettyprint}
    {
        "id": 999,
        "name":"Test", // Brand Name
        "networkId": 999, //Network ID
        "advertiserId": 999, //Advertiser ID
        "isDelete":"no", //`yes`,`no`
    }

## Add a brand

    POST http://m.trackmaster.com.cn/api_v2/networks/:networkId/brands

**Paremeters**

`name`
: _Required_ Brand Name

`advertiserId`
: _Required_ Advertiser ID


**Request**

    {
        "name": "Test", //Brand Name 
        "advertiserId": 999 //Advertiser ID
    }

**Response**

{:.prettyprint}
    {
        "name":"Test", // Brand Name
        "networkId": 999, //Network ID
        "advertiserId": 999, //Advertiser ID
        "isDelete":"no" //`yes`,`no`
    }


## Update a brand

    PATCH http://m.trackmaster.com.cn/api_v2/brands/:id
    
Note: Only submitted paremeters will be updated.

**Paremeters**

`name`
: _Required_ **string** Brand Name


**Request**

{:.prettyprint}
    {
        "name":"Test", //Brand Name 
        "advertiserId": 999, //Brand ID
        "isDelete":"no"//`yes`,`no` 
    }


**Response**

{:.prettyprint}
    {
        "id": 999,//Brand ID
        "name":"Test", // Brand Name
        "networkId": 999, //Network ID
        "advertiserId": 999, //Advertiser ID
        "isDelete":"no", //`yes`,`no`
    }


## Delete a brand

    DELETE http://m.trackmaster.com.cn/api_v2/brands/:id

Note: It will be failed when the brand has conntected with a campaign.

**Response**

{:.prettyprint}
    Status: 204 OK

