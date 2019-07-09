#任务完成电话信息查询接口

##获取已经完成任务电话号码接口

###功能说明：

 通过此接口可以获取指定任务中所有已经完成的电话号码

 >入参JSON实例

 ```
 
{
 	"robotCallJobId": 1,
 	"dialogFlowId": 2,
 	"resultStatuses": ["ANSWERED"],
 	"intentLevels": ["A"],
 	"hangupBy":"REMOTE_HANGUP",
 	"realIntent": true,
 	"calledPhoneNumber":"15364736473",
 	"callRecordId": 145213,
 	"customerPersonName": "张三",
 	"customerConcern":["公司位置","交通"],
 	"readStatus": "NOT_READ",
 	"chatDurationMin": 1,
 	"chatDurationMax": 3,
 	"lastCallRecord": true,
 	"redialTimes": 2,
 	"pageSize": 20,
 	"pageNum": 1
}
 
 ```

 >JSON响应实例：

 ```
 {
           "code": 200,
           "data": {
               "number": 1,
               "pageSize": 20,
               "totalElements": 4,
               "pages": 1,
               "content": [
                   {
                       "hangupBy": "REMOTE_HANGUP",
                       "callRecordId": 47,
                       "tenantId": 1,
                      "robotCallJobId": 50,
                      "dialogFlowId": 4,
                      "robotCallTaskId": 4,
                      "customerPersonId": 5,
                      "calledPhoneNumber": "18817501728",
                      "phoneNumberId": 0,
                      "resultStatus": "ANSWERED",
                      "intentLevel": "A",
                      "intentLevelName": "很好",
                      "realIntentLevel": null,
                      "realIntentLevelName":"很好",
                      "intentLevelTagId": 0,
                      "customerConcern": [
                        "价格","位置"
                       ],
                       "fullAudioUrl": "https://ai-call-platform.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId50/OUZAXBCB__TaskId_4/ai_user.wav",
                       "customerAudioUrl": "https://ai-call-platform.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId50/OUZAXBCB__TaskId_4/user.wav",
                       "analysisBasis": "",
                       "startTime": "2018-08-04 11:57:33",
                       "chatDuration": 93,
                       "chatRound": 16,
                       "readStatus": "NOT_READ",
                       "callDetailList": [
                           {
                               "text":"喂，您好, （停顿2s），您好，想问下您位于江北纬七路隧道附近，均价17000的高端商业综合体，我可以给您介绍一下吗？",
                               "type":"ROBOT",
                               "callDetailId": 1
                           },
                           {
                               "text":"嗯",
                               "type":"PERSON",
                               "callDetailId": 2
                           }
                       ]
                   }
               ]
           },
           "requestId": "YXDXFDSC",
           "resultMsg": "获取成功",
           "errorStackTrace": null
       }
 ```

###请求：

 URL：https://openapi.tanyibot.com/apiOpen/v1/callRecord/getCallRecordInfoList

###请求方法：

 POST


###请求参数:

 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
 hangupBy | String | 否 | 挂机状态 | REMOTE_HANGUP 
  customerGroupId| Long| 否 |分组ID| 100 
  robotCallJobId| Long| 是 | 任务id| 1 
  dialogFlowId| Long| 否 |话术id| 1 
  resultStatuses| List| 否 |通话结果 (ANSWERED, "已接听"),(NO_ANSWER, "未接"),(BUSY, "占线"),(POWER_OFF, "关机"),(OUT_OF_SERVICE, "被叫停机"),(REFUSED, "拒接"),(VACANT_NUMBER, "空号"),(CAN_NOT_CONNECT, "无法接通"), (FROM_PHONE_ERROR, "主叫号码不可用"),(SYSTEM_ERROR, "外呼失败")| ["ANSWERED", "REFUSED"] 
  intentLevels| List| 否 |客户关注点 (A, "A级(较强)"),(B, "B级(一般)"),(C, "C级(无法判断)"),(D, "D级(很少)"),(E, "E级别(需要再次跟进)"),(F, "F级别(无需再次跟进)")| ["B", "C"] 
  calledPhoneNumber| String| 否 |被叫电话号码| 15364736473 
  callRecordId| Long| 否 |通话记录id| 145213 
  customerPersonName| String| 否 |客户姓名| 张三 
  realIntent| boolean| 否 |是否人工标注意向| true 
  customerConcern| List| 否 |客户关注点| ["公司位置","交通"] 
  readStatus| String| 否 |查看状态| 未读 NOT_READ 已读 HAS_READ 
  chatDurationMin| Long| 否 |最小通话时长| 1 
  chatDurationMax| Long| 否 |最大通话时长| 3 
  lastCallRecord| boolean| 否 |是否去重查询| 如此处为true 条件只有 robotCallJobId resultStatuses intentLevels chatDurationMin chatDurationMax redialTimes 有效
  redialTimes| Long| 否 |自动重播次数| 3 此条件只在lastCallRecord为true时生效
  pageNum| Integer| 否 |第几页(默认为1)| 1 
  pageSize| Integer| 否 |显示数量/页（默认为20），最大不能超过100| 10 

###响应：

 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 
 hangupBy |String | 挂机状态 
  number| Integer | 第几页 
  pageSize| Integer | 每页页面条数 
  totalElements| Integer | 数据总条数 
  pages| Integer | 页面总数 
  callRecordId| Long | 通话ID 
  robotCallJobId| Long | 任务id 
  dialogFlowId| Long | 话术id 
  robotCallTaskId| Long | 子任务id（每个被叫电话为一个实例）
  customerPersonId| Long |接收电话客户id
  calledPhoneNumber| String | 被叫客户电话号码 
  phoneNumberId| Long |电话线路id
  resultStatus| String | 通话结果 (ANSWERED, "已接听"),(NO_ANSWER, "未接"),(BUSY, "占线"),(POWER_OFF, "关机"),(OUT_OF_SERVICE, "被叫停机"),(REFUSED, "拒接"),(VACANT_NUMBER, "空号"),(CAN_NOT_CONNECT, "无法接通"), (FROM_PHONE_ERROR, "主叫号码不可用"),(SYSTEM_ERROR, "外呼失败")
  intentLevel| String | 意向等级, (A, "A级(较强)"),(B, "B级(一般)"),(C, "C级(无法判断)"),(D, "D级(很少)"),(E, "E级别(需要再次跟进)"),(F, "F级别(无需再次跟进)") 
  intentLevelName | String | 意向标签名称 
  realIntentLevel| String | 真实意向等级 
  realIntentLevelName| String | 真实意向标签名称 
  intentLevelTagId | Long | 意向分类标签id 
  customerConcern| List | 客户关注点  
  fullAudioUrl| String | 完整音频地址 
  customerAudioUrl| String | 客户音频地址 
  analysisBasis| String | 说明 
  startTime| String | 开始拨打时间 
  chatDuration| Integer  | 通话时长 
  chatRound| Integer | 通话轮次 
  redialTimes| Integer | 自动重播次数
  requestId| String | 请求Id 
  resultMsg| String | 响应说明 

##获取一个通话的详情接口

###功能说明：

 通过此接口可以获取指定通话的详细信息

 >JSON响应实例：

 ```
 {
 	"code": 200,
 	"data": {
 		"callRecordId": 1,
 		"customerAudioUrl": null,
 		"startTime": "2018-10-02T16:54:08",
 		"endTime": "2018-10-02T16:54:08",
 		"chatRound": 0,
 		"chatDuration": 0,
 		"customerPerson": {
 			"customerPersonId": 2006007,
 			"creationTime": "2018-10-01 16:39",
 			"tenantId": 1,
 			"customerGroupId": 181,
 			"name": "空号",
 			"phoneNumber": "18673125007",
 			"wechatNumber": null,
 			"source": "UPLOADED_BY_YOURSELF",
 			"gender": "UNKNOWN",
 			"properties": {"ss":"test"},
 			"lastFollowTime": "2018-10-01 16:39:29",
 			"lastChatDuration": 0,
 			"lastStartTime": "2018-10-02 17:20:01",
 			"lastIntentLevel": "E",
 			"lastDialStatus": "CAN_NOT_CONNECT",
 			"assignTime": "2018-10-01 16:39:29",
 			"customerGroupName": "研发"
 		},
 		"resultStatus": "VACANT_NUMBER",
 		"intentLevel": "F",
 		"intentLevelName":"一般",
 		"realIntentLevel": null,
 		"realIntentLevelName":"一般",
 		"intentLevelTagId":0,
 		"customerConcern": ["价格", "位置"],
 		"fullAudioUrl": "https://ai-call-platform-daily.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId17/YKUYXGLL_TaskId_1305098/early_media.wav",
 		"analysisBasis": "空号",
 		"callDetailList": [{
 				"text": "喂，您好, （停顿2s），您好，想问下您位于江北纬七路隧道附近，均价17000的高端商业综合体，我可以给您介绍一下吗？",
 				"type": "ROBOT",
 				"callDetailId": 1
 			},
 			{
 				"text": "嗯",
 				"type": "PERSON",
 				"callDetailId": 2
 			}
 		],
 		"robotCallJobId": 29,
    "redialTimes": 0
 	},
 	"requestId": "PSVILAEB",
 	"resultMsg": "执行成功",
 	"errorStackTrace": null
 }
 ```

###请求：

 URL：https://openapi.tanyibot.com/apiOpen/v1/callRecord/callDetail

###请求方法：

 GET

###请求参数:

 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  callRecordId| Integer| 是 | 任务实例id| 1 |  

###响应：

 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
  callDetailList| List | 对话内容 |
  callRecordId| Long | 记录id |
  robotCallJobId| Long | 任务id |
  fullAudioUrl| String | 完整音频地址 |
  customerAudioUrl| String | 客户音频地址 |
  startTime| String | 开始拨打时间 |
  endTime| String | 结束拨打时间 |
  chatDuration| Integer  | 通话时长 |
  chatRound| Integer | 通话轮次 |
  resultStatus| String | 通话结果 (ANSWERED, "已接听"),(NO_ANSWER, "未接"),(BUSY, "占线"),(POWER_OFF, "关机"),(OUT_OF_SERVICE, "被叫停机"),(REFUSED, "拒接"),(VACANT_NUMBER, "空号"),(CAN_NOT_CONNECT, "无法接通"), (FROM_PHONE_ERROR, "主叫号码不可用"),(SYSTEM_ERROR, "外呼失败")|
  intentLevel| String | 意向等级, (A, "A级(较强)"),(B, "B级(一般)"),(C, "C级(无法判断)"),(D, "D级(很少)"),(E, "E级别(需要再次跟进)"),(F, "F级别(无需再次跟进)") |
  intentLevelName| String | 意向标签名称 |
  realIntentLevel| String | 真实意向等级,  |
  realIntentLevelName | String | 真实意向标签名称 |
  intentLevelTagId | Long | 意向分类标签id |
  customerConcern| List | 客户关注点,  |
  analysisBasis| String | 说明 |
  attributes| List | 参数 |
  requestId| String | 请求Id |
  resultMsg| String | 响应说明 |

##获取未完成任务电话号码接口

###功能说明：

 通过此接口可以获取指定任务中所有未完成呼叫任务的电话号码

> > JSON响应实例：
>
> ```
>  {
>           "code": 200,
>           "data": {
>               "number": 1,
>               "pageSize": 20,
>               "totalElements": 1,
>               "pages": 1,
>               "content": [
>                   {
>                       "robotCallTaskId": 3033235,
>                       "customerPersonId": 7170228,
>                       "customerPersonName": "不要拨打",
>                       "calledPhoneNumber": "156****7777",
>                       "customerPersonGroupName": "",
>                       "status": "NOT_STARTED",
>                       "inWhiteList": false,
>                       "properties": {
>                           "尾号数_单个": "1"
>                       },
>                       "inShareWhiteList": null
>                   }
>               ]
>           },
>           "requestId": "PDRAROJB",
>           "resultMsg": "执行成功",
>           "errorStackTrace": null
>       }
> ```
>
> 

###请求：

 URL：https://openapi.tanyibot.com/apiOpen/v1/callRecord/toBeCalledList

###请求方法：

 get

###请求参数:

| 参数名            | 类型    | 是否必须 | 描述                                                         | 实例        |
| ----------------- | ------- | -------- | ------------------------------------------------------------ | ----------- |
| pageNum           | Integer | 否       | 第几页，默认第一页                                           | 1           |
| pageSize          | Integer | 否       | 页面大小，默认20条                                           | 20          |
| robotCallJobId    | Integer | 是       | 任务id,必填                                                  | 1           |
| calledPhoneNumber | String  | 否       | 联系方式                                                     | 13266666666 |
| taskStatus        | String  | 否       | 呼叫状态,(NOT_STARTED,"未开始"),(IN_PROCESS,"进行中"),(COMPLETED,"已完成"),(RETRY,"重试拨打"),(AUTO_RETRY,"自动重拨"),(IN_CACHE,"缓存中"); | NOT_STARTED |

###响应：

| 参数名                  | 类型                | 描述                                                         |
| ----------------------- | ------------------- | ------------------------------------------------------------ |
| code                    | integer             | 响应码                                                       |
| number                  | Integer             | 第几页                                                       |
| pageSize                | Integer             | 每页页面条数                                                 |
| totalElements           | Integer             | 数据总条数                                                   |
| pages                   | Integer             | 页面总数                                                     |
| robotCallTaskId         | Long                | 任务id                                                       |
| customerPersonId        | Long                | 客户id                                                       |
| customerPersonName      | String              | 客户名称                                                     |
| calledPhoneNumber       | String              | 联系电话                                                     |
| customerPersonGroupName | String              | 客户所在组名称                                               |
| status                  | String              | 呼叫状态，NOT_STARTED(0, "未开始"), IN_PROCESS(1, "进行中"), COMPLETED(2, "已完成"), RETRY(3, "重试拨打"), AUTO_RETRY(4, "自动重拨"), IN_CACHE(5, "缓存中"); |
| inWhiteList             | Boolean             | 是否白名单，true代表在，false不在                            |
| inShareWhiteList        | Boolean             | 是否在共享白名单，true代表在，false代表不在                  |
| properties              | Map<String, String> | 自定义变量                                                   |
| requestId               | String              | 请求Id                                                       |
| resultMsg               | String              | 响应说明                                                     |

##从未呼客户列表中删除单个客户

###功能说明：

 通过此接口可以从未呼客户列表中删除单个客户

> JSON响应实例：

```
{
          "code": 200,
          "data": null,
          "requestId": "WUEAPMJO",
          "resultMsg": "删除成功",
          "errorStackTrace": null
      }
```

###请求：

 URL：https://openapi.tanyibot.com/apiOpen/v1/callRecord/deleteRobotCallTask

###请求方法：

 post

###请求参数:

| 参数名          | 类型 | 是否必须 | 描述                 | 实例 |
| --------------- | ---- | -------- | -------------------- | ---- |
| robotCallTaskId | Long | 是       | 需要删除的呼叫任务Id | 1    |

###响应：

| 参数名    | 类型    | 描述     |
| --------- | ------- | -------- |
| code      | integer | 响应码   |
| data      | Long    | 记录id   |
| requestId | String  | 请求Id   |
| resultMsg | String  | 响应说明 |

##从未呼客户列表中批量删除待呼客户名单

###功能说明：

 通过此接口可以从未呼客户列表中批量删除待呼客户名单

> JSON响应实例：

```
{
          "code": 200,
          "data": null,
          "requestId": "WUEAPMJO",
          "resultMsg": "删除成功",
          "errorStackTrace": null
      }
```

###请求：

 URL：https://openapi.tanyibot.com/apiOpen/v1/callRecord/deleteRobotCallTaskList

###请求方法：

 GET

###请求参数:

| 参数名            | 类型    | 是否必须 | 描述                                                         | 实例            |
| ----------------- | ------- | -------- | ------------------------------------------------------------ | --------------- |
| robotCallJobId    | Integer | 是       | 任务id                                                       | 1               |
| robotCallTaskIds  | List    | 否       | 删除子任务id 此字段不为空时下面筛选条件无效                  | 3033729,3033719 |
| calledPhoneNumber | String  | 否       | 联系方式                                                     | 13266666666     |
| taskStatus        | String  | 否       | 呼叫状态,(NOT_STARTED,"未开始"),(IN_PROCESS,"进行中"),(COMPLETED,"已完成"),(RETRY,"重试拨打"),(AUTO_RETRY,"自动重拨"),(IN_CACHE,"缓存中"); | IN_PROCESS      |

###响应：

| 参数名    | 类型    | 描述     |
| --------- | ------- | -------- |
| code      | integer | 响应码   |
| data      | Long    | 记录id   |
| requestId | String  | 请求Id   |
| resultMsg | String  | 响应说明 |

