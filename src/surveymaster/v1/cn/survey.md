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

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `status`     - 查看问卷状态

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

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "answered_count": 0,
            "created_at": "2014-01-14T11:34:58+08:00",
            "deleted_at": null,
            "finished_count": 0,
            "label": "",
            "landing_count": 0,
            "qualified_count": 0,
            "title": "test",
            "updated_at": "2014-01-14T11:35:17+08:00",
            "user_id": "52cfa8cde092372bf6000001",
            "id": "52d4b062e092371da5000001",
            "logo":  {
                "_id": "52d4b062e092371da5000002",
                "status": true,
                "url": ""
            }
        }
    ]

## 2. 获取所有问卷列表
    GET /admin/surveys

* 仅管理员可获取所有的问卷列表

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `status`     - 查看问卷状态

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

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "answered_count": 0,
            "created_at": "2014-01-14T11:34:58+08:00",
            "deleted_at": null,
            "finished_count": 0,
            "label": "",
            "head": "xxx",
            "foot": "xxx",
            "show_progressbar": true,
            "show_page_number": true,
            "question_numbering": "global",
            "freq_control": true,
            "landing_count": 0,
            "qualified_count": 0,
            "title": "test",
            "updated_at": "2014-01-14T11:35:17+08:00",
            "user_id": "52cfa8cde092372bf6000001",
            "id": "52d4b062e092371da5000001",
            "logo":  {
                "_id": "52d4b062e092371da5000002",
                "status": true,
                "url": ""
            }
        }
    ]

## 3. 获取某个用户问卷列表
    GET /admin/users/:user_id/surveys

* 仅管理员可获取所有的问卷列表

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `status`     - 查看问卷状态

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

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "answered_count": 0,
            "created_at": "2014-01-14T11:34:58+08:00",
            "deleted_at": null,
            "finished_count": 0,
            "label": "",
            "head": "xxx",
            "foot": "xxx",
            "show_progressbar": true,
            "show_page_number": true,
            "question_numbering": "global",
            "freq_control": true,
            "landing_count": 0,
            "qualified_count": 0,
            "title": "test",
            "updated_at": "2014-01-14T11:35:17+08:00",
            "user_id": "52cfa8cde092372bf6000001",
            "id": "52d4b062e092371da5000001",
            "logo":  {
                "_id": "52d4b062e092371da5000002",
                "status": true,
                "url": ""
            }
        }
    ]

## 4. 获取当前用户指定问卷
    GET /surveys/:id

* 根据当前用户权限，获取此用户可查看的问卷列表
* 普通用户仅查看自己建立的问卷

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `status`     - 查看问卷状态

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

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    {
        "answered_count": 0,
        "created_at": "2014-01-14T11:34:58+08:00",
        "deleted_at": null,
        "finished_count": 0,
        "label": "",
        "head": "xxx",
        "foot": "xxx",
        "show_progressbar": true,
        "show_page_number": true,
        "question_numbering": "global",
        "freq_control": true,
        "landing_count": 0,
        "qualified_count": 0,
        "title": "test",
        "updated_at": "2014-01-14T11:35:17+08:00",
        "user_id": "52cfa8cde092372bf6000001",
        "id": "52d4b062e092371da5000001",
        "logo":  {
            "_id": "52d4b062e092371da5000002",
            "status": true,
            "url": ""
        }
    }



## 5. 创建问卷
    POST /surveys

**请求**

`method`
: _可选_ *String* - 复制模板/复制问卷
: { method: 'tpl', history_id: 'tpl_id' }
: { method: 'copy', history_id: 'survey_id' }

`logo`
: _可选_ *Hash* - LOGO相关信息
: { logo: { status: true, url: 'xxxx'}}

`title`
: _必选_ *String* - 问卷标题，长度范围2 - 100个字符

`label`
: _可选_ *String* - 问卷说明

`head`
: _可选_ *String* - 问卷头信息

`foot`
: _可选_ *String* - 问卷尾信息

`freq_control`
: _可选_ *Boolean* - 是否开启频次控制

`show_progressbar`
: _可选_ *Boolean* - 是否显示进度条

`show_page_number`
: _可选_ *Boolean* - 是否显示页号

`question_numbering`
: _可选_ *String* - 问题编号方式

  * `none`   - 无编号方式
  * `global` - 全局编号方式
  * `bypage` - 页内编号方式

{:.prettyprint}
    {
        "label": "abc",
        "head": "xxx",
        "foot": "xxx",
        "show_progressbar": true,
        "show_page_number": true,
        "question_numbering": "global",
        "freq_control": true,
        "title": "test",
        "logo":  {
            "status": true,
            "url": "xxx"
        }
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "answered_count": 0,
        "created_at": "2014-01-14T11:34:58+08:00",
        "deleted_at": null,
        "finished_count": 0,
        "label": "abc",
        "head": "xxx",
        "foot": "xxx",
        "show_progressbar": true,
        "show_page_number": true,
        "question_numbering": "global",
        "freq_control": true,
        "landing_count": 0,
        "qualified_count": 0,
        "title": "test",
        "updated_at": "2014-01-14T11:35:17+08:00",
        "user_id": "52cfa8cde092372bf6000001",
        "id": "52d4b062e092371da5000001",
        "logo":  {
            "_id": "52d4b062e092371da5000002",
            "status": true,
            "url": ""
        }
    }

## 6. 修改指定问卷
    PATCH /surveys/:id

**请求**

`logo`
: _可选_ *Hash* - LOGO相关信息
: { logo: { status: true, url: 'xxxx'}}

`title`
: _必选_ *String* - 问卷标题，长度范围2 - 100个字符

`label`
: _可选_ *String* - 问卷说明

`head`
: _可选_ *String* - 问卷头信息

`foot`
: _可选_ *String* - 问卷尾信息

`freq_control`
: _可选_ *Boolean* - 是否开启频次控制

`show_progressbar`
: _可选_ *Boolean* - 是否显示进度条

`show_page_number`
: _可选_ *Boolean* - 是否显示页号

`question_numbering`
: _可选_ *String* - 问题编号方式

  * `none`   - 无编号方式
  * `global` - 全局编号方式
  * `bypage` - 页内编号方式

{:.prettyprint}
    {
        "label": "xxx",
        "head": "xxx",
        "foot": "xxx",
        "show_progressbar": true,
        "show_page_number": true,
        "question_numbering": "global",
        "freq_control": true,
        "title": "test",
        "logo":  {
            "status": true,
            "url": "xxx"
        }
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "answered_count": 0,
        "created_at": "2014-01-14T11:34:58+08:00",
        "deleted_at": null,
        "finished_count": 0,
        "label": "",
        "head": "xxx",
        "foot": "xxx",
        "show_progressbar": true,
        "show_page_number": true,
        "question_numbering": "global",
        "freq_control": true,
        "landing_count": 0,
        "qualified_count": 0,
        "title": "test",
        "updated_at": "2014-01-14T11:35:17+08:00",
        "user_id": "52cfa8cde092372bf6000001",
        "id": "52d4b062e092371da5000001",
        "logo":  {
            "_id": "52d4b062e092371da5000002",
            "status": true,
            "url": ""
        }
    }

## 7. 删除指定的问卷
    DELETE /surveys/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 8. 获取所有问卷模板
    GET /surveys/template/all

{:.prettyprint}
    {
        "answered_count": 0,
        "created_at": "2013-06-06T15:12:47+08:00",
        "deleted_at": null,
        "finished_count": 0,
        "label": "",
        "landing_count": 0,
        "qualified_count": 0,
        "title": "标准人口属性问卷",
        "updated_at": "2014-01-07T12:35:45+08:00",
        "user_id": "5159419c866106a1c9000001",
        "id": "51c00a26a4d6318cc6a79546",
        "logo": {
            "_id": "523053e3866106ee6e0000b1",
            "status": true,
            "url": ""
        }
    }

## 9. 获取已删除的问卷
    GET /admin/surveys/deleted

* 仅管理员可获取所有的问卷列表

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `created_at` - 建立时间
  * `updated_at` - 最后更新时间
  * `status`     - 查看问卷状态

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

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "answered_count": 0,
            "created_at": "2014-01-14T11:34:58+08:00",
            "deleted_at": null,
            "finished_count": 0,
            "label": "",
            "head": "xxx",
            "foot": "xxx",
            "show_progressbar": true,
            "show_page_number": true,
            "question_numbering": "global",
            "freq_control": true,
            "landing_count": 0,
            "qualified_count": 0,
            "title": "test",
            "updated_at": "2014-01-14T11:35:17+08:00",
            "user_id": "52cfa8cde092372bf6000001",
            "id": "52d4b062e092371da5000001",
            "logo":  {
                "_id": "52d4b062e092371da5000002",
                "status": true,
                "url": ""
            }
        }
    ]

## 10. 恢复被删除的问卷
    PATCH /admin/surveys/:survey_id/restore

* 仅管理员可恢复问卷

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 11. 彻底删除的问卷
    DELETE /admin/surveys/:survey_id/crashing

* 仅管理员可彻底删除问卷

**响应**

    Status: 204
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
