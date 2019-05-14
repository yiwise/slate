# 任务信息查询接口

## 获取任务列表接口

### 功能说明：

通过此接口可以获取指定公司的任务列表

> JSON 响应实例：

```json
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
      "createTime": "2018-09-26 18:07",
      "createdByUserName": null,
      "organizationName": null
    }]
  },
  "requestId": "OTMAGZFW",
  "resultMsg": "创建成功",
  "errorStackTrace": null
}
```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/getJobs

### 请求方法：

GET

### 请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 name| String| 否 |任务名称| 测试 |
 status| String| 否 | 任务状态,(NOT_STARTED, "未开始"),(IN_PROCESS, "进行中"),(COMPLETED, "已完成"),(RUNNABLE, "可运行"),(USER_PAUSE, "用户暂停"),(SYSTEM_SUSPENDED, "系统暂停"),(TERMINATE, "已终止"),(IN_QUEUE, "排队中");| 1 |
 pageNum| Integer| 否 | 第几页,默认1| 1 |
 pageSize| Integer| 否 | 页面大小,选填,默认20,最大值100| 10 |



### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 number| Integer | 第几页 |
 pageSize| Integer | 每页页面条数 |
 totalElements| Integer | 数据总条数 |
 pages| Integer | 页面总数 |
 robotCallJobId| Long | 任务id |
 name| String | 任务名称 |
 completedTask| Integer | 完成的任务 |
 taskCallTotal| Integer | 任务总数 |
 createTime| String | 创建时间 |
 createdByUserName| String | 创建人 |
 organizationName| String | 组织 |
 status| String | 任务状态, NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中"),COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停"),TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中");| 1 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

## 获取任务详情接口

### 功能说明：

通过此接口可以获取指定任务的详细信息

> JSON 响应实例：

```json
{
	"code": 200,
	"data": {
		"robotCallJob": {
			"robotCallJobId": 1,
			"tenantId": 1,
			"dialogFlowId": 1,
		  "dialogFlowName":"金融行业体验demo-优化版",
			"name": "dialog测试",
			"mode": "MANUAL",
			"robotCount": 12,
			"smsTemplateId": null,
			"phoneType": "LANDLINE",
			"dailyStartTime": "15:08:31",
			"dailyEndTime": "15:08:36",
			"inactiveTimeList": [{"startTime":"12:00", "endTime":"13:00"}],
			"description": null,
			"wechatAlertLevel": [],
			"wechatAlertLevelCode":[],
			"smsAlertLevel": [],
			"smsAlertLevelCode":[],
			"wechatConditionAlertLevel":[],
			"wechatConditionAlertLevelCode":[],
			"alertUsers": [],
			"wechatSendMethod": "SENDTOALL",
			"status": "TERMINATE",
			"startTime": null,
			"nextStartTime": "00:00:00",
			"createTime": "2018-10-09 15:08:54",
			"updateTime": "2018-10-09 15:11:20",
			"earlyWarningAlertUsers": []
		},
    "jobPhoneNumberList": [{
        "tenantPhoneNumberId": 675,
        "phoneNumber": "13576084683",
        "phoneName": "",
        "enabledStatus": 1,
        "phoneType": "LANDLINE",
        "concurrencyQuota": 5
      }],
    "transferPhoneNumber": [
        "1523654789",
        "1758426896"
    ],
		"completedTask": 3612,
		"taskCallTotal": 166
	},
	"requestId": "VJDMUZIC",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/getJobDetail

### 请求方法：

GET


### 请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 robotCallJobId| Long| 是 |任务Id| 21 |
 

### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 robotCallJobId| Long | 任务id |
 dialogFlowId| Long | 话术id |
 name| String | 任务名称 |
 mode| String | 任务类型 (AUTO, "自动任务"),(MANUAL, "手动任务")|
 phoneType| String | 线路类型 (MOBILE, "手机"),(LANDLINE, "固话"),(UNFIXED_CALL, "无主叫固话"),(CALL_POLICY_GROUP，"外呼策略组")|
 robotCount| Integer | 任务拨打的号码总数 |
 smsTemplateId| Long | 短信模版id |
 dailyStartTime| String | 可拨打开始时间 |
 dailyEndTime| String | 可拨打结束时间 |
 inactiveTimeList| List| 不可拨打时间段列表|
 description| String  | 任务注释 |
 wechatAlertLevel| String  | 微信提示等级 |
 wechatAlertLevelCode | Integer | 微信提示等级code |
 smsAlertLevel| String  | 短信提示等级 |
 smsAlertLevelCode | Integer | 短信提示登记code |
 wechatConditionAlertLevel | String | 微信条件提示等级|
 wechatConditionAlertLevelCode | Integer | 微信条件提示等级Code|
 alertUsers| String  | 提示人员 |
 earlyWarningAlertUsers| String  | 预警提示人员 |
 createTime| String | 任务创建时间 |
 updateTime| String | 任务修改时间 |
 startTime| String | 任务开始时间 |
 nextStartTime| String | 下一次任务开始时间 |
 status| String | 任务状态, NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中"),COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停"),TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中")| 1 |
 jobPhoneNumberList| List  | 任务主叫线路列表 |
 policyGroupPhoneNumberList| List  | 外呼策略组包含的线路信息 |
 transferPhoneNumber| List| 转人工号码 |
 dialogFlowName| String  | 话术名称 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
 

## 获取任务统计接口

### 功能说明：

通过此接口可以获取指定任务的统计详细信息

> JSON 响应实例：

```json
{
	"code": 200,
	"data": {
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
				}],
				"intentLevelTagDetailList":[
          {
              "code":0,
              "intentLevelTagDetailId":825,
              "intentLevelTagId":121,
              "name":"较差"
          },
          {
              "code":1,
              "intentLevelTagDetailId":826,
              "intentLevelTagId":121,
              "name":"一般"
          },
          {
              "code":2,
              "intentLevelTagDetailId":827,
              "intentLevelTagId":121,
              "name":"好"
          },
          {
              "code":3,
              "intentLevelTagDetailId":828,
              "intentLevelTagId":121,
              "name":"很好"
          }]
			}
	},
	"requestId": "VJDMUZIC",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/getJobStats

### 请求方法：

GET


### 请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 robotCallJobId| Long| 是 |任务Id| 21 |
 

### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 taskProgress| Double | 任务进度 | 
 answeredRate| Double | 接听率 | 
 completedTask| Integer | 完成总数 | 
 taskCallTotal| Integer | 任务总数 | 
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
 intentLevelTagDetailList | List | 意向分类详情列表|
 code | Integer| 意向分类详情编码|
 intentLevelTagDetailId |Long |意向分类详情id |
 intentLevelTagId | Long| 意向分类id |
 name | String| 意向分类详情名称 |
 


## 获取任务中的变量（包括话术变量和短信变量）

### 功能说明：

通过接口可以获取该任务中的自定义变量，包括话术变量、意向短信变量、挂机短信变量等

> JSON 响应实例：

```json
{
	"code": 200,
	"data": [
		"欠款金额",
		"最后还款日期"
	],
	"requestId": "RKXNIQAF",
	"resultMsg": "获取自定义属性成功",
	"errorStackTrace": null
}

```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/getJobProperties

### 请求方法：

### 请求方法：

GET

### 请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 robotCallJobId| Long| 是 |任务Id| 21 |

### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
