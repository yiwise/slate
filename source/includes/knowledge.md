# 专业版文本机器人知识库管理接口

## 查询知识列表接口

### 功能说明：

通过接口查询机器人知识库列表 

> JSON响应示例：

```json
{
  "code": 200,
  "data": {
    "number": 1,
    "pageSize": 20,
    "totalElements": 1,
    "pages": 1,
    "content": [
      {
        "createTime": "2020-04-01 16:27:00",
        "updateTime": "2020-04-01 16:27:00",
        "id": "5e8450544fce3e3e4405ae7a",
        "botId": 1,
        "knowledgeCategoryName": "测试类目",
        "title": "测试知识",
        "similarTitleList": ["测试类目相似句"],
        "answers": [
          {
            "gateways": [
              "ALL"
            ],
            "type": "PURE_TEXT",
            "content": "测试知识答案",
            "startTime": null,
            "endTime": null,
            "associatedKnowledgeList": []
          }
        ],
        "status": "ENABLED",
        "referenceExtraId": null
      }
    ]
  },
  "requestId": "SOUDQEFM",
  "resultMsg": "执行成功",
  "errorStackTrace": null
}

```

### 请求：

URL：https://brain.yiwise.com/apiOpen/knowledge/list

### 请求方法：

GET

### 请求参数:

| 参数名    | 类型   | 是否必须 | 默认值 | 描述 |
| --------- | ------ | -------- |--------- |---- |
| pageNum   | Integer | 否      | 1       | 页码 |
| pageSize | Integer | 否 | 20  | 每页数据条数|
|botId | Long | 是| | 机器人id|
| keyword | String | 否| | 对知识标题进行搜索 |

### 响应：

接口响应

| 字段名称  | 字段类型  | 字段描述      |
| --------- | --------  | ------------  |
| id        | String    | 问答知识id    |
| botId   | Long      | 机器人id      |
| knowledgeCategoryName | String | 知识类目名称 |
| title     | String    | 知识标题      |
| similarTitleList      | List\<String>  | 知识相似句列表|
| answers   | List      | 知识答案列表  |
| gateways  | List\<String> | 答案允许回复的渠道列表: <br>ALL=全部<br> WEB=web<br>WECHAT_PUBLIC=微信公众号<br>WECHAT_MINI_PROGRAM=微信小程序<br>WEIBO=微博       |
| type      | String    | 答案类型分为纯文本答案和富文本答案: <br>PURE_TEXT=纯文本<br>RICH_TEXT=富文本|
| content   | String    | 答案内容      |
| startTime | String    | 限制答案生效开始时间, 为空则表示没有限制|
| endTime   | String    | 限制答案生效结束时间, 为空则表示没有限制|
| associatedKnowledgeList | List | 答案关联的其他问答知识列表|
| status    | String    | 知识状态: ENABLED=启用, DISABLED=停用, DRAFT=草稿  |
| referenceExtraId | String | 知识关联引用的外部扩展id, 用于和业务方数据进行关联使用 |


## 添加知识接口

### 功能说明：
创建新的问答知识

> JSON请求示例:

```json
{
  "botId": 1,
  "knowledgeCategoryName": "待处理",
  "title": "测试添加知识",
  "similarTitleList": ["这是相似句"],
  "answers": [
    {
      "gateways": [
        "ALL"
      ],
      "type": "PURE_TEXT",
      "content": "测试添加知识答案",
      "startTime": null,
      "endTime": null,
      "associatedKnowledgeList": []
    }
  ],
  "status": "ENABLED"
}
```

> JSON响应示例：

```json
{
  "code": 200,
  "data": {
    "createTime": "2020-04-02 14:31:02",
    "updateTime": "2020-04-02 14:31:02",
    "id": "5e8586a763b52f68ed372c5c",
    "botId": 1,
    "knowledgeCategoryName": "待处理",
    "title": "测试添加知识",
    "similarTitleList": ["这是相似句"],
    "answers": [
      {
        "gateways": [
          "ALL"
        ],
        "type": "PURE_TEXT",
        "content": "测试添加知识答案",
        "startTime": null,
        "endTime": null,
        "associatedKnowledgeList": []
      }
    ],
    "status": "ENABLED",
    "referenceExtraId": null
  },
  "requestId": "WBVUYMHR",
  "resultMsg": "执行成功",
  "errorStackTrace": null
}
```


### 请求：

URL：https://brain.yiwise.com/apiOpen/knowledge/create

### 请求方法：

POST

### 请求参数:

| 参数名    | 类型   | 是否必须 |  描述 |
| --------- | ------ | -------- |---- |
| botId   | Long | 是      | 机器人id |
| knowledgeCategoryName | String | 是 | 机器人类目名称, 对于系统中不存在的类目, 会自动添加对应的类目信息|
| title | String    | 是    | 知识标题, 同一个机器人内需要保证唯一性|
| similarTitleList | List\<String> | 否| 知识相似句, 相似句也需要在机器人内保持唯一 |
| answers | List    | 是   | 机器人答案 |
| gateways  | List\<String> |是| 答案允许回复的渠道列表: <br>ALL=全部<br> WEB=web<br>WECHAT_PUBLIC=微信公众号<br>WECHAT_MINI_PROGRAM=微信小程序<br>WEIBO=微博       |
| type      | String    | 是    |答案类型分为纯文本答案和富文本答案: <br>PURE_TEXT=纯文本<br>RICH_TEXT=富文本|
| content   | String    | 是 |答案内容      |
| startTime | String    |否|  限制答案生效开始时间, 为空则表示没有限制, 时间格式为 **yyyy-MM-dd HH:mm:ss** |
| endTime   | String    | 否| 限制答案生效结束时间, 为空则表示没有限制, 时间格式为 **yyyy-MM-dd HH:mm:ss** |
|associatedKnowledgeList| List | 否| 答案关联的其他问答知识列表 |
| status    | String    | 是 | 知识状态: ENABLED=启用, DISABLED=停用, DRAFT=草稿 |
| referenceExtraId | String | 否 | 知识关联引用的外部扩展id, 用于和业务方数据进行关联使用 |

### 响应参数

| 字段名称  | 字段类型  | 字段描述      |
| --------- | --------  | ------------  |
| id        | String    | 问答知识id    |
| botId   | Long      | 机器人id      |
| knowledgeCategoryName | String | 知识类目名称 |
| title     | String    | 知识标题      |
| similarTitleList      | List\<String>  | 知识相似句列表|
| answers   | List      | 知识答案列表  |
| gateways  | List\<String> | 答案允许回复的渠道列表: <br>ALL=全部<br> WEB=web<br>WECHAT_PUBLIC=微信公众号<br>WECHAT_MINI_PROGRAM=微信小程序<br>WEIBO=微博       |
| type      | String    | 答案类型分为纯文本答案和富文本答案: <br>PURE_TEXT=纯文本<br>RICH_TEXT=富文本|
| content   | String    | 答案内容      |
| startTime | String    | 限制答案生效开始时间, 为空则表示没有限制|
| endTime   | String    | 限制答案生效结束时间, 为空则表示没有限制|
| associatedKnowledgeList | List | 答案关联的其他问答知识列表|
| status    | String    | 知识状态: ENABLED=启用, DISABLED=停用, DRAFT=草稿  |
| referenceExtraId | String | 知识关联引用的外部扩展id, 用于和业务方数据进行关联使用 |

## 更新问答知识

### 功能说明：
更新问答知识内容

 > JSON请求示例:

```json
{
    "createTime": "2020-04-02 14:31:02",
    "updateTime": "2020-04-02 14:31:02",
    "id": "5e8586a763b52f68ed372c5c",
    "botId": 1,
    "knowledgeCategoryName": "待处理",
    "title": "测试添加知识",
    "similarTitleList": ["这是相似句"],
    "answers": [
      {
        "gateways": [
          "ALL"
        ],
        "type": "PURE_TEXT",
        "content": "测试添加知识答案",
        "startTime": null,
        "endTime": null,
        "associatedKnowledgeList": []
      }
    ],
    "status": "ENABLED",
    "referenceExtraId": null
  }
```

> JSON响应示例:

```json
{
  "code": 200,
  "data": {
    "createTime": "2020-04-02 14:31:02",
    "updateTime": "2020-04-02 14:31:02",
    "id": "5e8586a763b52f68ed372c5c",
    "botId": 1,
    "knowledgeCategoryName": "待处理",
    "title": "测试添加知识",
    "similarTitleList": ["这是相似句"],
    "answers": [
      {
        "gateways": [
          "ALL"
        ],
        "type": "PURE_TEXT",
        "content": "测试添加知识答案",
        "startTime": null,
        "endTime": null,
        "associatedKnowledgeList": []
      }
    ],
    "status": "ENABLED",
    "referenceExtraId": null
  },
  "requestId": "WBVUYMHR",
  "resultMsg": "执行成功",
  "errorStackTrace": null
}
```


### 请求：

URL：https://brain.yiwise.com/apiOpen/knowledge/update

### 请求方法：

POST

### 请求参数:

| 参数名    | 类型   | 是否必须 |  描述 |
| --------- | ------ | -------- |---- |
| id        | String | 是 | 问答知识id |
| botId   | Long | 是      | 机器人id |
| knowledgeCategoryName | String | 是 | 机器人类目名称, 对于系统中不存在的类目, 会自动添加对应的类目信息|
| title | String    | 是    | 知识标题, 同一个机器人内需要保证唯一性|
| similarTitleList | List\<String> | 否| 知识相似句, 相似句也需要在机器人内保持唯一 |
| answers | List    | 是   | 机器人答案 |
| gateways  | List\<String> |是| 答案允许回复的渠道列表: <br>ALL=全部<br> WEB=web<br>WECHAT_PUBLIC=微信公众号<br>WECHAT_MINI_PROGRAM=微信小程序<br>WEIBO=微博       |
| type      | String    | 是    |答案类型分为纯文本答案和富文本答案: <br>PURE_TEXT=纯文本<br>RICH_TEXT=富文本|
| content   | String    | 是 |答案内容      |
| startTime | String    |否|  限制答案生效开始时间, 为空则表示没有限制, 时间格式为 **yyyy-MM-dd HH:mm:ss** |
| endTime   | String    | 否| 限制答案生效结束时间, 为空则表示没有限制, 时间格式为 **yyyy-MM-dd HH:mm:ss** |
|associatedKnowledgeList| List | 否| 答案关联的其他问答知识列表 |
| status    | String    | 是 | 知识状态: ENABLED=启用, DISABLED=停用, DRAFT=草稿 |
| referenceExtraId | String | 否 | 知识关联引用的外部扩展id, 用于和业务方数据进行关联使用 |

### 响应参数

| 字段名称  | 字段类型  | 字段描述      |
| --------- | --------  | ------------  |
| id        | String    | 问答知识id    |
| botId   | Long      | 机器人id      |
| knowledgeCategoryName | String | 知识类目名称 |
| title     | String    | 知识标题      |
| similarTitleList      | List\<String>  | 知识相似句列表|
| answers   | List      | 知识答案列表  |
| gateways  | List\<String> | 答案允许回复的渠道列表: <br>ALL=全部<br> WEB=web<br>WECHAT_PUBLIC=微信公众号<br>WECHAT_MINI_PROGRAM=微信小程序<br>WEIBO=微博       |
| type      | String    | 答案类型分为纯文本答案和富文本答案: <br>PURE_TEXT=纯文本<br>RICH_TEXT=富文本|
| content   | String    | 答案内容      |
| startTime | String    | 限制答案生效开始时间, 为空则表示没有限制|
| endTime   | String    | 限制答案生效结束时间, 为空则表示没有限制|
| associatedKnowledgeList | List | 答案关联的其他问答知识列表|
| status    | String    | 知识状态: ENABLED=启用, DISABLED=停用, DRAFT=草稿  |
| referenceExtraId | String | 知识关联引用的外部扩展id, 用于和业务方数据进行关联使用 |









