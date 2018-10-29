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
		"companyName": "杭州一知智能科技有限公司"
	},
	"requestId": "VCWAHVEJ",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/company/getCompanies

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 companyName|String | 公司名称 |
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
    "phoneType": "MOBILE",
    "concurrency": 2
  }],
  "requestId": "ILNBEQJF",
  "resultMsg": "获取成功",
  "errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/company/getPhones

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
 userPhoneId|Integer | 电话id |
 phone| String | 电话号码 |
 phoneName| String | 电话号码名称 |
 phoneType| Integer | 手机(MOBILE, "手机"),阿里云固话(LANDLINE, "固话"),无主叫(UNFIXED_CALL, "无主叫固话"),训练主叫账号(VERBAL_TRICK_TRAINING_CALLER, "训练主叫账号"),训练被叫账号(VERBAL_TRICK_TRAINING_CALLED, "训练被叫账号"),网关设备(VOIP_DEVICE, "网关设备"), |
 concurrency| Integer | 已经使用并发数 |
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
		"name": "金融理财--行业体验demo",
		"type": "NORMAL",
		"industry": {
			"name": "FINANCE",
			"desc": "金融类"
		},
		"subIndustry": {
			"name": "FINICING",
			"desc": "理财"
		},
		"familyNameTemplateId": null,
		"status": "DRAFT"
	}, {
		"robotDialogFlowId": 136,
		"name": "测试变量",
		"type": "NORMAL",
		"industry": {
			"name": "OTHER",
			"desc": "其他产品推广"
		},
		"subIndustry": {
			"name": "OTHER",
			"desc": "其他产品推广"
		},
		"familyNameTemplateId": null,
		"status": "APPROVED"
	}],
	"requestId": "NSLARYGU",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/company/getRobots

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
 type| Integer | 机器人话术类型 TEMPLATE(0, "模板"),DEMO(1, "展示"),NORMAL(2, "普通")|
 status| Integer | 状态 DRAFT(0, "编辑中"),PENDING_APPROVAL(1, "等待审核"),REJECTED(2, "拒绝"),APPROVED(3, "审核通过"); |
 industry| object | 一级行业类型 |
 subIndustry| String | 二级行业类型 |
 familyNameTemplateId| Long | 百家姓模板id |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

