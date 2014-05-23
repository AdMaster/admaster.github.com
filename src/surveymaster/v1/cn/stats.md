---
weight: 9
layout: default
category: surveymaster
title: 统计相关
language: cn
---

* TOC
{:toc}

## 1. 获取活跃问卷列表
    GET /stats/surveys/active

**响应**

{:.prettyprint}
    [
        {
            "answered_count": 2,
            "created_at": "2014-01-16T17:33:35+08:00",
            "deleted_at": null,
            "finished_count": 1,
            "label": "",
            "landing_count": 2,
            "qualified_count": 1,
            "title": "test_for_template",
            "updated_at": "2014-01-17T14:24:17+08:00",
            "user_id": "52cfa8cde092372bf6000001",
            "id": "52d7a76fe092377673000021",
            "logo": {
                "_id": "52d7a76fe092377673000022",
                "status": true,
                "url": ""
            }
        }
    ]


## 2. 获取问卷有效答案数量统计
    GET /stats/surveys/:survey_id/qualified

**参数**

`date`
: _可选_ **String** - today/30days/total

**响应**

{:.prettyprint}
    {
        "survey_id": "52d7a76fe092377673000021",
        "date": "today",
        "count": 1
    }

## 3. 获取问卷统计
    GET /stats/surveys/:id

**响应**

{:.prettyprint}
    {
        "answered_count": 2,
        "created_at": "2014-01-16T17:33:35+08:00",
        "deleted_at": null,
        "finished_count": 1,
        "foot": "",
        "freq_control": true,
        "head": "",
        "label": "",
        "landing_count": 2,
        "logo": {
            "status": true,
            "url": ""
        },
        "qualified_count": 1,
        "question_numbering": "none",
        "show_page_number": true,
        "show_progressbar": true,
        "title": "test_for_template",
        "updated_at": "2014-01-17T14:24:17+08:00",
        "user_id": "52cfa8cde092372bf6000001",
        "id": "52d7a76fe092377673000021",
        "questions": [
            {
                "description": "这是一个单选题",
                "display": {
                    "_id": "52d7a76fe092377673000027",
                    "perline": 1,
                    "random": false,
                    "style": "radio"
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "number": 1,
                "options": [
                    "选项1",
                    "选项2",
                    "选项3"
                ],
                "other": {
                    "_id": "52d7a76fe092377673000025",
                    "input": {
                        "_id": "52d7a76fe092377673000026",
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
                "page_number": 1,
                "quote_ids": [],
                "skip_prompt": "必答题",
                "survey_id": "52d7a76fe092377673000021",
                "title": "单选题",
                "type": "radio",
                "id": "52d7a76fe092377673000024"
            },
            {
                "description": "这是一个多选题",
                "display": {
                    "_id": "52d7a76fe09237767300002c",
                    "perline": 1,
                    "random": true
                },
                "exclusive": {
                    "_id": "52d7a76fe09237767300002d",
                    "label": "",
                    "status": true
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "max_option_num": 3,
                "min_option_num": 2,
                "number": 1,
                "options": [
                    "选项1",
                    "选项2",
                    "选项3",
                    "选项4"
                ],
                "other": {
                    "_id": "52d7a76fe09237767300002a",
                    "input": {
                        "_id": "52d7a76fe09237767300002b",
                        "max": "",
                        "min": "",
                        "prompt": "",
                        "status": true,
                        "type": "number"
                    },
                    "label": "",
                    "status": true
                },
                "page_id": "52d7a76fe092377673000028",
                "page_number": 2,
                "quote_ids": [],
                "skip_prompt": "",
                "survey_id": "52d7a76fe092377673000021",
                "title": "多选题",
                "type": "checkbox",
                "id": "52d7a76fe092377673000029"
            },
            {
                "description": "",
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "limit": {
                    "_id": "52d7a76fe092377673000030",
                    "max": null,
                    "min": null,
                    "prompt": "请输入邮箱",
                    "type": "date"
                },
                "number": 1,
                "page_id": "52d7a76fe09237767300002e",
                "page_number": 3,
                "quote_ids": [],
                "skip_prompt": "",
                "survey_id": "52d7a76fe092377673000021",
                "title": "单行文本题",
                "type": "text",
                "id": "52d7a76fe09237767300002f"
            },
            {
                "description": "",
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "limit": {
                    "_id": "52d7a76fe092377673000033",
                    "max": 1000,
                    "min": 1,
                    "prompt": ""
                },
                "number": 1,
                "page_id": "52d7a76fe092377673000031",
                "page_number": 4,
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
                    "_id": "52d7a76fe092377673000036",
                    "column_random": false,
                    "row_random": false
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "max_row_num": null,
                "min_row_num": null,
                "number": 1,
                "page_id": "52d7a76fe092377673000034",
                "page_number": 5,
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
                    "_id": "52d7a770e092377673000039",
                    "column_random": true,
                    "row_random": true
                },
                "exclusive": {
                    "_id": "52d7a770e09237767300003a",
                    "label": "",
                    "status": true
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "max_column_num": 3,
                "max_row_num": 3,
                "min_column_num": 1,
                "min_row_num": 1,
                "number": 1,
                "page_id": "52d7a76fe092377673000037",
                "page_number": 6,
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
            }
        ],
        "respondent_count": 1,
        "first_time": "2014-01-17T15:06:45+08:00",
        "last_time": "2014-01-17T15:06:45+08:00"
    }

## 4. 获取指定问题统计
    GET /stats/questions/:id

**响应**

{:.prettyprint}
    {
        "answered_count": 1,
        "description": "这是一个单选题",
        "display": {
            "_id": "52d7a76fe092377673000027",
            "perline": 1,
            "random": false,
            "style": "radio"
        },
        "for_panel": null,
        "for_track": 0,
        "is_required": true,
        "number": 1,
        "options": [
            "选项1",
            "选项2",
            "选项3"
        ],
        "options_stats": [
            {
                "option_id": 0,
                "option_name": "选项1",
                "count": 1
            },
            {
                "option_id": 1,
                "option_name": "选项2",
                "count": 0
            },
            {
                "option_id": 2,
                "option_name": "选项3",
                "count": 0
            },
            {
                "option_id": -1,
                "option_name": "其他选项",
                "count": 0
            }
        ],
        "other": {
            "_id": "52d7a76fe092377673000025",
            "input": {
                "_id": "52d7a76fe092377673000026",
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

## 5. 获取指定问题答案统计
    GET /stats/questions/:question_id/answers

**响应**

{:.prettyprint}
    [
        {
            "answered_page_ids": [
                "52d7a76fe092377673000023",
                "52d7a76fe09237767300002e",
                "52d7a76fe092377673000031",
                "52d7a76fe092377673000034",
                "52d7a76fe092377673000037",
                "52d7a770e09237767300003b"
            ],
            "city_code": "1000000000",
            "collector_id": "52d8d669e092370259000001",
            "created_at": "2014-01-17T15:06:45+08:00",
            "duration": 17,
            "ip": "127.0.0.1",
            "next_page_id": null,
            "passback": {},
            "qa": {
                "_id": "52d8d685e092375b9c000003",
                "duration": 3,
                "other": "",
                "question_id": "52d7a76fe092377673000024",
                "value": [
                    "0"
                ]
            },
            "qas": [
                {
                    "_id": "52d8d685e092375b9c000003",
                    "duration": 3,
                    "other": "",
                    "question_id": "52d7a76fe092377673000024",
                    "value": [
                        "0"
                    ]
                },
                {
                    "_id": "52d8d685e092375b9c000004",
                    "duration": 2,
                    "other": null,
                    "question_id": "52d7a76fe09237767300002f",
                    "value": [
                        "2014-01-03"
                    ]
                },
                {
                    "_id": "52d8d685e092375b9c000005",
                    "duration": 3,
                    "other": null,
                    "question_id": "52d7a76fe092377673000032",
                    "value": [
                        "safasfasfd"
                    ]
                },
                {
                    "_id": "52d8d685e092375b9c000006",
                    "duration": 4,
                    "other": null,
                    "question_id": "52d7a76fe092377673000035",
                    "value": [
                        "0.0",
                        "1.1",
                        "2.2"
                    ]
                },
                {
                    "_id": "52d8d685e092375b9c000007",
                    "duration": 6,
                    "other": null,
                    "question_id": "52d7a770e092377673000038",
                    "value": [
                        "2.2",
                        "0.2",
                        "0.1",
                        "1.1"
                    ]
                }
            ],
            "referer": null,
            "respondent_id": "52d8d670e092370259000009",
            "status": "finished",
            "survey_id": "52d7a76fe092377673000021",
            "track_datas": [
                {
                    "_id": "52d8d685e092375b9c000002",
                    "campaign_id": 12034,
                    "click": {},
                    "exposure": {
                        "placement_id": "200140946",
                        "creative_id": "0",
                        "action_time": "1389942382",
                        "times": "2",
                        "keyword": "0"
                    },
                    "other": {}
                }
            ],
            "updated_at": "2014-01-17T15:06:45+08:00",
            "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36",
            "worth": "qualified",
            "id": "52d8d685e092375b9c000001"
        }
    ]


## 5. 获取指定答案详情统计
    GET /stats/answers/:id

**响应**

{:.prettyprint}
    {
        "answered_page_ids": [
            "52d7a76fe092377673000023",
            "52d7a76fe09237767300002e",
            "52d7a76fe092377673000031",
            "52d7a76fe092377673000034",
            "52d7a76fe092377673000037",
            "52d7a770e09237767300003b"
        ],
        "city_code": "1000000000",
        "collector_id": "52d8d669e092370259000001",
        "created_at": "2014-01-17T15:06:45+08:00",
        "duration": 17,
        "ip": "127.0.0.1",
        "next_page_id": null,
        "passback": {},
        "referer": null,
        "respondent_id": "52d8d670e092370259000009",
        "status": "finished",
        "survey_id": "52d7a76fe092377673000021",
        "track_datas": [
            {
                "_id": "52d8d685e092375b9c000002",
                "campaign_id": 12034,
                "click": {},
                "exposure": {
                    "placement_id": "200140946",
                    "creative_id": "0",
                    "action_time": "1389942382",
                    "times": "2",
                    "keyword": "0"
                },
                "other": {}
            }
        ],
        "updated_at": "2014-01-17T15:06:45+08:00",
        "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1650.63 Safari/537.36",
        "worth": "qualified",
        "id": "52d8d685e092375b9c000001",
        "respondent": {
            "admckid": "1401151956201886732",
            "r_key": "cookie",
            "r_value": "1401151956201886732",
            "id": "52d8d670e092370259000009"
        },
        "qas": {
            "52d7a76fe092377673000024": {
                "_id": "52d8d685e092375b9c000003",
                "duration": 3,
                "other": "",
                "question_id": "52d7a76fe092377673000024",
                "value": [
                    "0"
                ]
            },
            "52d7a76fe09237767300002f": {
                "_id": "52d8d685e092375b9c000004",
                "duration": 2,
                "other": null,
                "question_id": "52d7a76fe09237767300002f",
                "value": [
                    "2014-01-03"
                ]
            },
            "52d7a76fe092377673000032": {
                "_id": "52d8d685e092375b9c000005",
                "duration": 3,
                "other": null,
                "question_id": "52d7a76fe092377673000032",
                "value": [
                    "safasfasfd"
                ]
            },
            "52d7a76fe092377673000035": {
                "_id": "52d8d685e092375b9c000006",
                "duration": 4,
                "other": null,
                "question_id": "52d7a76fe092377673000035",
                "value": [
                    "0.0",
                    "1.1",
                    "2.2"
                ]
            },
            "52d7a770e092377673000038": {
                "_id": "52d8d685e092375b9c000007",
                "duration": 6,
                "other": null,
                "question_id": "52d7a770e092377673000038",
                "value": [
                    "2.2",
                    "0.2",
                    "0.1",
                    "1.1"
                ]
            }
        },
        "questions": [
            {
                "description": "这是一个单选题",
                "display": {
                    "_id": "52d7a76fe092377673000027",
                    "perline": 1,
                    "random": false,
                    "style": "radio"
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "number": 1,
                "options": [
                    "选项1",
                    "选项2",
                    "选项3"
                ],
                "other": {
                    "_id": "52d7a76fe092377673000025",
                    "input": {
                        "_id": "52d7a76fe092377673000026",
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
                "page_number": 1,
                "quote_ids": [],
                "skip_prompt": "必答题",
                "survey_id": "52d7a76fe092377673000021",
                "title": "单选题",
                "type": "radio",
                "id": "52d7a76fe092377673000024"
            },
            {
                "description": "这是一个多选题",
                "display": {
                    "_id": "52d7a76fe09237767300002c",
                    "perline": 1,
                    "random": true
                },
                "exclusive": {
                    "_id": "52d7a76fe09237767300002d",
                    "label": "",
                    "status": true
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "max_option_num": 3,
                "min_option_num": 2,
                "number": 1,
                "options": [
                    "选项1",
                    "选项2",
                    "选项3",
                    "选项4"
                ],
                "other": {
                    "_id": "52d7a76fe09237767300002a",
                    "input": {
                        "_id": "52d7a76fe09237767300002b",
                        "max": "",
                        "min": "",
                        "prompt": "",
                        "status": true,
                        "type": "number"
                    },
                    "label": "",
                    "status": true
                },
                "page_id": "52d7a76fe092377673000028",
                "page_number": 2,
                "quote_ids": [],
                "skip_prompt": "",
                "survey_id": "52d7a76fe092377673000021",
                "title": "多选题",
                "type": "checkbox",
                "id": "52d7a76fe092377673000029"
            },
            {
                "description": "",
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "limit": {
                    "_id": "52d7a76fe092377673000030",
                    "max": null,
                    "min": null,
                    "prompt": "请输入邮箱",
                    "type": "date"
                },
                "number": 1,
                "page_id": "52d7a76fe09237767300002e",
                "page_number": 3,
                "quote_ids": [],
                "skip_prompt": "",
                "survey_id": "52d7a76fe092377673000021",
                "title": "单行文本题",
                "type": "text",
                "id": "52d7a76fe09237767300002f"
            },
            {
                "description": "",
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "limit": {
                    "_id": "52d7a76fe092377673000033",
                    "max": 1000,
                    "min": 1,
                    "prompt": ""
                },
                "number": 1,
                "page_id": "52d7a76fe092377673000031",
                "page_number": 4,
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
                    "_id": "52d7a76fe092377673000036",
                    "column_random": false,
                    "row_random": false
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "max_row_num": null,
                "min_row_num": null,
                "number": 1,
                "page_id": "52d7a76fe092377673000034",
                "page_number": 5,
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
                    "_id": "52d7a770e092377673000039",
                    "column_random": true,
                    "row_random": true
                },
                "exclusive": {
                    "_id": "52d7a770e09237767300003a",
                    "label": "",
                    "status": true
                },
                "for_panel": null,
                "for_track": 0,
                "is_required": true,
                "max_column_num": 3,
                "max_row_num": 3,
                "min_column_num": 1,
                "min_row_num": 1,
                "number": 1,
                "page_id": "52d7a76fe092377673000037",
                "page_number": 6,
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
            }
        ]
    }













