---
weight: 5
layout: default
category: sitemaster
language: cn
title: 站点访问详情
---

# 站点访问详情

* TOC
{:toc}

## 获取指定站点的访问详情

    GET /sites/:site_id/visits

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/xxxx/visits?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites/xxxx/visits?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          "id": '2323fwfs',
          "visitorType": "new",
          "visitCount" : 2,
          "daysSinceLastVisit": 1,
          "referralPath": "/home",
          "campaign": 10234,
          "placement" 200019232,
          "medium": 1345,
          "keyword": 0,
          "creative": 0,
          "cookieSourceType": "view",
          "cookieCampaign": 10269,
          "cookiePlacement": 200011234,
          "cookieMedium": 1239,
          "cookieKeyword": 12,
          "cookieCreative": 0,
          "browser": "Chrome",
          "browserVersion": "21.11.2.3",
          "operatingSystem": "mac lion",
          "operatingSystemVersion": "10.6",
          "isMobile": "no",
          "mobileDeviceBranding": "(not set)",
          "mobileDeviceModel": "(not set)",
          "mobileDeviceInfo": "(not set)",
          "mobileInputSelector": "normal",
          "continent": "亚洲",
          "country": "中国",
          "province": "北京",
          "city": "北京",
          "latitude": 114.21324,
          "longitude": 42.12312,
          "flashVersion": 11.1,
          "javaEnabled": "yes",
          "language": "zh_cn",
          "screenColors": "32bit",
          "screenResolution": "1440*900",
          "landingPagePath": "/index",
          "exitPagePath": "/about",
          "date": "2012-12-21",
          "month": 12,
          "week": 45,
          "hour": 15
      }
    ]


**参数**

`start-date`
: _必选_ **date** - 开始日期 格式 YYYY-mm-dd 例如: 2012-12-12

`end-date`
: _必选_ **date** - 结束日期 格式 YYYY-mm-dd 例如: 2012-12-12

`filters`
: _可选_ **string** - 过滤条件，可以对指标或者维度过滤，具体的过滤规则查看页面底部filter的说明

`segment`
: _可选_ **string** - 高级细分，设置对访次的细分过滤，具体查看页面底部segment的说明

`start-index`
: _可选_ **integer** -数据开始条目序号

`max-results`
: _可选_ **integer** -数据条目最大条目数(系统限制小于5000，否则异常)

`sort`
: _可选_ **string** - 排序方式，默认不排序格式



## 获取指定站点的页面浏览详情

    GET /sites/:site_id/pageviews

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/xxxx/pageviews?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites/xxxx/pageviews?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          "id": "12312",
          "visitId": "1232323",
          "pageId": "123123",
          "pageTitle": "欢迎来到admaster",
          "pagePath": "/weclome",
          "created_at": "2012-12-21 15:03:37",
          "pageLoadTime": 0,
          "stayTime": 123,
          "referralUrl": "http://www.admaster.com.cn/",
          "cliclNum": 20
      }
    ]


**参数**

`start-date`
: _必选_ **date** - 开始日期 格式 YYYY-mm-dd 例如: 2012-12-12

`end-date`
: _必选_ **date** - 结束日期 格式 YYYY-mm-dd 例如: 2012-12-12

`filters`
: _可选_ **string** - 过滤条件，可以对指标或者维度过滤，具体的过滤规则查看页面底部filter的说明

`segment`
: _可选_ **string** - 高级细分，设置对访次的细分过滤，具体查看页面底部segment的说明

`start-index`
: _可选_ **integer** -数据开始条目序号

`max-results`
: _可选_ **integer** -数据条目最大条目数(系统限制小于5000，否则异常)

`sort`
: _可选_ **string** - 排序方式，默认不排序格式


## 获取指定站点的事件详情

    GET /sites/:site_id/events

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/xxxx/events?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites/xxxx/events?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          "pageviewId": "123123",
          "visitId": "123123",
          "created_at": "2012-12-21 15:16:12",
          "category": "首页",
          "action": "登陆",
          "label": "(not set)",
          "value": 120
      }
    ]


**参数**

`start-date`
: _必选_ **date** - 开始日期 格式 YYYY-mm-dd 例如: 2012-12-12

`end-date`
: _必选_ **date** - 结束日期 格式 YYYY-mm-dd 例如: 2012-12-12

`filters`
: _可选_ **string** - 过滤条件，可以对指标或者维度过滤，具体的过滤规则查看页面底部filter的说明

`start-index`
: _可选_ **integer** -数据开始条目序号

`max-results`
: _可选_ **integer** -数据条目最大条目数(系统限制小于5000，否则异常)

`sort`
: _可选_ **string** - 排序方式，默认不排序格式
## dimensions

##filters 说明

####过滤器操作符

操作符|描述|URL编码格式|举例
---|---|---|---
==|等于|%3D%3D|filters=mt:timeOnPage%3D%3D10，返回页面停留时间等于10秒的结果
!=|不等于|!%3D|filters=mt:timeOnPage!%3D10,返回页面停留时间不等于10秒的结果
\>|大于|%3E|filters=ga:timeOnPage%3E10，返回页面停留时间大于10秒的结果
<|小于|%3C|filters=ga:timeOnPage%3C10，返回页面停留时间小于10秒的结果
\>=|大于等于|%3E%3D|filters=ga:timeOnPage%3E%3D10，返回页面停留时间大于等于10秒的结果
<=|小于等于|%3C%3|filters=ga:timeOnPage%3C%3D10，返回页面停留时间小于等于10秒的结果  
=@|包含子串|%3D@|filters=ga:city%3D@York，返回城市名中包含 York 字符的统计指标数据
!@|不包含子串|!@|filters=ga:city!@York，返回城市名中不包含 York 字符的统计指标数据
=~|和后面语法匹配|%3D~|filters=ga:city%3D~%5ENew.* ，返回城市名以 New 开头的统计指标数据
!~|和后面语法不匹配|!~|filters=ga:city!~%5ENew.* ，返回城市名不以 New 开头的统计指标数据  

###过滤器语法
 

##segment 说明
visits 接口可以根据 pageviews 或者 events 的filters 进行过滤
pageviews 接口可以根据 event 的filters 进行过滤


