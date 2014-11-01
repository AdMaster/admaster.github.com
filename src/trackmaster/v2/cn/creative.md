---
weight: 6
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 创意
version: v2
---

# 创意

* TOC
{:toc}

## 获取指定项目所有创意

    GET /campaigns/:campaignId/creatives

**响应**

{:.prettyprint}
    [{
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
        "color": 'No1','No2','No3','No4','No5','No6','No7','No8','No9','No10','No11','No12','No13','No14','No15','No16','No17','No18','No19','No20', // 创意的吉祥色，该颜色代表着创意, 同一个项目下颜色不可以相同
        "materialPath"://创意素材路径，支持swf，jpg，gif，png，flv
        "note"://创意的说明, 200个字之内
        "creatorId": 999, // 创建者id
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
    }]


## 获取项目下指定创意信息

    GET /creatives/:id

**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
        "color": 'No1','No2','No3','No4','No5','No6','No7','No8','No9','No10','No11','No12','No13','No14','No15','No16','No17','No18','No19','No20', // 创意的吉祥色，该颜色代表着创意, 同一个项目下颜色不可以相同
        "materialPath"://创意素材路径，支持swf，jpg，gif，png，flv
        "note"://创意的说明, 200个字之内
        "creatorId": 999, // 创建者id
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
    }


## 在指定项目下添加创意

    POST /campaigns/:campaignId/creatives

最多可以创建创意的数目为 20 个。

**参数**

{:.prettyprint}
    {
        "name": //必填，"创意名称",
        "shortName"://必填，创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
        "color": 'No1','No2','No3','No4','No5','No6','No7','No8','No9','No10','No11','No12','No13','No14','No15','No16','No17','No18','No19','No20', // 创意的吉祥色，该颜色代表着创意, 同一个项目下颜色不可以相同
        "materialPath"://创意素材路径，支持swf，jpg，gif，png，flv
        "note"://创意的说明, 200个字之内
        "creatorId": 999, // 创建者id
    }

**响应**

{:.prettyprint}
    {
        //创意 ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/1",
        //创意名称
        "name": "创意 A",
        //创意名缩写
        "shortname": "GO",
        //创意描述
        "description": "此创意针对20-30岁人群",
        //创意点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
    }

## 删除指定的创意

    DELETE /creatives/:id

删除创意后，创意变为默认创意，注意此时获取的监测代码会发生变化。

**响应**

    Status: 200 OK

## 修改指定的创意属性

    PATCH /creatives/:id



**参数**

{:.prettyprint}
    {
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
        "color": 'No1','No2','No3','No4','No5','No6','No7','No8','No9','No10','No11','No12','No13','No14','No15','No16','No17','No18','No19','No20', // 创意的吉祥色，该颜色代表着创意, 同一个项目下颜色不可以相同
        "materialPath"://创意素材路径，支持swf，jpg，gif，png，flv
        "note"://创意的说明, 200个字之内
        "creatorId": 999, // 创建者id
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
    }

**响应**

{:.prettyprint}
    {
        "id": 999,
        "name": //"创意名称",
        "shortName"://创意短名称，2个字符之内
        "targetUrl"://点击跳转地址
        "campaignId": 999, // 关联项目id
        "color": 'No1','No2','No3','No4','No5','No6','No7','No8','No9','No10','No11','No12','No13','No14','No15','No16','No17','No18','No19','No20', // 创意的吉祥色，该颜色代表着创意, 同一个项目下颜色不可以相同
        "materialPath"://创意素材路径，支持swf，jpg，gif，png，flv
        "note"://创意的说明, 200个字之内
        "creatorId": 999, // 创建者id
        "createdAt": "2012-01-10T02:30:59Z",
        "updatedAt": "2012-01-10T02:30:59Z"
    }
