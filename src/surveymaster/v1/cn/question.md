---
weight: 4
layout: default
category: surveymaster
title: 问题相关
---

* TOC
{:toc}

#API - 问题相关（共6个）

## 1. 获取指定问卷的问题列表（用于后台管理）

    GET /surveys/:survey_id/pages/questions

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
        {
            "page_id" : 1,
            "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
            "questions" : [
                {
                    "id" : 1,/* 问题的id（自增 全局唯一） */
                    "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/1',
                    "survey_id" : 112,
                    "type" : 'radio',
                    "title" : "我是一个单选",
                    "desc" : "我是一个单选题啊单选题",
                    "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
                    "required" : {/* 必答 */
                        "status" : "on",/* 是否设为必答题 */
                        "prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
                    },
                },
                {
                    "id" : 2,
                    "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/2',
                    "survey_id" : 112,
                    "type" : "checkbox",
                    "title" : "我是一个多选",
                    "desc" : "我是一个牛13的多选题",
                    "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
                    "required" : {
                        "status" : "on",
                        "min" : 1,/* 必须选择至少required.min个选项 */
                        "max" : 3,/* 必须选择不超过required.max个选项 */
                        "prompt" : "这一项是必填的噢！"
                    },
                },
                {
                    "id" : 3,
                    "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/3',
                    "survey_id" : 112,
                    "type" : "text",
                    "title" : "我是一个单行文本",
                    "desc" : "我是一个单行文本",
                    "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
                    "required" : {
                        "status" : "on",
                        "prompt" : "这一项是必填的噢！"
                    }
                },
                {
                    "id" : 4,
                    "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/4',
                    "survey_id" : 112,
                    "type" : "textarea",
                    "title" : "我是一个多行文本",
                    "desc" : "我是一个多行文本",
                    "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
                    "required" : {
                        "status" : "on",
                        "prompt" : "这一项是必填的噢！"
                    }
                }
            ]
        },
        {
            "page_id" : 2,
            "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
            "questions" : [
            ]
        }
    ]


## 2. 获取指定页的问题列表

    GET /surveys/pages/:page_id/questions

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
        {
            "id" : 1,/* 问题的id（自增 全局唯一） */
            "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/1',
            "survey_id" : 112,
            "type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
            "title" : "我是一个单选",
            "desc" : "我是一个单选题啊单选题",
            "options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
                "option_1",
                "option_2",
                "option_3"
            ],
            "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
            "quote_question_ids" : [],/* 引用题的question_id数组（注意：引用题只能引用当前页之前的题） */
            "other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
                "status" : "on",/* 是否显示其他选项 */
                "label" : "其他",/* 自定义选项名称 */
                "input" : {/* 输入框 */
                    "status" : "on",/* 是否出现输入框 */
                    "type" : "char/number/email/url/date",/* ENUM char:字符串 number:数字 email:邮箱 url:链接 date:日期 */
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
        },

        {
            "id" : 2,
            "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/2',
            "survey_id" : 112,
            "type" : "checkbox",
            "title" : "我是一个多选",
            "desc" : "我是一个牛13的多选题",
            "options" : [
                "option_1",
                "option_2",
                "option_3"
            ],
            "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
            "quote_question_ids" : [],
            "other" : {
                "status" : "on",
                "label" : "其他",
                "input" : {
                    "status" : "on",
                    "type" : "char/number/email/url/date",
                    "min" : 1,
                    "max" : 10,
                    "prompt" : "当输入值不合法时，出现提示"
                }
            },
            "required" : {
                "status" : "on",
                "min" : 1,/* 必须选择至少required.min个选项 */
                "max" : 3,/* 必须选择不超过required.max个选项 */
                "prompt" : "这一项是必填的噢！"
            },
            "display" : {
                "perline" : 2,
                "random" : false
            },
            "exclusive" : {/* 排他选项（注意：这是一个特殊选项，其id为-2） */
                "status" : "on",/* 是否出现排他选项 */
                "text" : "以上都不是"/* 自定义选项名称 */
            }
        },

        {
            "id" : 3,
            "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/3',
            "survey_id" : 112,
            "type" : "text",
            "title" : "我是一个单行文本",
            "desc" : "我是一个单行文本",
            "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
            "quote_question_ids" : [],
            "limit" : {/* 输入限制 */
                "type" : "char/number/email/url/date",/* ENUM char:字符串 number:数字 email:邮箱 url:链接 date:日期 */
                "min" : 2,
                "max" : 20，
                "prompt" : "请输入2～20个字符"
            },
            "required" : {
                "status" : "on",
                "prompt" : "这一项是必填的噢！"
            }
        },

        {
            "id" : 4,
            "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/4',
            "survey_id" : 112,
            "type" : "textarea",
            "title" : "我是一个多行文本",
            "desc" : "我是一个多行文本",
            "logic_id" : 1,/* 逻辑id，0表示此题没有任何逻辑 */
            "quote_question_ids" : [1,2],
            "limit" : {
                "min" : 2,
                "max" : 20，
                "prompt" : "请输入2～20个字符"
            },
            "required" : {
                "status" : "on",
                "prompt" : "这一项是必填的噢！"
            }
        }
    ]


## 3. 创建问题

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
	    "id" : 1,/* 问题id(自增) */
	    /* 问题详情 */
    }


## 4. 获取指定问题详情

    GET /surveys/pages/questions/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id" : 1,/* 问题的id（自增 全局唯一） */
        "url" : 'http://api.surveymaster.com.cn/surveys/pages/questions/1',
        "survey_id" : 1,
        "type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
        "title" : "我是一个单选",
        "desc" : "我是一个单选题啊单选题",
        "options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
            "option_1",
            "option_2",
            "option_3"
        ],
        "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
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

## 5. 修改指定的问题

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


## 6. 删除指定的问题

    DELETE /surveys/pages/questions/:id

**响应**

    Status: 204 No Content
    Location: http://api.surveymaster.com.cn/surveys/pages/1/questions
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
