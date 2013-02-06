---
weight: 8
layout: default
category: surveymaster
title: 后置逻辑相关
language: cn
---

* TOC
{:toc}

## 1. 获取指定页的后置逻辑列表
	GET /surveys/pages/:page_id/postlogics

**响应**

    Status: 200 OK

{:.prettyprint}
    [/* 每一个数组元素就是一条逻辑，按先后顺序依次检查组内各逻辑，一旦存在符合条件的逻辑，检查即终止 */
	    {
		    "postlogic_id" : 1,
		    "url" : 'http://api.surveymaster.com.cn/surveys/pages/postlogics/1',
		    "goto" : 8,/* 跳转到第几页 */
		    "order_num" : 1,
		    "conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
			    {/* 单选题 */
				    "question_id" : 1,
				    "range" : [1,3]
			    },
			    {/* 多选题，选项包括了“其他” */
				    "question_id" : 2,
				    "range" : [2,-1],
				    "type" : "all/any/none"
			    }
		    ]
	    },

	    {
		    "postlogic_id" : 2,
		    "url" : 'http://api.surveymaster.com.cn/surveys/pages/postlogics/2',
		    "goto" : 10,/* 跳转到第几页 */
		    "order_num" : 2,
		    "conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
			    {/* 单行文本 */
				    "question_id" : 4,
				    "include" : ["admaster","好"],
				    "exclude" : ["不好"]
			    },
			    {/* 单行文本，只允许输入number */
				    "question_id" : 5,
				    "min" : 3/* 至少输入min个字符 */
			    },
			    {/* 多行文本 */
				    "question_id" : 6,
				    "include" : ["99click","好"],
				    "exclude" : ["不好"]
			    }
		    ]
	    }
    ]


## 2. 获取指定的后置逻辑（页逻辑）
	GET /surveys/pages/postlogics/:id

**响应**

    Status: 200 OK

{:.prettyprint}
    {
	    "postlogic_id" : 1,/* 后置逻辑的id（自增 全局唯一） */
	    "url" : 'http://api.surveymaster.com.cn/surveys/pages/postlogics/1',
	    "page_id" : 1,
	    "goto" : 10,/* 跳转到第几页 */
	    "order_num" : 1,
	    "conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		    {/* 单选题 */
			    "question_id" : 1,
			    "range" : [1,3]
		    },
		    {/* 多选题，选项包括了“其他” */
			    "question_id" : 2,
			    "range" : [2,-1],
			    "type" : "all/any/none"
		    },
		    {/* 多选题 */
			    "question_id" : 3,
			    "range" : [4,5],
			    "type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
		    },
		    {/* 单行文本 */
			    "question_id" : 4,
			    "include" : ["admaster","好"],
			    "exclude" : ["不好"]
		    },
		    {/* 单行文本，只允许输入number */
			    "question_id" : 5,
			    "min" : 3/* 至少输入min个字符 */
		    },
		    {/* 多行文本 */
			    "question_id" : 6,
			    "include" : ["99click","好"],
			    "exclude" : ["不好"]
		    }
	    ]
    }


## 3. 添加后置逻辑
	POST /surveys/pages/:page_id/postlogics

**请求**

{:.prettyprint}
    {
	    "goto" : 10,/* 跳转到第几页 */
	    "order_num" : 1,
	    "conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		    {/* 单选题 */
			    "question_id" : 1,
			    "range" : [1,3]
		    },
		    {/* 多选题，选项包括了“其他” */
			    "question_id" : 2,
			    "range" : [2,-1],
			    "type" : "all/any/none"
		    },
		    {/* 多选题 */
			    "question_id" : 3,
			    "range" : [4,5],
			    "type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
		    },
		    {/* 单行文本 */
			    "question_id" : 4,
			    "include" : ["admaster","好"],
			    "exclude" : ["不好"]
		    },
		    {/* 单行文本，只允许输入number */
			    "question_id" : 5,
			    "min" : 3/* 至少输入min个字符 */
		    },
		    {/* 多行文本 */
			    "question_id" : 6,
			    "include" : ["99click","好"],
			    "exclude" : ["不好"]
		    }
	    ]
    }

**响应**

    Status: 201 No Content
    Location: http://api.surveymaster.com.cn/surveys/pages/1/postlogics
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
	    "postlogic_id" : 1,/* 后置逻辑id(自增) */
	    /* 后置逻辑详情 */
    }


## 4. 修改指定的后置逻辑
	PATCH /surveys/pages/postlogics/:id

**请求**

{:.prettyprint}
    {
	    "goto" : 10,/* 跳转到第几页 */
	    "order_num" : 1,
	    "conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		    {/* 单选题 */
			    "question_id" : 1,
			    "range" : [1,3]
		    },
		    {/* 多选题，选项包括了“其他” */
			    "question_id" : 2,
			    "range" : [2,-1],
			    "type" : "all/any/none"
		    },
		    {/* 多选题 */
			    "question_id" : 3,
			    "range" : [4,5],
			    "type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
		    },
		    {/* 单行文本 */
			    "question_id" : 4,
			    "include" : ["admaster","好"],
			    "exclude" : ["不好"]
		    },
		    {/* 单行文本，只允许输入number */
			    "question_id" : 5,
			    "min" : 3/* 至少输入min个字符 */
		    },
		    {/* 多行文本 */
			    "question_id" : 6,
			    "include" : ["99click","好"],
			    "exclude" : ["不好"]
		    }
	    ]
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 5. 删除指定的后置逻辑
	DELETE /surveys/pages/postlogics/:id

**响应**

    Status: 204 No Content
    Link: http://api.surveymaster.com.cn/surveys/pages/1/postlogics; rel="postlogics"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
