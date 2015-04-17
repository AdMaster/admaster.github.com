---
weight: 8
layout: default
category: trackmaster
subcategory: agency
language: en
title: spot
version: v2
---

# Spot

* TOC
{:toc}

## List spots

    GET http://m.trackmaster.com.cn/api_v2/campaigns/:id/spots

**Response**

{:.prettyprint}
    [{
    "campaignId": 999, // Campaign Id
    "placementId": 999, // Placement ID
    "creativeId": 999, // Creative ID
    "date": "2015-04-22T00:00:00.000Z", // Date
    "num": 888 // Perchase Unites
    }]

## Add a spot

    POST http://m.trackmaster.com.cn/api_v2/campaigns/:campaignId/spots

**Paremeters**

`campaignId`
: _Required_  Campaign ID

`date`
: _Required_   

`placementId`
: _Required_  Placement ID

`creativeId`
: _Required_  Creative ID

`num`
: _Required_  


**Request**

{:.prettyprint}
    {
        campaignId: 50000,//Campaign ID
        date: "2014-07-22T00:00:00.000Z",//Date
        placementId: 1,//Placement ID
        creativeId: 8,//Creative ID
        num: 30
    }

**Response**

{:.prettyprint}
    {
        campaignId: 50000,//Campaign ID
        date: "2014-07-22T00:00:00.000Z",//Date
        placementId: 1,//Placement ID
        creativeId: 8,//Creative ID
        num: 30

       }

## Update a spot

    PATCH http://m.trackmaster.com.cn/api_v2/spots/:id

Note: Only submitted paremeters will be updated.

**Paremeters**

`date`
: _Required_   

`placementId`
: _Required_  Placement ID

`creativeId`
: _Required_  Creative ID

`num`
: _Required_  

**Request**

{:.prettyprint}
    {
        campaignId: 50000,//Campaign ID
        date: "2014-07-22T00:00:00.000Z",//Date
        placementId: 1,//Placement ID
        creativeId: 8,//Creative ID
        num: 30

    }

**Response**

{:.prettyprint}
    {
        campaignId: 50000,//Campaign ID
        date: "2014-07-22T00:00:00.000Z",//Date
        placementId: 1,//Placement ID
        creativeId: 8,//Creative ID
        num: 30
    }

## Spot details

    GET http://m.trackmaster.com.cn/api_v2/spots/:id

**Response**

{:.prettyprint}
    {
        campaignId: 50000,//Campaign ID
        date: "2014-07-22T00:00:00.000Z",//Date
        placementId: 1,//Placement ID
        creativeId: 8,//Creative ID
        num: 30

        }
    
## Deltet spot

    DELETE http://m.trackmaster.com.cn/api_v2/spots/:id

**响应**

    Status: 204 OK 