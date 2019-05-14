# 任务操作接口

## 创建任务接口

### 功能说明：

通过此接口可以创建新的任务 

### 更新说明：

创建任务,支持使用多个无主叫固话,只需设置总并发数,由系统自动分配每个线路的并发。

> JSON 入参实例：

```json
{
	"concurrencyQuota": 2,
	"jobPhoneNumberIdList": [
		348,369
	],
	"transferPhoneNumber": [
	  "1523654789",
	  "1758426896"
	],
	"robotCallJob": {
		"alertUsers": [],
		"dailyEndTime": "21:00",
		"dailyStartTime": "09:00",
		"description": "gthjoitjdjfdk",
		"dialogFlowId": 2,
		"earlyWarningAlertUsers": [],
		"inactiveTimeList": [{"startTime":"12:00", "endTime":"13:00"}],
		"mode": "AUTO",
		"name": "测试名称3333",
		"phoneType": "LANDLINE",
		"robotCount": 10,
		"smsAlertLevel": ["A"],
		"smsTemplateId": 1,
		"startTime": "2017-11-21 04:32:00",
		"tenantId": 1,
		"wechatAlertLevel": [],
		"wechatSendMethod": "SENDTOALL",
		"wechatAlertLevelCode": [],
		"smsAlertLevelCode": [],
		"wechatConditionAlertLevelCode": []
	}
}
```

> JSON 响应实例：

```json
{
	"code": 200,
	"data": {"robotCallJobId":139},
	"requestId": "RKXNIQAF",
	"resultMsg": "修改成功",
	"errorStackTrace": null
}

```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/create

### 请求方法：

POST


### 请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 concurrencyQuota| Integer| 是 | 并发数（线路类型为手机号的时候可不传）| 10|
 jobPhoneNumberIdList| List| 是 |任务主叫号码列表 tenant_phone_number_id,当类型是手机号的时候他的size代表机器人的个数，当类型非手机号的时候他的size只能是1, 如果外呼方式选择的是外呼策略组，则里面内容为外呼策略组的id（size只能为1）|  [1,2,3] |
 transferPhoneNumber| List| 选择转人工话术时必填 |转人工号码,触发转人工时轮训号码列表| ["1523654789","1758426896"] |
 name| String| 是 |任务名称| 测试API任务 |
 mode| String| 是 | 任务类型 (AUTO, "自动任务"),(MANUAL, "手动任务"); | AUTO |
 startTime| String| 自动任务：是/手动任务：否 | 任务开始时间| "2017-11-21"  |
 dailyStartTime| String| 是 | 可拨打开始时间，不可以早于9点| 09:00 |
 dailyEndTime| String| 是 | 可拨打结束时间，不可以晚于20点| 20:00 |
 inactiveTimeList| List| 否 | 不可拨打时间段列表,最大三个不可拨打时段| [{"startTime":"12:00", "endTime":"13:00"}] |
 dialogFlowId| String| 是 | 话术id| 139|
 csStaffGroupId| Long| 是 | 坐席组id，通过话术API中获取人工介入标识。如果存在人工介入标识，需要传入坐席组Id| 139|
 alertUsers| String| 否 | 提醒的用户的id列表| [1,2]|
 earlyWarningAlertUsers| String| 否 | 行业预警消息推送人| [1,2]|
 phoneType| String| 是 | 号码类型 (MOBILE, "手机号码"),(LANDLINE, "固话"),(UNFIXED_CALL, "无主叫"), (CALL_POLICY_GROUP, "外呼策略组")| UNFIXED_CALL|
 smsAlertLevel| String| 否 | 短信推送提醒意向等级| ["A","B"]|
 smsTemplateId| Long| 否 | 短信模板id| |
 wechatAlertLevel| String| 否 | 微信推送提醒意向等级| ["A","B"]|
 wechatSendMethod| String| 否 | 微信推送方式（SENDTOALL，全推送），（SENDTOONE，单推送），（SENDTONONE 不推送）| SENDTOALL|
 description| String| 否 | 备注| 测试|
 wechatAlertLevelCode | Integer | 否 | 微信推送提醒意向等级编码 | [0, 1] |
 smsAlertLevelCode | Integer | 否| 短信推送提醒意向等级编码| [0, 1]|
 wechatConditionAlertLevelCode | Integer | 否| 微信条件推送提醒意向等级编码|[0, 1] |

### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 robotCallJobId|Long | 刚刚创建的任务ID |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

## 启动任务接口

### 功能说明：

通过此接口可以启动指定的任务

> JSON 响应实例：

```json
{
	"code": 200,
	"data": null,
	"requestId": "RKXNIQAF",
	"resultMsg": "修改成功",
	"errorStackTrace": null
}

```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/start

### 请求方法：

POST

### 请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 robotCallJobId| Long| 是 | 任务Id| 1 |

### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
 
## 暂停任务接口
 
### 功能说明：
 
通过此接口可以暂停指定的任务
 
> JSON 响应实例：
 
```json
{
	"code": 200,
	"data": null,
	"requestId": "RKXNIQAF",
	"resultMsg": "修改成功",
	"errorStackTrace": null
}
 
 ```
 
### 请求：
 
URL：https://openapi.tanyibot.com/apiOpen/v1/job/pause
 
### 请求方法：
 
POST
 
### 请求参数:
 
参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
robotCallJobId| Integer| 是 | 任务Id| 1 |
 
 
### 响应：
 
参数名 | 类型 | 描述 
--------- | ------- |------
code|Integer | 响应码 |
requestId| String | 请求Id |
resultMsg| String | 响应说明 |

## 停止任务接口
 
### 功能说明：
 
通过此接口可以停止  指定的任务
 
> JSON 响应实例：
 
```json
{
	"code": 200,
	"data": null,
	"requestId": "RKXNIQAF",
	"resultMsg": "修改成功",
	"errorStackTrace": null
}
```
 
### 请求：
 
URL：https://openapi.tanyibot.com/apiOpen/v1/job/stop
 
### 请求方法：
 
 POST
 
 
### 请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Integer| 是 | 任务Id| 1 |
 
 
### 响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|Integer | 响应码 |
 requestId| String | 请求Id |
  resultMsg| String | 响应说明 |
  
## 删除任务
  
### 功能说明：
  
通过调用此接口可以删除任务信息

> JSON 入参实例

```json
{
  "robotCallJobId": "1"
}
```
> JSON 响应实例：

```
{
	"code": 200,
	"data": null,
	"requestId": "GDFVVSAE",
	"resultMsg": "删除成功",
	"errorStackTrace": null
}

```
  
### 请求：
 
URL：https://openapi.tanyibot.com/apiOpen/v1/job/delete
 
### 请求方法：
 
POST
 
### 请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Long| 是 | 删除任务| 1 |  
### 响应：
 
 参数名 | 类型 | 描述 |
 --------- | ------- |------
  code|Integer | 响应码 |
 requestId| String | 请求Id |
  resultMsg| String | 响应说明 |

## 向任务中导入客户接口
 
### 功能说明：
 
通过此接口可以向指定的任务导入客户信息，用于拨打电话。（单次导入客户数量不能大于100）
 
> JSON 入参实例:
 
```json
{
	"robotCallJobId": 28,
	"customerPersons": [{
		"name": "test",
		"phoneNumber": "11111111111",
		"properties": {
			"欠款金额": "10.13",
			"最后还款日期": "2018年10月3日"
		}
	}]
}
  
```
  
> JSON 响应实例：
 
 ```
 {
 	"code": 200,
 	"data": null,
 	"requestId": "RKXNIQAF",
 	"resultMsg": "修改成功",
 	"errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：https://openapi.tanyibot.com/apiOpen/v1/job/importCustomer

###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Long| 是 | 任务Id| 1 |
  name| String| 是 | 客户名称| 张三 |
  phoneNumber| String| 是 | 客户电话| 13998987676 |
  properties| Map<String,String>| 否 | 话术中自定义的语句内容| 请看json入参 |

 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|Integer | 响应码 |
 requestId| String | 请求Id |
  resultMsg| String | 响应说明 |

##修改任务并发数（AI坐席数量）

###功能说明：

通过接口可以更改AI坐席数量，功能同crm端编辑话术时修改外呼号码的AI坐席数

>入参JSON实例

```
{
	"robotCallJobId": 28,
	"robotCount": 2
}

```

>JSON响应实例：

```
{
	"code": 200,
	"data": null,
	"requestId": "RKXNIQAF",
	"resultMsg": "导入成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/updateAiCount

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |------
 robotCallJobId| Long| 是 | 任务Id| 1 |
 robotCount| Integer| 是 | 任务数量| 1 |


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
 
  
