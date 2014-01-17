---
weight: 6
layout: default
category: surveymaster
title: 答案相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定问卷的答案列表
    GET /surveys/:survey_id/answers

**参数**

`collector_id`
: _可选_ **String** - 指定渠道id进行过滤

`per_page`
: _可选_ **integer** - 每页显示记录数，默认30

`page`
: _可选_ **integer** - 页数

**响应**

    Status: 200 OK

{:.prettyprint}
    [
        {
            "collector_id": "52d8d669e092370259000001",
            "created_at": "2014-01-17T15:06:27+08:00",
            "respondent_id": "52d8d670e092370259000009",
            "status": "finished",
            "survey_id": "52d7a76fe092377673000021",
            "updated_at": "2014-01-17T15:06:45+08:00",
            "worth": "qualified",
            "id": "52d8d673e09237025900000a",
            "qas": [
                {
                    "_id": "52d8d685e09237025900001f",
                    "duration": 3,
                    "other": "",
                    "question_id": "52d7a76fe092377673000024",
                    "value": [
                        "0"
                    ]
                },
                {
                    "_id": "52d8d685e092370259000020",
                    "duration": 2,
                    "other": null,
                    "question_id": "52d7a76fe09237767300002f",
                    "value": [
                        "2014-01-03"
                    ]
                },
                {
                    "_id": "52d8d685e092370259000021",
                    "duration": 3,
                    "other": null,
                    "question_id": "52d7a76fe092377673000032",
                    "value": [
                        "safasfasfd"
                    ]
                },
                {
                    "_id": "52d8d685e092370259000022",
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
                    "_id": "52d8d685e092370259000023",
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
            "track_datas": [
                {
                    "_id": "52d8d685e092370259000024",
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
            ]
        }
    ]


## 3. 获取指定答案的详情
    GET /surveys/:survey_id/answers/:id

**响应**

    Status: 200 OK

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
        "created_at": "2014-01-17T15:06:27+08:00",
        "duration": 17,
        "ip": "127.0.0.1",
        "passback": {},
        "qas": [
            {
                "duration": 3,
                "other": "",
                "question_id": "52d7a76fe092377673000024",
                "value": [
                    "0"
                ]
            },
            {
                "duration": 2,
                "other": null,
                "question_id": "52d7a76fe09237767300002f",
                "value": [
                    "2014-01-03"
                ]
            },
            {
                "duration": 3,
                "other": null,
                "question_id": "52d7a76fe092377673000032",
                "value": [
                    "safasfasfd"
                ]
            },
            {
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
        "id": "52d8d673e09237025900000a"
    }

## 4. 编辑指定答卷中某一个问题的答案（注意：特殊功能，使用者非受访者本人）
    PATCH /surveys/:survey_id/answers/:answer_id/qas/:id

**请求**

{:.prettyprint}
    {
        "value" : ["-1"], // -1代表"其他"选项
    }


**响应**

    Status: 201
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "duration": 3,
        "other": "",
        "question_id": "52d7a76fe092377673000024",
        "value": [
            "-1"
        ]
    }

## 5. 删除指定答案
    DELETE /surveys/:survey_id/answers/:id

**响应**

    Status: 204
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 6. 删除指定渠道的所有答案
    DELETE /surveys/:survey_id/collectors/:collector_id/answers

**响应**

    Status: 204
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
