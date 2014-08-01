---
weight: 4
layout: default
category: surveymaster
title: 问题相关
language: cn
version: v1
---

* TOC
{:toc}

## 1. 获取指定问卷的问题列表
    GET /surveys/:survey_id/questions

**参数**

`page_id`
: _可选_ **String** - 指定排序方式

  * `page_id` - 指定只显示该页的问题列表

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
        {
            "description": "这是一个单选题", // 描述
            "display": { // 显示方式
                "perline": 1, // 每行显示个数
                "random": false, // 是否随机显示
                "style": "radio" // 圆点/下拉显示
                "last_option_fixed": true // 最后一个选项固定
            },
            "is_required": true, // 是否必答
            "number": 1, // 在当前页的编号
            "options": [ // 选项
                "选项1",
                "选项2",
                "选项3"
            ],
            "other": { // 其他选项
                "input": {
                    "max": "100", // 输入字符最大长度
                    "min": "2", // 输入字符最小长度
                    "prompt": "请输入字符", // 输入限制提示
                    "status": true, // 是否显示输入框
                    "type": "char" // 输入框类型，默认为字符类型
                },
                "label": "其他选项", // 其他选项自定义名称，默认为'其他'
                "status": true // 是否出现其他选项
            },
            "page_id": "52d7a76fe092377673000023",
            "quote_ids": [], // 引用题id
            "skip_prompt": "必答题", // 必答提示
            "survey_id": "52d7a76fe092377673000021",
            "title": "单选题", // 标题
            "type": "radio", // 问题类型
            "id": "52d7a76fe092377673000024"
        },
        {
            "description": "这是一个多选题",
            "display": {
                "perline": 1,
                "random": true
                "last_option_fixed": true // 最后一个选项固定
            },
            "exclusive": { // 排他选项
                "label": "", // 排他选项自定义名称，默认为'以上都不是'
                "status": true // 是否出现其他选项
            },
            "is_required": true,
            "max_option_num": 3, // 选项数最大限制
            "min_option_num": 2, // 选项数最小限制
            "number": 1,
            "options": [
                "选项1",
                "选项2",
                "选项3",
                "选项4"
            ],
            "other": {
                "input": {
                    "max": "",
                    "min": "",
                    "prompt": "",
                    "status": true,
                    "type": ""
                },
                "label": "",
                "status": true
            },
            "page_id": "52d7a76fe092377673000028",
            "quote_ids": [],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "多选题",
            "type": "checkbox",
            "id": "52d7a76fe092377673000029"
        },
        {
            "description": "",
            "is_required": true,
            "limit": {
                "max": null,
                "min": null,
                "prompt": "请输入邮箱",
                "type": "email"
            },
            "number": 1,
            "page_id": "52d7a76fe09237767300002e",
            "quote_ids": [],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "单行文本题",
            "type": "text",
            "id": "52d7a76fe09237767300002f"
        },
        {
            "description": "",
            "is_required": true,
            "limit": {
                "max": 1000,
                "min": 1,
                "prompt": ""
            },
            "number": 1,
            "page_id": "52d7a76fe092377673000031",
            "quote_ids": [],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "多行文本题",
            "type": "textarea",
            "id": "52d7a76fe092377673000032"
        },
        {
            "description": "这是一个图片单选题", // 描述
            "display": { // 显示方式
                "perline": 1, // 每行显示个数
                "random": false, // 是否随机显示
                "last_option_fixed": true // 最后一个选项固定
            },
            "is_required": true, // 是否必答
            "number": 1, // 在当前页的编号
            "options": [ // 选项
                "选项1",
                "选项2",
                "选项3"
            ],
            "urls": [ // 选项
                "图片链接1",
                "图片链接2",
                "图片链接3"
            ],
            "other": { // 其他选项
                "input": {
                    "max": "100", // 输入字符最大长度
                    "min": "2", // 输入字符最小长度
                    "prompt": "请输入字符", // 输入限制提示
                    "status": true, // 是否显示输入框
                    "type": "char" // 输入框类型，默认为字符类型
                },
                "label": "其他选项", // 其他选项自定义名称，默认为'其他'
                "status": true // 是否出现其他选项
            },
            "page_id": "52d7a76fe092377673000023",
            "quote_ids": [], // 引用题id
            "skip_prompt": "必答题", // 必答提示
            "survey_id": "52d7a76fe092377673000021",
            "title": "图片单选题", // 标题
            "type": "picradio", // 问题类型
            "id": "52d7a76fe092377673000024"
        },
        {
            "description": "这是一个图片多选题",
            "display": {
                "perline": 1,
                "random": true
                "last_option_fixed": true // 最后一个选项固定
            },
            "exclusive": { // 排他选项
                "label": "", // 排他选项自定义名称，默认为'以上都不是'
                "status": true // 是否出现其他选项
            },
            "is_required": true,
            "max_option_num": 3, // 选项数最大限制
            "min_option_num": 2, // 选项数最小限制
            "number": 1,
            "options": [
                "选项1",
                "选项2",
                "选项3",
                "选项4"
            ],
            "urls": [ // 选项
                "图片链接1",
                "图片链接2",
                "图片链接3",
                "图片链接4"
            ],
            "other": {
                "input": {
                    "max": "",
                    "min": "",
                    "prompt": "",
                    "status": true,
                    "type": ""
                },
                "label": "",
                "status": true
            },
            "page_id": "52d7a76fe092377673000028",
            "quote_ids": [],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "图片多选题",
            "type": "piccheckbox",
            "id": "52d7a76fe092377673000029"
        },
        {
            "column_options": [
                "列选项1",
                "列选项2",
                "列选项3"
            ],
            "description": "",
            "display": {
                "column_random": false, // 列选项是否随机显示
                "row_random": false // 行选项是否随机显示
            },
            "is_required": true,
            "max_row_num": null, // 必答行数最大限制
            "min_row_num": null, // 必答行数最小限制
            "number": 1,
            "page_id": "52d7a76fe092377673000034",
            "quote_ids": [],
            "row_options": [
                "行选项1",
                "行选项2",
                "行选项3"
            ],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "矩阵单选题",
            "type": "matrixradio",
            "id": "52d7a76fe092377673000035"
        },
        {
            "column_options": [
                "列选项1",
                "列选项2",
                "列选项3"
            ],
            "description": "",
            "display": {
                "column_random": true,
                "row_random": true
            },
            "exclusive": {
                "label": "",
                "status": true
            },
            "is_required": true,
            "max_column_num": 3,
            "max_row_num": 3,
            "min_column_num": 1,
            "min_row_num": 1,
            "number": 1,
            "page_id": "52d7a76fe092377673000037",
            "quote_ids": [],
            "row_options": [
                "行选项1",
                "行选项2",
                "行选项3"
            ],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "矩阵多选题",
            "type": "matrixcheckbox",
            "id": "52d7a770e092377673000038"
        },
        {
            "description": "这是一个打分题",
            "display": {
                "style": 'star' // 显示样式, 默认为星星
            },
            "is_required": true,
            "max_option": 5, // 打分最大值
            "min_option": 1, // 打分最小值
            "max_desc": '满意', // 最大分值描述
            "min_desc": '不满意', // 最小分值描述
            "number": 1,
            "options": [
                "选项1",
                "选项2",
                "选项3",
                "选项4"
            ],
            "step": 1, // 打分增值
            "page_id": "52d7a76fe092377673000028",
            "quote_ids": [],
            "skip_prompt": "",
            "survey_id": "52d7a76fe092377673000021",
            "title": "打分题",
            "type": "rating",
            "id": "52d7a76fe092377673000029"
        },
        {
            "description": "描述文本题",
            "number": 1,
            "page_id": "52d7a770e09237767300003b",
            "survey_id": "52d7a76fe092377673000021",
            "type": "desc",
            "id": "52d7a770e09237767300003c"
        }
    ]

## 2. 获取指定问题详情
    GET /surveys/:survey_id/questions/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "description": "这是一个单选题",
        "display": {
            "perline": 1,
            "random": false,
            "style": "radio"
        },
        "is_required": true,
        "number": 1,
        "options": [
            "选项1",
            "选项2",
            "选项3"
        ],
        "other": {
            "input": {
                "max": "100",
                "min": "2",
                "prompt": "请输入字符",
                "status": true,
                "type": "char"
            },
            "label": "其他选项",
            "status": true
        },
        "page_id": "52d7a76fe092377673000023",
        "quote_ids": [],
        "skip_prompt": "必答题",
        "survey_id": "52d7a76fe092377673000021",
        "title": "单选题",
        "type": "radio",
        "id": "52d7a76fe092377673000024"
    }

## 3. 创建问题
    POST /surveys/:survey_id/questions

**参数**

`page_id`
: _必选_ **String** - 指定该页创建问题

`type`
: _必选_ **String** - 指定问题类型

  * `type` - radio/checkbox/text/textarea/matrixradio/matrixcheckbox/description

`position`
: _必选_ **String** - 问题位置

  * `position` - top/bottom/above/below

`other_id`
: _如果position为above/below，必选_ **String** - 上一问题id

**请求**

{:.prettyprint}
    {
        "type": "radio",
        "position": "top",
        "description": "这是一个单选题",
        "display": {
            "perline": 1,
            "random": false,
            "style": "radio"
        },
        "is_required": true,
        "options": [
            "选项1",
            "选项2",
            "选项3"
        ],
        "other": {
            "input": {
                "max": "100",
                "min": "2",
                "prompt": "请输入字符",
                "status": true,
                "type": "char"
            },
            "label": "其他选项",
            "status": true
        },
        "page_id": "52d7a76fe092377673000023",
        "quote_ids": [],
        "skip_prompt": "必答题",
        "title": "单选题",
    }

**响应**

    Status: 201
    Location: http://api.surveymaster.com.cn/surveys/1/questions
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d7a76fe092377673000024"
        // 问题详情
    }

## 4. 修改指定的问题

    PATCH /surveys/:survey_id/questions/:id

**请求**

{:.prettyprint}
    {
        "id" : "52d7a76fe092377673000024",
        "type": "radio",
        "description": "这是一个单选题",
        "display": {
            "perline": 1,
            "random": false,
            "style": "radio"
        },
        "is_required": true,
        "options": [
            "选项1",
            "选项2",
            "选项3"
        ],
        "other": {
            "input": {
                "max": "100",
                "min": "2",
                "prompt": "请输入字符",
                "status": true,
                "type": "char"
            },
            "label": "其他选项",
            "status": true
        },
        "quote_ids": [],
        "skip_prompt": "必答题",
        "title": "单选题",
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d7a76fe092377673000024"
        // 问题详情
    }

## 5. 移动指定的问题
    PATCH /surveys/:survey_id/questions/:question_id/move

**参数**

`page_id`
: _必选_ **String** - 需要移动至某页的id

`position`
: _必选_ **String** - 问题位置

  * `position` - top/bottom/above/below

`other_id`
: _如果position为above/below，必选_ **String** - 上一问题id

**请求**

{:.prettyprint}
    {
        "page_id": "52d7a76fe092377673000023",
        "position": "above",
        "other_id": "52d7a76fe092377673000024"
    }

**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : "52d7a76fe092377673000024"
        // 问题详情
    }

## 6. 删除指定的问题
    DELETE /surveys/:survey_id/questions/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
