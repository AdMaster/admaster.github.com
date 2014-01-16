---
weight: 4
layout: default
category: surveymaster
title: 问题相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定问卷的问题列表
    GET /surveys/:survey_id/questions

**参数**

`page_id`
: _可选_ **String** - 指定排序方式

  * `page_id` - 指定只显示该page的questions

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

## 4. 创建问题

    POST /surveys/pages/:page_id/questions

**请求**

{:.prettyprint}
    {
        "type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
        "title" : "我是一个单选",
        "desc" : "我是一个单选题啊单选题",
        "options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
            "option_1",
            "option_2",
            "option_3"
        ],
        "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
        "quote_question_ids" : [1],
        "other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
            "status" : "on",/* 是否显示其他选项 */
            "label" : "其他",/* 自定义选项名称 */
            "input" : {/* 输入框 */
                "status" : "on",/* 是否出现输入框 */
                "type" : "char/number/email/url/date",
                "min" : 1,/* 允许输入的最少字符数 */
                "max" : 10,/* 允许输入的最多字符数 */
                "prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
            }
        },
        "required" : {/* 必答 */
            "status" : "on",/* 是否设为必答题 */
            "prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
        },
        "display" : {/* 显示相关 */
            "style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为on时，other的前端实现要与此设置保持一致) */
            "perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
            "random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
        }
    }

**响应**

    Status: 201 No Content
    Location: http://api.surveymaster.com.cn/surveys/1/questions
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
	    "question_id" : 1,/* 问题id(自增) */
	    /* 问题详情 */
    }

## 6. 修改指定的问题

    PATCH /surveys/pages/questions/:id

**请求**

{:.prettyprint}
    {
        "type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本(注意：允许改题型) */
        "title" : "我是一个单选",
        "desc" : "我是一个单选题啊单选题",
        "options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
            "option_1",
            "option_2",
            "option_3"
        ],
        "quote_question_ids" : [],
        "other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
            "status" : "on",/* 是否显示其他选项 */
            "label" : "其他",/* 自定义选项名称 */
            "input" : {/* 输入框 */
                "status" : "on",/* 是否出现输入框 */
                "type" : "char/number/email/url/date",
                "min" : 1,/* 允许输入的最少字符数 */
                "max" : 10,/* 允许输入的最多字符数 */
                "prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
            }
        },
        "required" : {/* 必答 */
            "status" : "on",/* 是否设为必答题 */
            "prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
        },
        "display" : {/* 显示相关 */
            "style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为on时，other的前端实现要与此设置保持一致) */
            "perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
            "random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
        }
    }


**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 7. 删除指定的问题

    DELETE /surveys/pages/questions/:id

**响应**

    Status: 204 No Content
    Location: http://api.surveymaster.com.cn/surveys/pages/1/questions
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
