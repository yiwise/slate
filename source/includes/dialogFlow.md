# 话术接口

##获取话术列表接口

###功能说明：

通过此接口可以获取用户所有的话术信息

>JSON响应实例：

```
{
	"code": 200,
	"data": [
		{
		"dialogFlowId": 1,
		"name": "话术标题"
		}
	],
	"requestId": "VCWAHVEJ",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/dialogFlow/getDialogFlowList

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 dialogFlowId |Long | 话术Id |
 name | String | 话术名称 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |


##获取话术中存在人工介入和转人工等标识

###功能说明：

通过接口可以获取指定话术的标识


>JSON响应实例：

```
 {
     "code": 200,
     "data": {
         "dialogFlowId": 358,
         "placeholderExist": true,
         "jumpToHumanServiceExist": false,
         "humanInterventionExist": false
     },
     "requestId": "QKFCMKOY",
     "resultMsg": "获取成功",
     "errorStackTrace": null
 }

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/dialogFlow/getDialogFlowCallJobRelatedInfo

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例
--------- | ------- |------- | ------ |----------
 dialogFlowId| Long| 是 |话术ID| 0 |

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 placeholderExist | boolean |是否有变量名 |
 jumpToHumanServiceExist | boolean |是否转人工标识 |
 humanInterventionExist | boolean |是否有人工介入标识 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

