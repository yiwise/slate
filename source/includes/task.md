#任务操作接口

##创建任务接口

###功能说明：

通过此接口可以创建新的任务

###更新说明：

创建任务,支持使用多个无主叫固话,只需设置总并发数,由系统自动分配每个线路的并发。

>入参JSON实例：

```
{
	"jobPhoneNumberList": [{
		"key": 348,
		"value": "test"
	}],
	"robotCallJob": {
		"alertUsers": [],
		"dailyEndTime": "21:00",
		"dailyStartTime": "09:00",
		"description": "gthjoitjdjfdk",
		"dialogFlowId": 2,
		"earlyWarningAlertUsers": [],
		"inactiveEndTime": "13:00",
		"inactiveStartTime": "12:00",
		"mode": "AUTO",
		"name": "测试名称3333",
		"phoneType": "LANDLINE",
		"robotCount": 10,
		"smsAlertLevel": ["A"],
		"smsTemplateId": 1,
		"startTime": "2017-11-21 04:32:00",
		"tenantId": 1,
		"wechatAlertLevel": [],
		"wechatSendMethod": "SENDTOALL"
	}
}
```

>JSON响应实例：

```
{
	"code": 200,
	"data": 139,
	"requestId": "RKXNIQAF",
	"resultMsg": "修改成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://crm.tanyibot.com/apiOpen/v1/task/createTask

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 jobPhoneNumberList| List| 是 |任务主叫号码列表 key为tenant_phone_number_id， val是线路号码|  [{"key": 348,"value": "test"}] |
 name| String| 是 |任务名称| 测试API任务 |
 mode| Integer| 是 | 任务类型 AUTO(0, "自动任务"),MANUAL(1, "手动任务"); | AUTO |
 startTime| String| 是 | 任务开始时间| "2017-11-21 04:32:00"  |
 dailyStartTime| String| 是 | 可拨打开始时间| 08:00 |
 dailyEndTime| String| 是 | 可拨打结束时间| 22:00 |
 inactiveStartTime| String| 是 | 暂时停止开始时间| 12:00 |
 inactiveEndTime| String| 是 | 暂时停止结束时间| 13:00 |
 dialogFlowId| String| 是 | 话术id| 139|
 alertUsers| String| 否 | 提醒的用户的id列表| [1,2]|
 earlyWarningAlertUsers| String| 否 | 行业预警消息推送人| [1,2]|
 phoneType| String| 是 | 号码类型 MOBILE(0, "M", "手机号码"),LANDLINE(1, "L", "固话"),UNFIXED_CALL(2, "U", "无主叫"),VERBAL_TRICK_TRAINING_CALLER(3, "VR", "训练主叫账号"),VERBAL_TRICK_TRAINING_CALLED(4, "VD", "训练被叫账号"),VOIP_DEVICE(5, "D", "网关设备");| UNFIXED_CALL|
 robotCount| String| 是 | AI数量| 10|
 smsAlertLevel| String| 否 | 短信推送提醒意向等级| ["A","B"]|
 smsTemplateId| String| 否 | 短信模板地址| |
 wechatAlertLevel| String| 否 | 微信推送提醒意向等级| ["A","B"]|
 wechatSendMethod| String| 否 | 微信推送方式（SENDTOALL 全推送/SENDTOONE 单推送/SENDTONONE 不推送）| SENDTOALL|
 description| String| 否 | 备注| 测试|



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 data|Long | 刚刚创建的任务ID |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

##启动任务接口

###功能说明：

通过此接口可以启动指定的任务

>JSON响应实例：

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

URL：https://crm.tanyibot.com/apiOpen/v1/task/start

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 robotCallJobId| Integer| 是 | 任务Id| 1 |


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
 
##暂停任务接口
 
###功能说明：
 
 通过此接口可以暂停指定的任务
 
 >JSON响应实例：
 
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
 
 URL：https://crm.tanyibot.com/apiOpen/v1/task/pause
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Integer| 是 | 任务Id| 1 |
 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
 requestId| String | 请求Id |
  resultMsg| String | 响应说明 |

##停止任务接口
 
###功能说明：
 
 通过此接口可以停止  指定的任务
 
 >JSON响应实例：
 
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
 
 URL：https://crm.tanyibot.com/apiOpen/v1/task/stop
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Integer| 是 | 任务Id| 1 |
 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
 requestId| String | 请求Id |
  resultMsg| String | 响应说明 |
  
##删除任务
  
###功能说明：
  
通过调用此接口可以删除任务信息
>入参JSON实例

```
{
  "robotCallJobId": "1"
}
```
>JSON响应实例：

```
{
	"code": 200,
	"data": null,
	"requestId": "GDFVVSAE",
	"resultMsg": "删除成功",
	"errorStackTrace": null
}

```
  
###请求：
 
 URL：https://crm.tanyibot.com/apiOpen/v1/task/delete
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| long| 是 | 删除任务| 1 |  
###响应：
 
 参数名 | 类型 | 描述 |
 --------- | ------- |------
  code|Integer | 响应码 |
 requestId| String | 请求Id |
  resultMsg| String | 响应说明 |

##向任务中导入客户接口
 
###功能说明：
 
 通过此接口可以向指定的任务导入客户信息，用于拨打电话
 
 >入参JSON实例:
 
  ```
{
	"robotCallJobId": 28,
	"customerPersons": [{
		"name": "test",
		"phoneNumber": "11111111111",
		"properties": {
			"ttt": "jjj"
		}
	}]
}
  
  ```
  
 >JSON响应实例：
 
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
 
 URL：https://crm.tanyibot.com/apiOpen/v1/task/importTaskCustomer

###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  robotCallJobId| Integer| 是 | 任务Id| 1 |
  name| String| 是 | 客户名称| 张三 |
  phoneNumber| String| 是 | 客户电话| 13998987676 |
  properties| Map<String,String>| 否 | 话术中自定义的语句内容| 请看json入参 |

 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
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
	"resultMsg": "修改成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://crm.tanyibot.com/apiOpen/v1/task/update

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |------
 robotCallJobId| Integer| 是 | 任务Id| 1 |
 robotCount| Integer| 是 | 任务数量| 1 |


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
 
  
