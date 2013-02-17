---
weight: 5
layout: default
category: trackmaster
subcategory: agency
language: cn
title: 项目
---

# 项目

* TOC
{:toc}

## 获取指定工作网络下某个广告主有操作权限的项目列表

    GET /networks/:network_id/advertisers/:advertiser_id/campaigns

**参数**

`name`
: _可选_ **string** - 项目名称，支持模糊搜索，例如：名称为 “这是一个测试项目” 搜索 “一个”即可找到该项目

`network_brand_id`
: _可选_ **integer** - 项目所属网络品牌ID

`status`
: _可选_ *Enum* - 项目状态

  * `all` - 所有状态, (_默认_)
  * `typing` - 拟稿中，当项目的属性、位置列表、点位等数据任意有值时，状态为编辑中。
  * `testing` - 测试中，当项目的监测代码已生成并已导出，且有数据进来，状态为测试中。
  * `kickoff` - 项目初期，项目上线的第一周为项目初期。
  * `midterm` - 项目中期，项目初期之后到项目结束一周前，为项目中期，小于一周的项目没有项目中期。
  * `teminal` - 项目末期，结束日期的前一周，为项目末期。小于一周的项目没有项目末期；大于一周且小于两周的项目没有项目中期，项目末期为开始日期一周后到结束的时间段。
  * `finished` - 已结束，当前时间在结束时间之后的，为已结束状态。

`start_date`
: _可选_ **date** - 项目开始时间，会列出项目开始日期小于等于此设定的项目

`end_date`
: _可选_ **date** - 项目结束时间，会列出项目结束日期大于等于此设定的项目

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照项目ID排序
  * `network_brand_id` - 按照品牌 ID 排序
  * `name` - 按照项目名称排序
  * `total_cost` - 按照总成本排序
  * `media_num` - 按照媒体数排序
  * `placement_num` - 按照广告位数排序
  * `start_date` - 按照开始日期排序
  * `end_date` - 按照结束日期排序
  * `est_imp` - 按照总预计曝光排序
  * `est_clk` - 按照总预计点击排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/12/advertisers/10035/campaigns?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/12/advertisers/10035/campaigns?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [

      {
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "这是一个测试项目",//项目名称
        "network_brand_id": 10213,//项目的网络品牌 ID
        "cost_type": "CNY",//媒体预算货币类型
        "total_cost": 20000000,//项目总费用
        "start_date": "2012-01-03",//项目开始时间
        "end_date": "2012-06-23",//项目结束时间
        "default_target": "http://www.admaster.com.cn"//项目默认点击目标地址
        "media_num": 8,//项目中媒体数目
        "placement_num": 258,//项目中广告位数目
		"real_imp": 10187535,//项目总曝光数
        "real_clk": 13700,//项目总点击数
        "est_imp": 9183213,//项目预估总曝光数
        "est_clk": 12334,//项目预估总点击数
		"sp_imp": 753823,//项目预估同期曝光数
        "sp_clk": 15342,//项目预估同期点击数
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
      }
    ]


## 获取指定项目信息

    GET /networks/advertisers/campaigns/:id

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/1/medias/attributes>; rel="nwmedias"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [

	{
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "这是一个测试项目",//项目名称
        "network_brand_id": 10213,//项目网络品牌 ID
        "cost_type": "CNY",//媒体预算货币类型
        "total_cost": 20000000,//项目总费用
        "start_date": "2012-01-03",//项目开始时间
        "end_date": "2012-06-23",//项目结束时间
        "default_target": "http://www.admaster.com.cn"//项目默认点击目标地址
        "media_num": 8,//项目中媒体数目
        "placement_num": 258,//项目中广告位数目
        "target_audience":{//目标受众人群
            "age": "19-25",//目标受众人群年龄范围
            "sex": ["male"]//目标受众人群性别。如需同时选择“男”和“女”，格式为"sex": ["male","female"]；如不选择性别，则不输入 sex 内容，即{ "age": "19-25",}
        },
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
    }
]

## 添加指定项目到指定广告主下

    POST /networks/:network_id/advertisers/:advertiser_id/campaigns

注意：同广告主下项目名称不允许重名

**参数**

`name`
: _必选_ **string** - 项目名称，长度范围 3 - 100 个字符

`network_brand_id`
: _必选_ **integer** - 所属网络品牌 ID

`start_date`
: _必选_ **date** - 项目开始日期 YYYY-mm-dd 例如：2012-01-03

`end_date`
: _必选_ **date** - 项目结束日期 YYYY-mm-dd 例如：2012-06-23, 结束日期要大于开始日期

`default_target`
: _必选_ **string** - 项目默认点击目标地址，例如: http://www.admaster.com.cn/

`cost_type`
: _可选_ **string** - 媒体预算货币类型

  * `None` 不设置媒体预算 _默认值_
  * `CNY` 人民币
  * `USD` 美元

`target_audience`
: _可选_ *Object* - 目标受众人群

{:.prettyprint}
    {
        "age": "19-25",//目标受众人群年龄范围，例如: 16-20  16岁到20岁
        "sex": ["male"]//目标受众人群性别，`male` 男, `female` 女。如需同时选择“男”和“女”，格式为"sex": ["male","female"]；如不选择性别，则不输入 sex 内容，即{ "age": "19-25",}
    }


**请求**

{:.prettyprint}   
	{
        "name": "这是一个测试项目",//项目名称
        "network_brand_id": 10021,//项目网络品牌 ID
        "start_date": "2012-01-31",//项目开始日期
        "end_date": "2012-04-20",//项目结束日期
        "default_target": "http://www.admaster.com.cn/",
        "cost_type": "USD",//媒体预算货币类型
        "target_audience": {//目标受众人群
            "age": "16-30",//目标受众人群年龄范围
            "sex": ["female","male"]//目标受众人群性别
        }
    }
	


**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/10786
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 10786,//项目 ID
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10786",
        "name": "这是一个测试项目",//项目名称
        "network_brand_id": 10021,//项目网络品牌 ID
        "cost_type": "USD",//媒体预算货币类型
        "total_cost": 20000,//项目总费用
        "start_date": "2012-01-31",//项目开始日期
        "end_date": "2012-04-20",//项目结束日期
        "default_target": "http://www.admaster.com.cn"
        "media_num": 2,//项目中媒体数目
        "placement_num": 4,//项目中广告位数目
        "target_audience":{//目标受众人群
            "age": "16-30",//目标受众人群年龄范围
            "sex": ["female"]//目标受众人群性别
        },
        "status": "midterm",//项目当前状态
        "is_online": "yes",//如果当前时间在项目开始时间到项目结束时间之后 7 天内，当前参数为“yes”，否则为“no”
        "created_at": "2012-09-06T20:39:23Z"//项目创建时间
    }

**字段说明**

参见页面底部说明

## 修改指定项目属性

    PATCH /networks/advertisers/campaigns/:id

**参数**

`name`
: _可选_ **string** - 项目名称，长度范围 3 - 100 个字符

`network_brand_id`
: _可选_ **integer** - 所属网络品牌 ID

`start_date`
: _可选_ **date** - 项目开始日期 YYYY-mm-dd 例如：2012-01-03

`end_date`
: _可选_ **date** - 项目结束日期 YYYY-mm-dd 例如：2012-06-23, 结束日期要大于开始日期

`default_target`
: _可选_ **string** - 项目默认点击目标地址，例如: http://www.admaster.com.cn/

`cost_type`
: _可选_ **string** - 媒体预算货币类型

  * `None` 不设置媒体预算 _默认值_
  * `CNY` 人民币
  * `USD` 美元

`target_audience`
: _可选_ *Object* - 目标受众人群

{:.prettyprint}
    {
        "age": "19-25",//目标受众人群年龄范围，例如: 16_20  16岁到20岁
        "sex": ["male"]//目标受众人群性别，`male` 男, `female` 女。如需同时选择“男”和“女”，格式为"sex": ["male","female"]；如不选择性别，则不输入 sex 内容，即{ "age": "19-25",}
    }

**请求**

{:.prettyprint}
	{
        "name": "这是一个测试项目",//项目名称
        "network_brand_id": 10021,//项目网络品牌 ID
        "start_date": "2012-01-31",//项目开始日期
        "end_date": "2012-04-20",//项目结束日期
        "default_target": "http://www.admaster.com.cn/",
        "cost_type": "USD",//媒体预算货币类型
        "target_audience": {//目标受众人群
            "age": "16-30",//目标受众人群年龄范围
            "sex": ["female"]//目标受众人群性别
        }
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999



## 删除指定项目

    DELETE /networks/advertisers/campaigns/:id

注意：当项目下有广告位时不允许删除项目；如需删除请先删除该项目下的广告位。

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/12/advertisers/10035/campaigns
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 字段说明

返回值字段         | 字段类型 | 字段说明
id               | integer | 项目 ID
url              | string  | 请求URL
name             | string  | 项目名称
network_brand_id | integer | 项目所属网络品牌 ID
cost_type        | string  | 币种
total_cost       | integer | 总花费
start_date       | date    | 开始日期
end_date         | date    | 结束日期
default_target   | date    | 默认目标
media_num        | integer | 媒体数量
placement_num    | integer | 广告位数量
status           | string  | 状态
is_online        | string  | 是否在线
created_at       | date    | 创建时间

