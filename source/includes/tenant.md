# 公司信息接口

##获取公司列表接口

###功能说明：

通过此接口可以获取用户所有的公司信息

>JSON响应实例：

```
{
	"code": 200,
	"data": {
		"tenantId": 1,
		"tenantName": "杭州一知智能科技有限公司"
	},
	"requestId": "VCWAHVEJ",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://crm.tanyibot.com/apiOpen/v1/tenant/getTenant

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 tenantName|String | 公司名称 |
 tenantId| Long | 公司Id |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |


##获取公司的主叫电话列表接口

###功能说明：

通过接口可以获取指定公司的所有主叫电话的列表


>JSON响应实例：

```
{
  "code": 200,
  "data": [{
    "userPhoneId": 276,
    "phone": "0000000000",
    "phoneName": "0000000000",
    "phoneType": "MOBILE"
  }],
  "requestId": "ILNBEQJF",
  "resultMsg": "获取成功",
  "errorStackTrace": null
}

```

###请求：

URL：https://crm.tanyibot.com/apiOpen/v1/phone/getPhoneList

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 tenantPhoneNumberId|Long | 电话id |
 phone| String | 电话号码 |
 phoneName| String | 电话号码名称 |
 phoneType| String | (MOBILE, "手机"),(LANDLINE, "固话"),(UNFIXED_CALL, "无主叫固话")|
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

##获取公司的机器人话术列表接口

###功能说明：

通过接口可以获取指定公司的所有配置完成的机器人话术 

>JSON响应实例：

```
{
	"code": 200,
	"data": [{
		"robotDialogFlowId": 96,
		"name": "金融理财--行业体验demo"
	}, {
		"robotDialogFlowId": 136,
		"name": "测试变量"
	}],
	"requestId": "NSLARYGU",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://crm.tanyibot.com/apiOpen/v1/dialogFlow/getDialogFlowList

###请求方法：

GET

###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 robotDialogFlowId|Integer | 机器人话术id |
 name| String | 机器人话术名称 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

