#任务完成电话信息查询接口

##获取已经完成任务电话号码接口
 
###功能说明：
 
 通过此接口可以获取指定任务中所有已经完成的电话号码
 
 >入参JSON实例
 
 ```
 
{
 	"customerGroupId": 1,
 	"robotCallJobId": 1,
 	"dialogFlowId": 2,
 	"resultStatuses": ["ANSWERED"],
 	"searchWords": "测试",
 	"intentLevels": ["A"],
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
                      "realIntentLevel": null,
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
 
 URL：https://crm.tanyibot.com/apiOpen/v1/callRecord/getCallRecordInfoList
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  customerGroupId| Long| 否 |分组ID| 100 |
  robotCallJobId| Long| 是 | 任务id| 1 |
  dialogFlowId| Long| 否 |话术id| 1 |
  resultStatuses| List| 否 |通话结果 (ANSWERED, "已接听"),(NO_ANSWER, "未接"),(BUSY, "占线"),(POWER_OFF, "关机"),(OUT_OF_SERVICE, "被叫停机"),(REFUSED, "拒接"),(VACANT_NUMBER, "空号"),(CAN_NOT_CONNECT, "无法接通"), (FROM_PHONE_ERROR, "主叫号码不可用"),(SYSTEM_ERROR, "外呼失败")| ["ANSWERED", "REFUSED"] |
  intentLevels| List| 否 |客户关注点 (A, "A级(较强)"),(B, "B级(一般)"),(C, "C级(无法判断)"),(D, "D级(很少)"),(E, "E级别(需要再次跟进)"),(F, "F级别(无需再次跟进)")| ["B", "C"] |
  searchWords| String| 否 |关键字搜索,支持电话号码、通话记录id、客户姓名| 0 |
  pageNum| Integer| 否 |第几页(默认为1)| 1 |
  pageSize| Integer| 否 |显示数量/页（默认为20），最大不能超过100| 10 |
  
  
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
  number| Integer | 第几页 |
  pageSize| Integer | 每页页面条数 |
  totalElements| Integer | 数据总条数 |
  pages| Integer | 页面总数 |
  callRecordId| Long | 通话ID |
  robotCallJobId| Long | 任务id |
  dialogFlowId| Long | 话术id |
  robotCallTaskId| Long | 子任务id（每个被叫电话为一个实例）|
  customerPersonId| Long |接收电话客户id|
  calledPhoneNumber| String | 被叫客户电话号码 |
  phoneNumberId| Long |电话线路id|
  resultStatus| String | 通话结果 (ANSWERED, "已接听"),(NO_ANSWER, "未接"),(BUSY, "占线"),(POWER_OFF, "关机"),(OUT_OF_SERVICE, "被叫停机"),(REFUSED, "拒接"),(VACANT_NUMBER, "空号"),(CAN_NOT_CONNECT, "无法接通"), (FROM_PHONE_ERROR, "主叫号码不可用"),(SYSTEM_ERROR, "外呼失败")|
  intentLevel| String | 意向等级, (A, "A级(较强)"),(B, "B级(一般)"),(C, "C级(无法判断)"),(D, "D级(很少)"),(E, "E级别(需要再次跟进)"),(F, "F级别(无需再次跟进)") |
  realIntentLevel| String | 真实意向等级 |
  customerConcern| List | 客户关注点  |
  fullAudioUrl| String | 完整音频地址 |
  customerAudioUrl| String | 客户音频地址 |
  analysisBasis| String | 说明 |
  startTime| String | 开始拨打时间 |
  chatDuration| Integer  | 通话时长 |
  chatRound| Integer | 通话轮次 |
  requestId| String | 请求Id |
  resultMsg| String | 响应说明 |

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
 		"realIntentLevel": null,
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
 		"robotCallJobId": 29
 	},
 	"requestId": "PSVILAEB",
 	"resultMsg": "执行成功",
 	"errorStackTrace": null
 }
 ```
 
###请求：
 
 URL：https://crm.tanyibot.com/apiOpen/v1/callRecord/callDetail
 
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
  realIntentLevel| String | 真是意向等级,  |
  customerConcern| List | 客户关注点,  |
  analysisBasis| String | 说明 |
  attributes| List | 参数 |
  requestId| String | 请求Id |
  resultMsg| String | 响应说明 |




