---
weight: 5
layout: default
category: openmaster
language: cn
title: 接口定义 - 通用说明
version: v1
---

# 接口定义 - 通用说明


## 通用参数说明

`access_token`
	oauth 验证串，通过授权验证可以得到，请求授权数据的时候需要携带
	

## 返回状态说明

**返回状态在请求返回的头部信息**
	
`200 OK`
	请求成功

`201 CREATED`
	创建成功

`202 ACCEPTED`
	更新、修改成功

`204 NO CONTENT`
	无返回内容

`400 BAD REQUEST`
	请求地址不存在或者带有不支持的参数

`401 UNAUTHORIZED`
	未经授权

`403 FORBIDDEN`
	禁止访问

`404 NOT FOUND`
	请求的资源不存在

`422 UNPROCESSABLE ENTITY`
  请求参数错误，返回消息中包含错误信息列表

`500 INTERNAL SERVER ERROR`
	服务器内部错误

## 错误代码说明

