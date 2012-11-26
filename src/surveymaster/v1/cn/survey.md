---
weight: 2
layout: default
category: surveymaster
title: 问卷相关
language: cn
---

* TOC
{:toc}

## 1. 获取问卷列表

    GET /surveys

* 根据当前用户权限，获取此用户可查看的问卷列表
* 普通用户仅查看自己建立的问卷
* 管理员可查看所有问卷

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `landing_count` - 查看问卷用户数
  * `answered_count` - 回答问卷用户数
  * `finished_count` - 完整回答问卷用户数

`direction`
: _可选_ **String** - 排序方式

  * `asc` - 升序
  * `desc` - 降序 (_默认_)

`created_start`
: _可选_ **integer** - 指定此参数，将获取建立时间在此范围之后的问卷

  * `2012-08-03` - 符合ISO 8601格式的日期形式
  * `2012-07-31T09:36:27Z` - 符合ISO 8601格式的时间格式

`created_end`
: _可选_ **integer** - 指定此参数，将获取建立时间在此范围之前的问卷

  * 同`created_start`

`updated_start`
: _可选_ **integer** - 指定此参数，将获取最后修改时间在此范围之后的问卷

  * 同`created_start`

`updated_end`
: _可选_ **integer** - 指定此参数，将获取最后修改时间在此范围之前的问卷

  * 同`created_start`

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
      {
        "survey_id" : 112,
        "url" : "http://api.surveymaster.com/surveys/112",
        "logo" : "http://domain.com/img/logo.gif",
        "title" : "伊利8月新生活",
        "label" : "第一波",
        "owner_id" : 123,
        "created_at" : "2012-07-31T09:36:27Z",
        "updated_at" : "2012-07-31T09:46:27Z",
        "head" : "感谢您参与我们的问卷调查。",
        "foot" : "AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
        "show_progressbar" : "no",
        "show_page_number" : "yes",
        "question_numbering" : "global",
        "is_onepage" : "no",
        "is_deleted" : "no",
        "landing_count" : 50000,
        "answered_count" : 30000,
        "finished_count" : 5000
      },
      {
        /* 另一文档数据 */
      }
    ]


## 2. 获取某个用户问卷列表

    GET /users/:user_id/surveys

* 仅管理员可获取指定用户的问卷列表

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `id` - 按问卷ID排序（_默认_）
  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `landing_count` - 查看问卷用户数
  * `answered_count` - 回答问卷用户数
  * `finished_count` - 完整回答问卷用户数

`direction`
: _可选_ **String** - 排序方式

  * `asc` - 升序
  * `desc` - 降序 (_默认_)

`created_start`
: _可选_ **integer** - 指定此参数，将获取建立时间在此范围之后的问卷

  * `2012-08-03` - 符合ISO 8601格式的日期形式
  * `2012-07-31T09:36:27Z` - 符合ISO 8601格式的时间格式

`created_end`
: _可选_ **integer** - 指定此参数，将获取建立时间在此范围之前的问卷

  * 同`created_start`

`updated_start`
: _可选_ **integer** - 指定此参数，将获取最后修改时间在此范围之后的问卷

  * 同`created_start`

`updated_end`
: _可选_ **integer** - 指定此参数，将获取最后修改时间在此范围之前的问卷

  * 同`created_start`

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
      {
        "survey_id" : 112,
        "url" : "http://api.surveymaster.com/surveys/112",
        "logo" : "http://domain.com/img/logo.gif",
        "title" : "伊利8月新生活",
        "label" : "第一波",
        "owner_id" : 123,
        "created_at" : "2012-07-31T09:36:27Z",
        "updated_at" : "2012-07-31T09:46:27Z",
        "head" : "感谢您参与我们的问卷调查。",
        "foot" : "AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
        "show_progressbar" : "no",
        "show_page_number" : "yes",
        "question_numbering" : "global",
        "is_onepage" : "no",
        "is_deleted" : "no",
        "landing_count" : 50000,
        "answered_count" : 30000,
        "finished_count" : 5000
      },
      {
        /* 另一文档数据 */
      }
    ]


## 3. 创建问卷

    POST /surveys

**请求**

`logo`
: _可选_ *String* - LOGO图标地址

`title`
: _必选_ *String* - 问卷标题，长度范围2 - 100个字符

`label`
: _可选_ *String* - 问卷说明

`head`
: _可选_ *String* - 问卷头信息

`foot`
: _可选_ *String* - 问卷尾信息

`show_progressbar`
: _可选_ *String* - 是否显示进度条

`is_onepage`
: _可选_ *String* - 是否在一页显示

`show_page_number`
: _可选_ *String* - 是否显示页号

`question_numbering`
: _可选_ *String* - 问题编号方式

  * `global` - 全局编号方式
  * `in_page` - 页内编号方式

{:.prettyprint}
    {
      "logo" : "http://domain.com/img/logo.gif",
      "title" : "伊利8月新生活",
      "label" : "第一波",
      "head" : "首先感谢您参与我们的问卷调查。",
      "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。",
      "show_progressbar" : "no",
      "is_onepage" : "no",
      "show_page_number" : "yes",
      "question_numbering" : "global",
    }

**响应**

    Status: 201 Created
    Location: http://api.surveymaster.com.cn/surveys

{:.prettyprint}
    {
      "survey_id" : 112,
      "url" : "http://api.surveymaster.com.cn/surveys/112",
      "logo" : "http://domain.com/img/logo.gif",
      "title" : "伊利8月新生活",
      "label" : "第一波",
      "owner_id" : 123,
      "created_at" : "2012-07-31T09:36:27Z",
      "updated_at" : "2012-07-31T09:46:27Z",
      "head" : "感谢您参与我们的问卷调查。",
      "foot" : "AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
      "show_progressbar" : "no",
      "show_page_number" : "yes",
      "question_numbering" : "global",
      "is_onepage" : "no",
      "is_deleted" : "no",
      "landing_count" : 0,
      "answered_count" : 0,
      "finished_count" : 0
    }


## 4. 获取指定问卷详情

    GET /surveys/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
      "survey_id" : 112,
      "url" : "http://api.surveymaster.com.cn/surveys/112",
      "logo" : "http://domain.com/img/logo.gif",
      "title" : "伊利8月新生活",
      "label" : "第一波",
      "owner_id" : 123,
      "created_at" : "2012-07-31T09:36:27Z",
      "updated_at" : "2012-07-31T09:46:27Z",
      "head" : "感谢您参与我们的问卷调查。",
      "foot" : "AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
      "show_progressbar" : "no",
      "show_page_number" : "yes",
      "question_numbering" : "global",
      "is_onepage" : "no",
      "is_deleted" : "no",
      "landing_count" : 0,
      "answered_count" : 0,
      "finished_count" : 0
    }

## 5. 修改指定问卷

    PATCH /surveys/:id

**请求**

`logo`
: _可选_ *String* - LOGO图标地址

`title`
: _必选_ *String* - 问卷标题，长度范围2 - 100个字符

`label`
: _可选_ *String* - 问卷说明

`head`
: _可选_ *String* - 问卷头信息

`foot`
: _可选_ *String* - 问卷尾信息

`show_progressbar`
: _可选_ *String* - 是否显示进度条

`is_onepage`
: _可选_ *String* - 是否在一页显示

`show_page_number`
: _可选_ *String* - 是否显示页号

`question_numbering`
: _可选_ *String* - 问题编号方式

  * `global` - 全局编号方式
  * `in_page` - 页内编号方式

`is_deleted`
: _可选_ *String* - 是否删除

{:.prettyprint}
    {
      "logo" : "http://domain.com/img/logo.gif",
      "title" : "伊利8月新生活",
      "label" : "第一波",
      "head" : "首先感谢您参与我们的问卷调查。",
      "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。",
      "show_progressbar" : "no",
      "is_onepage" : "no",
      "show_page_number" : "yes",
      "question_numbering" : "global",
      "is_deleted" : "no"
    }

**响应**

    Status: 204 No Content
