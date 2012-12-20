---
weight: 5
layout: default
category: sitemaster
language: cn
title: 站点分析报告
---

# 站点分析报告

* TOC
{:toc}

## 获取指定站点的报告

    GET /sites/:site_id/analytics

**响应**

    Status: 200 OK
    Link: <http://{{site.site_api_host}}/sites/xxxx/analytics?page=2>; rel="next",
          <http://{{site.site_api_host}}/sites/xxxx/analytics?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
          "dm:date": "2012-12-12",
          "mt:visits": 30898,
          "mt:pageviews": 69239,
          "mt:visitors": 20123
      }
    ]


**参数**

`start-date`
: _必选_ **date** - 开始日期 格式 YYYY-mm-dd 例如: 2012-12-12

`end-date`
: _必选_ **date** - 结束日期 格式 YYYY-mm-dd 例如: 2012-12-12

`metrics`
: _必选_ **string** - 指标，多个用逗号隔开，指标有那些可以参考页面底部指标列表

`diensions`
: _可选_ **string** - 维度，多个用逗号开个，最多支持3个维度 参考页面底部维度列表

`filters`
: _可选_ **string** - 过滤条件，可以对指标或者维度过滤，具体的过滤规则查看页面底部filter的说明

`segment`
: _可选_ **string** - 高级细分，设置对访次的细分过滤，具体查看页面底部segment的说明

`start-index`
: _可选_ **integer** -数据开始条目序号

`max-results`
: _可选_ **integer** -数据条目最大条目数(系统限制小于5000，否则异常)

`sort`
: _可选_ **date** - 排序方式，默认不排序格式


## diensions

名称|类型|级别|说明
----|----|----|
dm:visitorType|	Visitor|visit-dm|访问者类型(新访或回访，值为“new”或者“return”)
dm:visitCount|	Visitor	|visit-dm|第几次访问，大于0的自然数
dm:daysSinceLastVisit	|Visitor	|visit-dm|距离上次访问的天数
dm:referralPath|	Traffic Sources |visit-dm|引荐路径
dm:campaign|	Traffic Sources| visit-dm|项目，smt_cp
dm:placement	|Traffic Sources| visit-dm|广告位,smt_pl
dm:medium	|Traffic Sources| visit-dm|媒体，smt_md
dm:keyword	|Traffic Sources| visit-dm|关键字，smt_kw
dm:creative|	Traffic Sources| visit-dm|创意，smt_ct
dm:cookieSourceType|	Traffic Sources| visit-dm|来源类型，`点击引导` 或 `曝光引导`或`(not set)`
dm:cookieCampaign|	Traffic Sources| visit-dm|项目，通过 cookie 获取
dm:cookiePlacement	|Traffic Sources| visit-dm|广告位,通过 cookie 获取
dm:cookieMedium	|Traffic Sources| visit-dm|媒体，通过 cookie 获取
dm:cookieKeyword	|Traffic Sources| visit-dm|关键字，通过 cookie 获取
dm:cookieCreative|	Traffic Sources| visit-dm|创意，通过 cookie 获取
dm:browser	|Platform / Device|visit-dm|浏览器（[字典](https://github.com/AdMaster/SiteMaster/wiki/siteBrowse)）
dm:browserVersion	|Platform / Device|visit-dm|浏览器版本（[字典](https://github.com/AdMaster/SiteMaster/wiki/siteBrowse)）
dm:operatingSystem	|Platform / Device|visit-dm|操作系统（字典）
dm:operatingSystemVersion|	Platform / Device|visit-dm|操作系统版本（字典）
dm:isMobile|	Platform / Device	|visit-dm|是否是移动设备(Yes or No)
dm:mobileDeviceBranding	|Platform / Device|	visit-dm|移动设备品牌，如：三星，htc(字典)
dm:mobileDeviceModel	|Platform / Device	|visit-dm|移动设备型号，如ipad1，ipad2（字典）
dm:mobileDeviceInfo|	Platform / Device|	visit-dm|品牌+型号
dm:mobileInputSelector|	Platform / Device|	visit-dm|输入方式，值为 “touchscreen” 或者 “(not set)”
dm:continent	|Geo / Network	|visit-dm|大洲（字典）
dm:country	|Geo / Network	|visit-dm|国家（字典）
dm:province	|Geo / Network	|visit-dm|省份（字典）
dm:city	|Geo / Network	|visit-dm|城市（字典）
dm:latitude|	Geo / Network	|visit-dm|纬度
dm:longitude	|Geo / Network|	visit-dm|经度
dm:flashVersion|	System|	visit-dm|flash版本（采集到的原始数据）
dm:javaEnabled|System	|visit-dm|是否支持java（Yes or No）
dm:language|	System|visit-dm|语言
dm:screenColors	|System	|visit-dm|屏幕颜色
dm:screenResolution	|System|	visit-dm|屏幕分辨率
dm:landingPagePath	|Page Tracking|	visit-dm|登陆页路径
:exitPagePath|	Page Tracking	|visit-dm|退出页路径
dm:date|	Time 	|time-dm|日期
dm:month	|Time |	time-dm|月份
dm:week	|Time 	|time-dm|周
dm:hour	|Time |	time-dm|时
dm:host|	Page Tracking	|page-dm|主机名(带端口号)
dm:pagePath	|Page Tracking|	page-dm|页面路径
dm:pageTitle	|Page Tracking	|page-dm|页面标题
dm:eventCategory	|Event Tracking 	||事件分类
dm:eventAction	|Event Tracking 	||事件动作
dm:eventLabel	|Event Tracking 	||事件标签
dm:adcookie|	Traffic Sources|visit-dm|admcookie id


##metrics 说明

名称|类型|级别|说明
----|----|----|
mt:visitors	|Visitor|	raw-mt|通过第一方cookie 统计的访问者
mt:newVisits	|Visitor|	raw-mt|新访者
mt:visits	|Session	|raw-mt|访问次数
mt:bounces	|Session|raw-mt|跳出次数
mt:entrances	|Page Tracking	|raw-mt|进入次数
mt:pageviews	|Page Tracking	|raw-mt|浏览量
mt:uniquePageviews	|Page Tracking	|raw-mt|唯一浏览量
mt:timeOnPage	|Page Tracking	|raw-mt|页面停留时间
mt:exits	|Page Tracking	|raw-mt|退出次数
mt:pageLoadTime|	Site Speed	|raw-mt|页面加载时间（所有样本加载时间总和）
mt:pageLoadSample|Site Speed	|raw-mt|页面加载样本数量
mt:totalEvents|	Event Tracking 	|raw-mt|事件总数
mt:uniqueEvents|	Event Tracking |	raw-mt|唯一身份事件数
mt:eventValue	|Event Tracking |	raw-mt|事件价值
mt:advisitors|	Visitor|	raw-mt|通过第三方admcookie 统计的访问者

##filters 说明

####过滤器操作符

针对维度和指标分别有6个过滤器操作符，操作符必须被URL编码。  

####指标操作符

操作符|描述|URL编码格式|举例
---|---|---|---
==|等于|%3D%3D|filters=mt:timeOnPage%3D%3D10，返回页面停留时间等于10秒的结果
!=|不等于|!%3D|filters=mt:timeOnPage!%3D10,返回页面停留时间不等于10秒的结果
\>|大于|%3E|filters=ga:timeOnPage%3E10，返回页面停留时间大于10秒的结果
<|小于|%3C|filters=ga:timeOnPage%3C10，返回页面停留时间小于10秒的结果
\>=|大于等于|%3E%3D|filters=ga:timeOnPage%3E%3D10，返回页面停留时间大于等于10秒的结果
<=|小于等于|%3C%3|filters=ga:timeOnPage%3C%3D10，返回页面停留时间小于等于10秒的结果  

####维度过滤器

操作符|描述|URL编码格式|举例
---|---|---|---
==|完全匹配|%3D%3D|filters=ga:city%3D%3DIrvine，返回城市为Irvine的统计指标数据
!=|不匹配|!%3D|filters=ga:city!%3DIrvine，返回城市不为Irvine的统计指标数据
=@|包含子串|%3D@|filters=ga:city%3D@York，返回城市名中包含 York 字符的统计指标数据
!@|不包含子串|!@|filters=ga:city!@York，返回城市名中不包含 York 字符的统计指标数据
=~|和后面语法匹配|%3D~|filters=ga:city%3D~%5ENew.* ，返回城市名以 New 开头的统计指标数据
!~|和后面语法不匹配|!~|filters=ga:city!~%5ENew.* ，返回城市名不以 New 开头的统计指标数据  

###过滤器语法
 
###组合过滤器
过滤器可以用 OR 或 AND 进行逻辑组合，语句部分的长度上限为128字符。  
####OR
“或操作”用逗号(,)表示，优先级高于与操作。  
例：如下表示国家为 United States 或 Canada：

	ga:country==United%20States,ga:country==Canada

如下表示在 Windows 或 Mac 操作系统下的 Firefox 用户:

	ga:browser==Firefox;ga:operatingSystem==Windows,ga:  

####AND
“与操作”用分号(;)表示，可用于在同一表达中组合维度和指标。  
例：如下表示国家为 United States，同时访次大于5： 

	ga:country==United%20States;ga:visits>5
如下表示国家为 United States ，同时语言不以 'en'开头:


##segment 说明
高级细分功能暂不提供


