#任务信息查询接口

##获取任务列表接口

###功能说明：

通过此接口可以获取指定公司的任务列表

>JSON响应实例：

```
{
  "code": 200,
  "data": {
    "number": 1,
    "pageSize": 20,
    "totalElements": 1,
    "pages": 1,
    "content": [{
      "robotCallJobId": 1,
      "name": "dialog测试",
      "status": "TERMINATE",
      "completedTask": 2157,
      "taskCallTotal": 166,
      "creationTime": "2018-09-26 18:07",
      "createdByUserName": null,
      "organizationName": null
    }]
  },
  "requestId": "OTMAGZFW",
  "resultMsg": "创建成功",
  "errorStackTrace": null
}
```

###请求：

URL：http://robot.yiwise.cn/openapi/v1/task/getTasks

###请求方法：

GET

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 taskName| String| 否 |任务名称| 测试API任务 |
 status| Integer| 否 | 任务状态,NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中"),COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停"),TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中");| 1 |
 pageNum| Integer| 否 | 第几页,默认1| 1 |
 pageSize| Integer| 否 | 页面大小,选填,默认20| 10 |



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 number| Integer | 第几页 |
 pageSize| Integer | 每页页面条数 |
 totalElements| Integer | 数据总条数 |
 pages| Integer | 页面总数 |
 robotCallJobId| Integer | 任务id |
 name| String | 任务名称 |
 completedTask| Integer | 完成的任务 |
 taskCallTotal| Integer | 任务总数 |
 creationTime| String | 创建时间 |
 createdByUserName| String | 创建人 |
 organizationName| String | 组织 |
 status| Integer | 任务状态, NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中"),COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停"),TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中");| 1 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

##获取任务详情接口

###功能说明：

通过此接口可以获取指定任务的详细信息

>JSON响应实例：

```
{
	"code": 200,
	"data": {
		"robotCallJob": {
			"robotCallJobId": 1,
			"tenantId": 1,
			"dialogFlowId": 1,
			"name": "dialog测试",
			"mode": "MANUAL",
			"robotCount": 12,
			"smsTemplateId": null,
			"phoneType": "LANDLINE",
			"dailyStartTime": "15:08:31",
			"dailyEndTime": "15:08:36",
			"inactiveStartTime": "00:00:00",
			"inactiveEndTime": "00:00:00",
			"description": null,
			"wechatAlertLevel": [],
			"smsAlertLevel": [],
			"alertUsers": [],
			"wechatSendMethod": "SENDTOALL",
			"status": "TERMINATE",
			"startTime": null,
			"nextStartTime": "00:00:00",
			"creationTime": "2018-10-09 15:08:54",
			"lastModifiedTime": "2018-10-09 15:11:20",
			"earlyWarningAlertUsers": []
		},
		"jobPhoneNumberList": null,
		"completedTask": 3612,
		"taskCallTotal": 166,
		"createdByUserName": "超管",
		"organizationName": "系统内置",
		"dialogFlowName": "内置",
		"smsTemplateName": null,
		"systemPauseNextStart": null,
		"callJobStatsInfo": {
			"taskProgress": 2175.9,
			"answeredRate": 9.47,
			"intentLevel": {
				"A": 568,
				"B": 555,
				"C": 606,
				"D": 598,
				"E": 560,
				"F": 569
			},
			"taskCallTotal": 3612,
			"answeredTask": 342,
			"chatDurationTotal": 89659,
			"completedTask": 0,
			"customerConcern": ["安全", "地理位置", "健身", "价格", "交通"],
			"dialResult": {
				"ANSWERED": 342,
				"NO_ANSWER": 348,
				"BUSY": 353,
				"POWER_OFF": 344,
				"OUT_OF_SERVICE": 341,
				"REFUSED": 366,
				"VACANT_NUMBER": 338,
				"CAN_NOT_CONNECT": 334,
				"FROM_PHONE_ERROR": 346,
				"SYSTEM_ERROR": 344
			},
			"chatRound": {
				"LESS_3": 9,
				"F3_T6": 1,
				"F6_T10": 4,
				"F10_MORE": 336
			},
			"chatDuration": {
				"LESS_10S": 14,
				"F10S_T1MIN": 28,
				"F1MIN_T2MIN": 35,
				"F2MIN_T3MIN": 43,
				"F3MIN_TMORE": 230
			},
			"callJobStatsBrokenLine": {
				"taskCallCompletedList": [{
					"date": "2018-09-27",
					"val": 1000
				}, {
					"date": "2018-10-09",
					"val": 1455
				}],
				"answeredTaskList": [{
					"date": "2018-09-27",
					"val": 119
				}, {
					"date": "2018-10-09",
					"val": 134
				}],
				"answeredTaskRateList": [{
					"date": "2018-09-27",
					"val": 11.90
				}, {
					"date": "2018-10-09",
					"val": 9.21
				}],
				"chatDurationTotalList": [{
					"date": "2018-09-25",
					"val": 22547
				}, {
					"date": "2018-09-27",
					"val": 31218
				}, {
					"date": "2018-10-09",
					"val": 35894
				}],
				"averageDurationList": [{
					"date": "2018-09-27",
					"val": 26233
				}, {
					"date": "2018-10-09",
					"val": 26786
				}]
			}
		}
	},
	"requestId": "VJDMUZIC",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：http://robot.yiwise.cn/openapi/v1/task/getTaskDetail

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 robotCallJobId| Integer| 是 |任务Id| 21 |
 

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 robotCallJobId| Integer | 任务id |
 name| String | 任务名称 |
 mode| String | 任务类型 AUTO(0, "自动任务"),MANUAL(1, "手动任务")|
 phoneType| String | 电话类型 MOBILE(0, "M", "手机号码"),LANDLINE(1, "L", "固话"),UNFIXED_CALL(2, "U", "无主叫"),VERBAL_TRICK_TRAINING_CALLER(3, "VR", "训练主叫账号"),VERBAL_TRICK_TRAINING_CALLED(4, "VD", "训练被叫账号"),VOIP_DEVICE(5, "D", "网关设备")|
 robotCount| Integer | 任务拨打的号码总数 |
 startDate| String | 任务开始时间 |
 dailyStartTime| String | 可拨打开始时间 |
 dailyEndTime| String | 可拨打结束时间 |
 inactiveStartTime| String | 暂时停止开始时间 |
 inactiveEndTime| String | 暂时停止结束时间 |
 status| Integer | 任务状态, NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中"),COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停"),TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中");| 1 |
 description| String  | 任务注释 |
 createdByUserName| String  | 创建人 |
 organizationName| String  | 创建组织 |
 dialogFlowName| String  | 话术名称 |
 taskProgress| Double | 任务进度 | 
 answeredRate| Double | 接听率 | 
 taskCallTotal| Integer | 任务完成总数 | 
 answeredTask| Integer | 接听数量 | 
 chatDurationTotal| Integer | 总接听时间 | 
 intentLevel| Map | 意向等级 | 
 customerConcern| Map | 关注点 | 
 dialResult| Map | 通话结果 | 
 chatRound| Map | 通话轮次 | 
 chatDuration| Map | 通话时间 | 
 taskCallCompletedList| List | 任务完成 | 
 answeredTaskList| List | 通话结果 | 
 answeredTaskRateList| List | 通话比例 | 
 chatDurationTotalList| List | 通话轮次 |
 averageDurationList| List | 平均通话时长 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
 
##获取已经完成任务电话号码接口
 
###功能说明：
 
 通过此接口可以获取指定任务中所有已经完成的电话号码
 
 >入参JSON实例
 
 ```
 
{
 	"customerGroupId": 1,
 	"robotCallJobId": 1,
 	"dialogFlowId": 2,
 	"followStatus": "AI_INITIAL_VISIT",
 	"latestCreationTime": "2018-07-25",
 	"resultStatuses": ["ANSWERED"],
 	"searchWords": "测试",
 	"intentLevels": ["A"],
 	"getTrainTaskList": true,
 	"pageSize": 20,
 	"earliestCreationTime": "2018-07-25",
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
                       ],
                       "fullAudioUrl": "https://ai-call-platform.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId50/OUZAXBCB__TaskId_4/ai_user.wav",
                       "customerAudioUrl": "https://ai-call-platform.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId50/OUZAXBCB__TaskId_4/user.wav",
                       "analysisBasis": "",
                       "startTime": "2018-08-04 11:57:33",
                       "chatDuration": 93,
                       "chatRound": 16,
                       "manualMarked": false,
                       "readStatus": "NOT_READ",
                       "customerGroupName": null,
                       "robotCallJobName": "曹文浩123",
                       "dialogFlowName": "张三",
                       "customerPersonInfo": null,
                       "callDetailList": null
                   }
               ]
           },
           "requestId": "YXDXFDSC",
           "resultMsg": "获取成功",
           "errorStackTrace": null
       }
 ```
 
###请求：
 
 URL：http://robot.yiwise.cn/openapi/v1/task/getCallRecordInfoList
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Integer| 是 | 任务id| 1 |
  searchWords| Integer| 否 |关键字搜索| 0 |
  customerGroupId| Integer| 否 |分组ID| 100 |
  resultStatuses| List| 否 |通话结果 ANSWERED(0, "已接听", null),NO_ANSWER(1, "未接", "呼叫号码未接听"),BUSY(2, "占线", "呼叫号码占线"),POWER_OFF(3, "关机", "呼叫号码关机"),OUT_OF_SERVICE(4, "被叫停机", "呼叫号码停机"),REFUSED(5, "拒接", "呼叫号码拒接"),VACANT_NUMBER(6, "空号", "呼叫的号码是空号"),CAN_NOT_CONNECT(7, "无法接通", "呼叫的号码无法接通"),                 // 无法接通，或没拨通，或没能获取到EarlyMediaFROM_PHONE_ERROR(8, "主叫号码不可用", "主叫号码不可用"),              // 主叫号码不可用，主叫欠费SYSTEM_ERROR(9, "外呼失败", "外呼失败")| ["ANSWERED", "REFUSED"] |
  intentLevels| List| 否 |客户关注点 A(0, "A级(较强)"),B(1, "B级(一般)"),C(2, "C级(无法判断)"),D(3, "D级(很少)"),E(4, "E级别(需要再次跟进)"),F(5, "F级别(无需再次跟进)")| ["B", "C"] |
  followStatus| String| 否 |跟进状态 AI_INITIAL_VISIT(0, "AI初访"),PEOPLE_INITIAL_VISIT(1, "人工初访"),FOLLOW_UP(2, "持续跟进");| 1 |
  dialogFlowId| Integer| 否 |话术id| 1 |
  earliestCreationTime| Integer| 否 |最早创建时间，日期标准格式，请不要包含时间。可以为空| "2018-07-25" |
  latestCreationTime| Integer| 否 |最晚创建时间，日期标准格式，请不要包含时间。可以为空| "2018-07-25" |
  getTrainTaskList| Integer| 否 |为true表示获取话术训练列表| true |
  pageNum| Integer| 否 |第几页(默认为1)| 1 |
  pageSize| Integer| 否 |显示数量/页（默认为20）| 10 |
  resultQueryList| List| 否 |支持按分析结果作为条件| 10 |
  
  
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
  number| Integer | 第几页 |
  pageSize| Integer | 每页页面条数 |
  totalElements| Integer | 数据总条数 |
  pages| Integer | 页面总数 |
  callRecordId| Integer | 通话ID |
  robotCallTaskId| Integer | 任务实例id（每个被叫电话为一个实例） |
  dialogFlowId| Integer | 话术id |
  dialogFlowName| Integer | 话术名称 |
  robotCallJobId| Integer |任务id|
  robotCallJobName| Integer |任务名称|
  phoneNumberId| Integer |电话线路id|
  customerPersonId| Integer |接受电话客户id|
  calledPhoneNumber| String | 被叫客户电话号码 |
  resultStatus| String | 接听状态,  |
  intentLevel| String | 意向等级,  |
  realIntentLevel| String | 真是意向等级,  |
  customerConcern| List | 客户关注点,  |
  fullAudioUrl| String | 完整音频地址 |
  customerAudioUrl| String | 客户音频地址 |
  chatDuration| Integer  | 通话时长 |
  chatRound| Integer | 通话轮次 |
  startTime| String | 开始拨打时间 |
  endTime| String | 结束拨打时间 |
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
        "phoneLog": {
            "phoneLogs": [ 
                {
                    "sceneInstanceLogId": 1321,
                    "sceneInstanceId": 540, 
                    "speaker": "AI", 
                    "content": "哎，您好，等待2s 哎，您好，拱墅区 中大银泰城边上有个首付50万左右的精装公寓你考虑吗？", 
                    "userMean": null,
                    "userMeanDetail": null,
                    "aiUnknown": 1,
                    "startTime": 0,
                    "endTime": 0,
                    "gmtCreate": "2018-01-24 20:51:53",
                    "gmtModified": "2018-01-24 20:51:53"
                },
                {
                    "sceneInstanceLogId": 1322,
                    "sceneInstanceId": 540,
                    "speaker": "ME",
                    "content": "喂你好",
                    "userMean": "~",
                    "userMeanDetail": null,
                    "aiUnknown": 0,
                    "startTime": 300,
                    "endTime": 1145,
                    "gmtCreate": "2018-01-24 20:51:55",
                    "gmtModified": "2018-01-24 20:51:55"
                },
                {
                    "sceneInstanceLogId": 1323,
                    "sceneInstanceId": 540,
                    "speaker": "ME",
                    "content": "哦你好",
                    "userMean": "~",
                    "userMeanDetail": null,
                    "aiUnknown": 0,
                    "startTime": 2330,
                    "endTime": 3565,
                    "gmtCreate": "2018-01-24 20:51:57",
                    "gmtModified": "2018-01-24 20:51:57"
                }
          "luyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/540/JYSYDCCHVFYYTMGJKKHJAMHARNNBWEJQ.wav" 
         },
         "sceneInstance": {
             "callInstanceId": 540, 
             "companyId": 1, 
             "callJobId": 31, 
             "customerId": 55, 
             "customerTelephone": "17751279857", 
             "customerName": "不弃", 
             "status": 2, 
             "finishStatus": 0,
             "duration": 87, 
             "chatRound": 18, 
             "startTime": "2018-01-24 20:51:53", 
             "endTime": "2018-01-24 20:53:28", 
             "callerPhone": "18072749353", 
             "luyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/540/JYSYDCCHVFYYTMGJKKHJAMHARNNBWEJQ.wav",
             "userLuyinOssUrl": "https://byrobot-test.oss-cn-hangzhou.aliyuncs.com/RobotPhoneCommunicate/540_user.wav",
             "properties": "{}",
             "handlePerson": "房产电销优化版",
             "callType": 1,
             "readStatus": 1,
             "jobName": "buqi新的测试任务",
            "robotDefId": 6,
             "sceneDefId": 11,
             "sceneRecordId": 1,
             "trackResult": null,
             "hangUp": 0,
             "secondaryCallTime": "1970-01-01 13:00:00",
             "secondaryCallTimes": 2,
             "gmtCreate": "2018-01-24 20:51:31",
             "gmtModified": "2018-02-03 18:27:19"
         },
         "taskResult": [ 
             {
                 "sceneInstanceResultId": 188,
                 "companyId": 1,
                 "sceneInstanceId": 540,
                 "resultName": "预约时间",
                 "resultValue": "2018-01-25 08:00",
                 "resultDesc": null,
                 "analyzeType": null,
                 "gmtCreate": "2018-01-24 20:53:01",
                "gmtModified": "2018-01-24 20:53:01"
             },
             {
                 "sceneInstanceResultId": 189,
                 "companyId": 1,
                 "sceneInstanceId": 540,
                 "resultName": "客户意向等级",
                 "resultValue": "A级(较强)",
                 "resultDesc": "该客户在通话过程中主动询问了产品细节，有进一步了解产品的意愿。",
                 "analyzeType": "BY_ANALYZE_USER_LEVEL",
                 "gmtCreate": "2018-01-24 20:53:28",
                 "gmtModified": "2018-01-31 10:34:55"
             }
         ]
     },
     "resultMsg": "获取成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://robot.yiwise.cn/openapi/v1/task/phoneLogInfo
 
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
  phoneLogs| List | 对话内容 |
  sceneInstanceId| Integer | 任务实例id |
  speaker| String |角色|
  content| String | 内容 |
  aiUnknown| Integer | 是否是ai无法应答的问题，1-是，0-否 |
  luyinOssUrl| String |通话录音|
  callInstanceId| Integer | 任务实例id（每个被叫电话为一个实例） |
  companyId| Integer | 公司id |
  callJobId| Integer |任务id|
  customerId| Integer | 客户id |
  customerTelephone| String | 客户手机 |
  customerName| String | 客户名称 |
  finishStatus| String | 任务实例已经完成的状态, 0:已接, 1:拒接, 2:无法接通, 3:主叫号码不可用, 4:空号, 5:关机, 6:占线, 7:停机, 8:未接, 9:主叫欠费 |
  status| Integer | |
  duration| Integer  | 通话时长 |
  chatRound| Integer | 通话轮次 |
  startTime| String | 开始拨打时间 |
  endTime| String | 结束拨打时间 |
  callerPhone| String | 主叫电话 |
  luyinOssUrl| Integer | 通话录音 |
  callType| Integer | 拨打类型 0: 免费试用 1: 任务 2: 用户单独拨打 |
  readStatus| Integer | 是否已读 0: 未读 1: 已读 |
  robotDefId| String | 关联的机器人id |
  sceneDefId| String | 场景ID | 
  sceneRecordId| Integer | 关联的录音id | 
  trackResult| List | bug追踪结果 | 
  jobName| String | 任务名称 | 
  hangUp| Integer | 挂机人, 0: AI 1: 用户 |
  taskResult| String | 任务结果分析 |
  resultMsg| String | 响应说明 |




