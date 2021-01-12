# 专业版文本机器人聊天接口

##聊天接口

###功能说明：

通过一问一答形式和机器人交互，多功能聊天接口较简单聊天接口功能更丰富，比如可以在每一轮对话前对外部变量进行更新等。 



###请求地址：

URL：https://openapi.tanyibot.com/apiOpen/v1/chat

###请求方法：

POST

###请求:

> 请求示例

```json
{
  "botId": 123,
  "text": "请问明天杭州的天气怎么样",
  "sessionId": null,
  "tag": "xxxx",
  "metaData": {
      "姓名": "张三",
      "城市": "杭州"
  }
}
```

请求参数说明

| 参数名    | 类型   | 是否必须 | 描述                                                         | 实例                     |
| --------- | ------ | -------- | ------------------------------------------------------------ | ------------------------ |
| text      | String | 是       | 用户输入                                                     | 我想查下明天的天气       |
| botId   | Long   | 是       | 机器人id                                                     | 38                       |
| sessionId | String | 否       | 会话ID，用于标识一个访问者的会话和保持上下文信息。<br/>对于一个新的访问者，首次调用Chat接口时无需传递此字段，机器人会开启一个会话，并在Chat接口的响应中返回该会话的SessionId。 | 5d1dc916c5efd96084bff32d |
| tag       | String | 否       | 可以传递任何内容参数，该参数将会直接在返回结果中透传回来。   |                          |
| metaData  | Map   | 否       | 用于在对话中向机器人传递外部变量，在机器人配置中可以使用此变量进行对话控制等，其中key为字符串类型的变量名称，值为字符串类型的 具体变量的值 |                          |

**需要注意的是，metaData里面的key，在机器人配置中的使用方式，比如metaData里面有key: 姓名, 在机器人中使用形式为 ${meta.姓名},所有的变量前面会添加meta.用于防止和系统内的其他词槽或者机器人内部变量冲突。**

###响应：

> JSON响应示例：

```
{
    "code":200,
    "data":{
        "chatId":2450,
        "sessionId":"5d1dc916c5efd96084bff32d",
        "messages":[
            {
                "text":{
                    "answer":"哈喽，人见人爱的我来啦，有啥我可以帮您的吗~",
                    "answerSource":"CHAT"
                },
                "recommends":[]
            }
        ]
    },
    "requestId":"TLDCOZPZ",
    "resultMsg":"执行成功",
    "errorStackTrace":null
}

```

接口响应

| 字段名称  | 字段类型 | 字段描述       |
| --------- | -------- | -------------- |
| chatId    | Long     | 本轮会话消息id |
| sessionId | String   | 本次会话id     |
| message   | Message  | 返回消息内容   |

### Message 结构

| 字段名称  | 字段类型  | 字段描述                                                   |
| --------- | --------- | ---------------------------------------------------------- |
| text      | Text      | 答案内容             |
| recommends | List<Recommend> | 推荐的答案列表 |

### Text结构

| 字段名称     | 字段类型 | 字段描述                                                     |
| ------------ | -------- | ------------------------------------------------------------ |
| answer       | String   | 回复内容                                                     |
| answerSource | String   | 回复来源: <br>CHAT=闲聊<br> KNOWLEDGE=问答知识,<br>DIALOG_FLOW=多轮对话<br>UNKNOWN=拒答回复<br>CLARIFICATION=智能澄清<br>KNOWLEDGE_RECOMMEND=问答知识推荐 |

### Recommend结构

| 字段名称       | 字段类型 | 字段描述 |
| -------------- | -------- | -------- |
| knowledgeId    | String   | 知识id   |
| knowledgeTitle | String   | 知识标题 |



