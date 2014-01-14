---
weight: 5
layout: default
category: surveymaster
title: 渠道相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定问卷的渠道列表
	GET /surveys/:survey_id/collectors

**响应**

    Status: 200 OK

**参数**

`sort`
: _可选_ **String** - 指定排序方式

  * `status` - 状态
  * `id`     - id (_默认_)

`direction`
: _可选_ **String** - 排序方式

  * `asc`  - 升序
  * `desc` - 降序 (_默认_)

{:.prettyprint}
  [
    {
      answered_count: 0,
      deadline_time: null,
      finished_count: 0,
      landing_count: 0,
      name: "New openlink",
      qualified_count: 0,
      sample_num: 111,
      status: true,
      survey_id: "52d4b062e092371da5000001",
      type: "openlink",
      id: "52d4b09ee092371da5000008",
      passwd: "a4$_B8addj_09jhk",
      freq_control: true,
      redirect: "baidu.com",
      cross: {
        _id: "52d4b09ee092371da500000b",
        callback: "",
        param:[],
        status: false
      },
      track_logic: {
        _id: "52d4b09ee092371da500000c",
        activity: {
          _id: "52d4b09ee092371da500000f",
          redirect: "",
          status: false
        },
        campaign:[],
        click: {
          _id: "52d4b09ee092371da500000e",
          redirect: "",
          status: false
        },
        exposure: {
          _id: "52d4b09ee092371da500000d",
          redirect: "",
          status: false
        },
        status: false
      },
      prologue: {
        _id: "52d4b09ee092371da5000009",
        content: "",
        status: false
      },
      epilogue: {
        _id: "52d4b09ee092371da5000009",
        content: "",
        status: false
      }
    }
  ]


## 2. 获取指定的渠道
	GET /surveys/:survey_id/collectors/:id

**响应**

    Status: 200 OK

{:.prettyprint}
  {
    answered_count: 0,
    deadline_time: null,
    finished_count: 0,
    landing_count: 0,
    name: "New openlink",
    qualified_count: 0,
    sample_num: 111,
    status: true,
    survey_id: "52d4b062e092371da5000001",
    type: "openlink",
    id: "52d4b09ee092371da5000008",
    passwd: "a4$_B8addj_09jhk",
    freq_control: true,
    redirect: "baidu.com",
    cross: {
      _id: "52d4b09ee092371da500000b",
      callback: "",
      param:[],
      status: false
    },
    track_logic: {
      _id: "52d4b09ee092371da500000c",
      activity: {
        _id: "52d4b09ee092371da500000f",
        redirect: "",
        status: false
      },
      campaign:[],
      click: {
        _id: "52d4b09ee092371da500000e",
        redirect: "",
        status: false
      },
      exposure: {
        _id: "52d4b09ee092371da500000d",
        redirect: "",
        status: false
      },
      status: false
    },
    prologue: {
      _id: "52d4b09ee092371da5000009",
      content: "",
      status: false
    },
    epilogue: {
      _id: "52d4b09ee092371da5000009",
      content: "",
      status: false
    }
  }

## 3. 添加渠道
	POST /surveys/:survey_id/collectors

**请求**

{:.prettyprint}
  {
    deadline_time: null, // 结束时间
    name: "New openlink",
    sample_num: 12, // 收集上限
    status: true, // 状态
    type: "openlink/edm", // 渠道类型
    redirect: "baidu.com", // 答题结束后跳转地址
    passwd: "a4$_B8addj_09jhk"
    cross: {
      callback: "",
      param:[],
      status: false
    },
    track_logic: {
      activity: {
        redirect: "",
        status: false
      },
      campaign:[],
      click: {
        redirect: "",
        status: false
      },
      exposure: {
        redirect: "",
        status: false
      },
      status: false
    },
    prologue: {
      content: "",
      status: false
    },
    epilogue: {
      content: "",
      status: false
    }
  }

**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
  {
    answered_count: 0,
    deadline_time: null,
    finished_count: 0,
    landing_count: 0,
    name: "New openlink",
    qualified_count: 0,
    sample_num: 111,
    status: true,
    survey_id: "52d4b062e092371da5000001",
    type: "openlink",
    id: "52d4b09ee092371da5000008",
    passwd: "a4$_B8addj_09jhk",
    freq_control: true,
    redirect: "baidu.com",
    cross: {
      _id: "52d4b09ee092371da500000b",
      callback: "",
      param:[],
      status: false
    },
    track_logic: {
      _id: "52d4b09ee092371da500000c",
      activity: {
        _id: "52d4b09ee092371da500000f",
        redirect: "",
        status: false
      },
      campaign:[],
      click: {
        _id: "52d4b09ee092371da500000e",
        redirect: "",
        status: false
      },
      exposure: {
        _id: "52d4b09ee092371da500000d",
        redirect: "",
        status: false
      },
      status: false
    },
    prologue: {
      _id: "52d4b09ee092371da5000009",
      content: "",
      status: false
    },
    epilogue: {
      _id: "52d4b09ee092371da5000009",
      content: "",
      status: false
    }
  }

## 4. 修改指定的渠道
	PATCH /surveys/:survey_id/collectors/:id

**请求**

{:.prettyprint}
  {
    deadline_time: null, // 结束时间
    name: "New openlink",
    sample_num: 12, // 收集上限
    status: true, // 状态
    redirect: "baidu.com", // 答题结束后跳转地址
    passwd: "a4$_B8addj_09jhk"
    cross: {
      callback: "",
      param:[],
      status: false
    },
    track_logic: {
      activity: {
        redirect: "",
        status: false
      },
      campaign:[],
      click: {
        redirect: "",
        status: false
      },
      exposure: {
        redirect: "",
        status: false
      },
      status: false
    },
    prologue: {
      content: "",
      status: false
    },
    epilogue: {
      content: "",
      status: false
    }
  }

**响应**

    Status: 201 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
  {
    answered_count: 0,
    deadline_time: null,
    finished_count: 0,
    landing_count: 0,
    name: "New openlink",
    qualified_count: 0,
    sample_num: 111,
    status: true,
    survey_id: "52d4b062e092371da5000001",
    type: "openlink",
    id: "52d4b09ee092371da5000008",
    passwd: "a4$_B8addj_09jhk",
    freq_control: true,
    redirect: "baidu.com",
    cross: {
      _id: "52d4b09ee092371da500000b",
      callback: "",
      param:[],
      status: false
    },
    track_logic: {
      _id: "52d4b09ee092371da500000c",
      activity: {
        _id: "52d4b09ee092371da500000f",
        redirect: "",
        status: false
      },
      campaign:[],
      click: {
        _id: "52d4b09ee092371da500000e",
        redirect: "",
        status: false
      },
      exposure: {
        _id: "52d4b09ee092371da500000d",
        redirect: "",
        status: false
      },
      status: false
    },
    prologue: {
      _id: "52d4b09ee092371da5000009",
      content: "",
      status: false
    },
    epilogue: {
      _id: "52d4b09ee092371da5000009",
      content: "",
      status: false
    }
  }


## 5. 删除指定的渠道
	DELETE /surveys/:survey_id/collectors/:id

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
