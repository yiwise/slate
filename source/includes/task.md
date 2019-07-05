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
		"wechatConditionAlertLevelCode": [],
        "redialCondition":["CALL_LOSS","NO_ANSWER","BUSY","REFUSED","POWER_OFF","OUT_OF_SERVICE","CAN_NOT_CONNECT","FROM_PHONE_ERROR","SYSTEM_ERROR"],
        "redialInterval":6,
        "redialTimes":1,
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
 concurrencyQuota| Integer| 是 | 并发数（线路类型为手机号的时候可不传）| 10
 jobPhoneNumberIdList| List| 是 |任务主叫号码列表 tenant_phone_number_id,当类型是手机号的时候他的size代表机器人的个数，当类型非手机号的时候他的size只能是1；如果外呼方式选择的是外呼策略组，则里面内容为外呼策略组的id（size只能为1）|  [1,2,3] 
 transferPhoneNumber| List| 选择转人工话术时必填 |转人工号码,触发转人工时轮训号码列表| ["1523654789","1758426896"] 
 name| String| 是 |任务名称| 测试API任务 
 mode| String| 是 | 任务类型 (AUTO, "自动任务"),(MANUAL, "手动任务"); | AUTO 
 startTime| String| 自动任务：是/手动任务：否 | 任务开始时间| "2017-11-21"  
 dailyStartTime| String| 是 | 可拨打开始时间，不可以早于9点| 09:00 
 dailyEndTime| String| 是 | 可拨打结束时间，不可以晚于20点| 20:00 
 inactiveTimeList| List| 否 | 不可拨打时间段列表,最大三个不可拨打时段| [{"startTime":"12:00", "endTime":"13:00"}] 
 dialogFlowId| String| 是 | 话术id| 139
 csStaffGroupId| Long| 是 | 坐席组id，通过话术API中获取人工介入标识。如果存在人工介入标识，需要传入坐席组Id| 139
 alertUsers| String| 否 | 提醒的用户的id列表| [1,2]
 earlyWarningAlertUsers| String| 否 | 行业预警消息推送人| [1,2]
 robotCount| Integer| 是 | 机器人数| 10
 phoneType| String| 是 | 号码类型 (MOBILE, "手机号码"),(LANDLINE, "固话"),(UNFIXED_CALL, "无主叫"), (CALL_POLICY_GROUP, "外呼策略组")| UNFIXED_CALL
 smsAlertLevel| String| 否 | 短信推送提醒意向等级| ["A","B"]
 smsTemplateId| Long| 否 | 短信模板id| 
 wechatAlertLevel| String| 否 | 微信推送提醒意向等级| ["A","B"]
 wechatSendMethod| String| 否 | 微信推送方式（SENDTOALL，全推送），（SENDTOONE，单推送），（SENDTONONE 不推送）| SENDTOALL
 description| String| 否 | 备注| 测试
 wechatAlertLevelCode | Integer | 否 | 微信推送提醒意向等级编码 | [0, 1] 
 smsAlertLevelCode | Integer | 否| 短信推送提醒意向等级编码| [0, 1]
 wechatConditionAlertLevelCode | Integer | 否| 微信条件推送提醒意向等级编码|[0, 1] 
 redialCondition | Set | 选择自动重拨时必填 | 重拨条件(CALL_LOSS,"呼损客户"),(NO_ANSWER,"无应答"),(BUSY,"忙线中"),(REFUSED,"拒接"),(POWER_OFF,"关机"),(OUT_OF_SERVICE,"停机"),(CAN_NOT_CONNECT,“无法接通“),(FROM_PHONE_ERROR,"主叫欠费"),(SYSTEM_ERROR,"外呼失败") |["CALL_LOSS"] 
 redialInterval | Integer | 选择自动重拨时必填 | 重拨间隔(分钟，取值范围6分钟~24 x 60分钟) |6 
 redialTimes | Integer | 选择自动重拨时必填 | 重拨次数(取值范围1~10） |6 

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
  robotCallJobId| Long| 是 | 任务Id| 1 
  name| String| 否 | 客户名称| 张三 
  phoneNumber| String| 是 | 客户电话| 13998987676 
  properties| Map<String,String>| 否 | 话术中自定义的语句内容| 请看json入参 

 

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

  

##（开始/暂停/终止所有任务前）检查所有任务

###功能说明：

通过接口可以在开始/暂停/终止所有任务前检查所有任务

> 入参JSON实例

```
{
        "operation": "PAUSE",                    
        "robotCallJobIdSet": [11445,44564],      
        "statusSet": [                             
          "IN_PROCESS"
        ],
        "name": "模糊查询",                         
        "beginCreateDate": "2018-10-10"            
        "endCreateDate": "2018-10-12"             
      }

```

> JSON响应实例：

```
{
          "code": 200,
          "data": {
              "executable": [                                           
               {
                      "robotCallJobId":33,                               
                      "robotCallJobName":"熊隆祥重新添加到拨打任务调试",
                      "createTime":"2018-10-11 11:21:36",                
                      "createUserName":"超管",                           
                      "status":"NOT_STARTED",                           
                      "hangUpType":"PHONE_UNBIND",                       
                      "hangUpReason":"使用的线路已解绑",                
                      "statsInfo":{                                      
                          "robotCallJobId":33,                           
                          "completedTask":1,                           
                          "totalTask":1，                                
                          "answeredTask":1,                              
                          "ablevelCustomer"：1                          
                      }
                  }
              ],
              "unexecutable": [                                         
              {
                          "msg":""                                      
                          "statsInfo":                                   
                          {
                          "robotCallJobId":33,                          
                          "completedTask":1,                           
                          "totalTask":1，                            
                          "answeredTask":1,                             
                          "ablevelCustomer"：1                        
                           }
                 }
              ]
          },
          "requestId": "IJAQKCWI",
          "resultMsg": "操作成功",
          "errorStackTrace": null
      }
        "requestId": "BWPTZMQZ",
        "resultMsg": "操作成功",
        "errorStackTrace": null
      }

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/checkAll

###请求方法：

POST

###请求参数:

| 参数名            | 类型      | 是否必须 | 描述                                                         | 实例          |
| ----------------- | --------- | -------- | ------------------------------------------------------------ | ------------- |
| operation         | String    | 是       | 操作类型，必填 PAUSE:暂停 START:开始                         | PAUSE         |
| robotCallJobIdSet | Set       | 是       | 任务id集合                                                   | [11445,44564] |
| statusSet         | String    | 否       | 任务状态，NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中")，COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停")，TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中"),SYSTEM_HANG_UP(10, "系统挂起"),WAITING_FOR_REDIAL(11, "等待重呼"),ACCOUNT_DISABLE(12, "账户禁用"),MAINTAIN(13, "系统维护"); | IN_PROCESS    |
| name              | String    | 否       | 任务名称                                                     | 我是任务名    |
| beginCreateDate   | LocalDate | 否       | 开始任务创建日期                                             | 2018-10-10    |
| endCreateDate     | LocalDate | 否       | 结束任务创建日期                                             | 2018-10-12    |

###响应：

| 参数名           | 类型          | 描述                                                         |
| ---------------- | ------------- | ------------------------------------------------------------ |
| code             | Integer       | 响应码                                                       |
| requestId        | String        | 请求Id                                                       |
| resultMsg        | String        | 响应说明                                                     |
| robotCallJobId   | Long          | 任务id                                                       |
| robotCallJobName | String        | 任务名                                                       |
| createTime       | LocalDateTime | 创建时间                                                     |
| createUserName   | String        | 任务创建人                                                   |
| status           | String        | 任务状态，NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中")，COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停")，TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中"),SYSTEM_HANG_UP(10, "系统挂起"),WAITING_FOR_REDIAL(11, "等待重呼"),ACCOUNT_DISABLE(12, "账户禁用"),MAINTAIN(13, "系统维护"); |
| hangUpType       | String        | 系统挂起类型  ACCOUNT_DEBT(0, "账户欠费", "使用的线路账户已欠费"),NO_ROBOT_AVAILABLE(1, "没有可用坐席", "当前没有可用坐席"),PHONE_UNBIND(2, "线路已解绑", "使用的线路已解绑"),LINE_BREAKDOWN(3, "线路故障", "使用的线路状态均为故障"),AVAILABLE_ROBOT_NOT_ENOUGH(4,"有效坐席数不足","有效坐席数不足，请检查有效AI坐席数量！"); |
| hangUpReason     | String        | 系统挂起原因                                                 |
| completedTask    | Long          | 已完成的任务总量                                             |
| totalTask        | Long          | 任务总数                                                     |
| answeredTask     | Long          | 接通电话总量                                                 |
| ablevelCustomer  | Long          | AB类客户数量                                                 |
| msg              | String        | 信息                                                         |

  ##执行（开始，暂停）所有任务

###功能说明：

通过接口可以执行（开始，暂停）所有任务

> 入参JSON实例

```
{
        "operation": "PAUSE",                     
        "executable": [                         
          {
                            "robotCallJobId":33,                              
                            "robotCallJobName":"熊隆祥重新添加到拨打任务调试", 
                            "createTime":"2018-10-11 11:21:36",                
                            "createUserName":"超管",                           
                            "status":"NOT_STARTED",                         
                            "hangUpType":"PHONE_UNBIND",                      
                            "hangUpReason":"使用的线路已解绑",                 
                            "statsInfo":{                                     
                                "robotCallJobId":33,                           
                                "completedTask":1,                             
                                "totalTask":1，                               
                                "answeredTask":1,                             
                                "ablevelCustomer"：1                          
                            }
           }
        ]
      }

```

> JSON响应实例：

```
{
        "code": 200,
        "data":
          {
            "robotCallJobId": 56,                          
            "robotCallJobName": "lxc-测试1",               
            "msg": "该任务状态(已完成)不可开始"           
          }
        ],
        "requestId": "HYDMKHZF",
        "resultMsg": "操作成功",
        "errorStackTrace": null
      }

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/executeJobs

###请求方法：

POST

###请求参数:

| 参数名           | 类型          | 是否必须 | 描述                                                         | 实例                |
| ---------------- | ------------- | -------- | ------------------------------------------------------------ | ------------------- |
| operation        | String        | 是       | 操作类型                                                     | PAUSE               |
| executable       | List          | 是       | 操作任务                                                     |                     |
| robotCallJobId   | Long          | 否       | 任务id                                                       | 1                   |
| robotCallJobName | String        | 否       | 任务名                                                       | 测试任务            |
| createTime       | LocalDateTime | 否       | 创建时间                                                     | 2018-10-11 11:21:36 |
| createUserName   | String        | 否       | 任务创建人                                                   | jack                |
| status           | String        | 否       | 任务状态，NOT_STARTED(0, "未开始"),IN_PROCESS(1, "进行中")，COMPLETED(2, "已完成"),RUNNABLE(3, "可运行"),USER_PAUSE(4, "用户暂停"),SYSTEM_SUSPENDED(5, "系统暂停")，TERMINATE(6, "已终止"),IN_QUEUE(7, "排队中"),SYSTEM_HANG_UP(10, "系统挂起"),WAITING_FOR_REDIAL(11, "等待重呼"),ACCOUNT_DISABLE(12, "账户禁用"),MAINTAIN(13, "系统维护"); | NOT_STARTED         |
| hangUpType       | String        | 否       | 系统挂起类型  ACCOUNT_DEBT(0, "账户欠费", "使用的线路账户已欠费"),NO_ROBOT_AVAILABLE(1, "没有可用坐席", "当前没有可用坐席"),PHONE_UNBIND(2, "线路已解绑", "使用的线路已解绑"),LINE_BREAKDOWN(3, "线路故障", "使用的线路状态均为故障"),AVAILABLE_ROBOT_NOT_ENOUGH(4,"有效坐席数不足","有效坐席数不足，请检查有效AI坐席数量！"); | PHONE_UNBIND        |
| hangUpReason     | String        | 否       | 系统挂起原因                                                 | xxx                 |
| completedTask    | Long          | 否       | 已完成的任务总量                                             | 100                 |
| totalTask        | Long          | 否       | 任务总数                                                     | 1000                |
| answeredTask     | Long          | 否       | 接通电话总量                                                 | 50                  |
| ablevelCustomer  | Long          | 否       | AB类客户数量                                                 | 10                  |

###响应：

| 参数名           | 类型    | 描述     |
| ---------------- | ------- | -------- |
| code             | Integer | 响应码   |
| requestId        | String  | 请求Id   |
| resultMsg        | String  | 响应说明 |
| robotCallJobId   | Long    | 任务id   |
| robotCallJobName | String  | 任务名   |
| msg              | String  | 信息     |

  

## 修改任务接口

### 功能说明：

通过此接口可以修改任务 

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
		"wechatConditionAlertLevelCode": [],
        "redialCondition":["CALL_LOSS","NO_ANSWER","BUSY","REFUSED","POWER_OFF","OUT_OF_SERVICE","CAN_NOT_CONNECT","FROM_PHONE_ERROR","SYSTEM_ERROR"],
        "redialInterval":6,
        "redialTimes":1,
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

URL：https://openapi.tanyibot.com/apiOpen/v1/job/modify

### 请求方法：

PATCH

### 请求参数:

| 参数名                        | 类型    | 是否必须                  | 描述                                                         | 实例                                       |
| ----------------------------- | ------- | ------------------------- | ------------------------------------------------------------ | ------------------------------------------ |
| concurrencyQuota              | Integer | 是                        | 并发数（线路类型为手机号的时候可不传）                       | 10                                         |
| jobPhoneNumberIdList          | List    | 是                        | 任务主叫号码列表 tenant_phone_number_id,当类型是手机号的时候他的size代表机器人的个数，当类型非手机号的时候他的size只能是1；如果外呼方式选择的是外呼策略组，则里面内容为外呼策略组的id（size只能为1） | [1,2,3]                                    |
| transferPhoneNumber           | List    | 选择转人工话术时必填      | 转人工号码,触发转人工时轮训号码列表                          | ["1523654789","1758426896"]                |
| name                          | String  | 是                        | 任务名称                                                     | 测试API任务                                |
| mode                          | String  | 是                        | 任务类型 (AUTO, "自动任务"),(MANUAL, "手动任务");            | AUTO                                       |
| startTime                     | String  | 自动任务：是/手动任务：否 | 任务开始时间                                                 | "2017-11-21"                               |
| dailyStartTime                | String  | 是                        | 可拨打开始时间，不可以早于9点                                | 09:00                                      |
| dailyEndTime                  | String  | 是                        | 可拨打结束时间，不可以晚于20点                               | 20:00                                      |
| inactiveTimeList              | List    | 否                        | 不可拨打时间段列表,最大三个不可拨打时段                      | [{"startTime":"12:00", "endTime":"13:00"}] |
| dialogFlowId                  | String  | 是                        | 话术id                                                       | 139                                        |
| csStaffGroupId                | Long    | 是                        | 坐席组id，通过话术API中获取人工介入标识。如果存在人工介入标识，需要传入坐席组Id | 139                                        |
| alertUsers                    | String  | 否                        | 提醒的用户的id列表                                           | [1,2]                                      |
| earlyWarningAlertUsers        | String  | 否                        | 行业预警消息推送人                                           | [1,2]                                      |
| phoneType                     | String  | 是                        | 号码类型 (MOBILE, "手机号码"),(LANDLINE, "固话"),(UNFIXED_CALL, "无主叫"), (CALL_POLICY_GROUP, "外呼策略组") | UNFIXED_CALL                               |
| smsAlertLevel                 | String  | 否                        | 短信推送提醒意向等级                                         | ["A","B"]                                  |
| smsTemplateId                 | Long    | 否                        | 短信模板id                                                   |                                            |
| wechatAlertLevel              | String  | 否                        | 微信推送提醒意向等级                                         | ["A","B"]                                  |
| wechatSendMethod              | String  | 否                        | 微信推送方式（SENDTOALL，全推送），（SENDTOONE，单推送），（SENDTONONE 不推送） | SENDTOALL                                  |
| description                   | String  | 否                        | 备注                                                         | 测试                                       |
| wechatAlertLevelCode          | Integer | 否                        | 微信推送提醒意向等级编码                                     | [0, 1]                                     |
| smsAlertLevelCode             | Integer | 否                        | 短信推送提醒意向等级编码                                     | [0, 1]                                     |
| wechatConditionAlertLevelCode | Integer | 否                        | 微信条件推送提醒意向等级编码                                 | [0, 1]                                     |
| redialCondition               | Set     | 选择自动重拨时必填        | 重拨条件(CALL_LOSS,"呼损客户"),(NO_ANSWER,"无应答"),(BUSY,"忙线中"),(REFUSED,"拒接"),(POWER_OFF,"关机"),(OUT_OF_SERVICE,"停机"),(CAN_NOT_CONNECT,“无法接通“),(FROM_PHONE_ERROR,"主叫欠费"),(SYSTEM_ERROR,"外呼失败") | ["CALL_LOSS"]                              |
| redialInterval                | Integer | 选择自动重拨时必填        | 重拨间隔(分钟，取值范围6分钟~24 x 60分钟)                    | 6                                          |
| redialTimes                   | Integer | 选择自动重拨时必填        | 重拨次数(取值范围1~10）                                      | 6                                          |

### 响应：

| 参数名         | 类型    | 描述             |
| -------------- | ------- | ---------------- |
| code           | Integer | 响应码           |
| robotCallJobId | Long    | 刚刚创建的任务ID |
| requestId      | String  | 请求Id           |
| resultMsg      | String  | 响应说明         |

##已呼客户列表重新添加客户到呼叫任务

###功能说明：

通过接口可以在已呼客户列表中重新添加客户到呼叫任务

> 入参JSON实例

```
{
             "robotCallJobId": 1,         
         	  "customerPersonIds": [       
         	   		1919005, 1919006
         	   ],
         	 "lastCallRecord": true,              
             "searchWords": "12323424",           
             "customerGroupId": 1,              
             "resultStatuses": ["ANSWERED", "REFUSED"], 
             "intentLevels": [                
               "A"
             ],
             "followStatus": "AI_INITIAL_VISIT",  
             "dialogFlowId": 2,                   
             "earliestCreationTime" :  "2018-07-25" ,          
             "latestCreationTime" :  "2018-07-30" ,            
       }

```

> JSON响应实例：

```
{
          "code": 200,
          "data": null,
          "requestId": "WYPNOVHI",
          "resultMsg": "添加成功",
          "errorStackTrace": null
      }

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/reAddCustomerToJob

###请求方法：

POST

###请求参数:

| 参数名               | 类型       | 是否必须 | 描述                                                         | 实例                                      |
| -------------------- | ---------- | -------- | ------------------------------------------------------------ | ----------------------------------------- |
| robotCallJobId       | Long       | 是       | 任务Id                                                       | 1                                         |
| customerPersonIds    | List<Long> | 是       | 需要添加的客户id                                             | customerPersonIds: [  1919005, 1919006  ] |
| lastCallRecord       | Boolean    | 否       | 是否过滤重复通话记录只显示最近的一条                         | true                                      |
| searchWords          | String     | 否       | 通过手机号码或者用户名通话记录ID模糊搜索筛选                 | xxx                                       |
| customerGroupId      | Long       | 否       | 分组id                                                       | 1                                         |
| resultStatuses       | List       | 否       | ANSWERED(0, "已接听", null), NO_ANSWER(1, "无应答", "呼叫号码未接听"), BUSY(2, "忙线中", "呼叫号码占线"), POWER_OFF(3, "关机", "呼叫号码关机"), OUT_OF_SERVICE(4, "停机", "呼叫号码停机"), REFUSED(5, "拒接", "呼叫号码拒接"), VACANT_NUMBER(6, "空号", "呼叫的号码是空号"), CAN_NOT_CONNECT(7, "无法接通", "呼叫的号码无法接通"),                 FROM_PHONE_ERROR(8, "主叫停机", "主叫号码不可用"),                   SYSTEM_ERROR(9, "系统错误", "外呼失败，系统错误"),                             CALL_LOSS(10,"多并发呼损","等待服务中用户挂断"), TRANSFER_ARTIFICIAL(11,"转人工呼损","等待转人工服务中用户挂断"); | ["ANSWERED", "REFUSED"]                   |
| intentLevels         | List       | 否       | 意向等级A(0, "A级(较强)"), B(1, "B级(一般)"), C(2, "C级(无法判断)"), D(3, "D级(很少)"), E(4, "E级别(需要再次跟进)"), F(5, "F级别(无需再次跟进)"); | ["A","B"]                                 |
| followStatus         | String     | 否       | 跟进状态CLUE(0, "线索"), AI_INITIAL_VISIT(1, "AI初访"), PEOPLE_INITIAL_VISIT(2, "人工初访"), AI_FOLLOW_UP(3, "AI持续跟进"), PEOPLE_FOLLOW_UP(4, "人工持续跟进"), QUOTE(5, "报价"), DEAL(6, "成交"), LOSS(7, "流失"); | AI_INITIAL_VISIT                          |
| dialogFlowId         | Long       | 否       | 话术ID                                                       | 1                                         |
| earliestCreationTime | LocalDate  | 否       | 最早创建时间，日期标准格式，请不要包含时间。可以为空         | 2018-07-25                                |
| latestCreationTime   | LocalDate  | 否       | 最晚创建时间，日期标准格式，请不要包含时间。可以为空         | 2018-07-30                                |

###响应：

| 参数名    | 类型    | 描述     |
| --------- | ------- | -------- |
| code      | Integer | 响应码   |
| requestId | String  | 请求Id   |
| resultMsg | String  | 响应说明 |

  

## 获取任务统计相关信息（总量，完成量）

###功能说明：

通过接口可以获取任务统计相关信息（总量，完成量）

> 入参JSON实例

```
{
	 [                                  
        "1017",
        "1014",
        "1013"
      ]
}

```

> JSON响应实例：

```
{
        "code": 200,
        "data": {
          "1013": {            
            "taskTotal": 0,     
            "taskCompleted": 0 
          },
          "1014": {
            "taskTotal": 31455,
            "taskCompleted": 0
          },
          "1017": {
            "taskTotal": 1,
            "taskCompleted": 1
          }
        },
        "requestId": "IOKMTMXV",
        "resultMsg": "获取成功",
        "errorStackTrace": null
      }

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/job/getJobStatsInfoList

###请求方法：

POST

###请求参数:

| 参数名         | 类型 | 是否必须 | 描述         | 实例                          |
| -------------- | ---- | -------- | ------------ | ----------------------------- |
| robotCallJobId | List | 是       | 任务id的列表 | [ "1017",  "1014",  "1013"  ] |

###响应：

| 参数名        | 类型    | 描述       |
| ------------- | ------- | ---------- |
| code          | Integer | 响应码     |
| requestId     | String  | 请求Id     |
| resultMsg     | String  | 响应说明   |
| taskTotal     | Long    | 总任务     |
| taskCompleted | Long    | 完成任务量 |
