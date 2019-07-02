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

URL：https://openapi.tanyibot.com/apiOpen/v1/tenant/getTenant

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
    "tenantPhoneNumberId": 276,
    "phoneNumber": "0000000000",
    "phoneName": "0000000000",
    "phoneType": "MOBILE",
    "localBillRate": 60,
    "otherBillRate": 60,
    "callOutIndustry": "FINANCE",
    "areaCode": "0571",
    "province": "浙江",
    "city": "杭州",
  }],
  "requestId": "ILNBEQJF",
  "resultMsg": "获取成功",
  "errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/phone/getPhoneList

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 tenantPhoneNumberId|Long | 电话id |
 phoneNumber| String | 电话号码 |
 phoneName| String | 电话号码名称 |
 phoneType| String | (MOBILE, "手机"),(LANDLINE, "固话"),(UNFIXED_CALL, "无主叫固话")|
 localBillRate| String | 本地话费（单位：厘）|
 otherBillRate| String | 外地话费（单位：厘）|
 callOutIndustry| String | (FINANCE, "金融"),(OTHER, "其他")|
 areaCode| String | 归属地区号|
 province| String | 归属地省|
 city| String | 归属地市|
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
		"dialogFlowId": 96,
		"name": "金融理财--行业体验demo"
	}, {
		"dialogFlowId": 136,
		"name": "测试变量"
	}],
	"requestId": "NSLARYGU",
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
 code|integer | 响应码 |
 dialogFlowId|Integer | 机器人话术id |
 name| String | 机器人话术名称 |
 industry| String | 一级行业类型（枚举在枚举说明中） |
 subIndustry| String | 二级行业类型（枚举在枚举说明中） |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

##话单计费统计

###功能说明：

通过接口可以获取公司话单计费统计 

> JSON响应实例：

```
{
    "code": 200,
    "data": {
        "callCostStatsPhoneNumberList": [
            {
                "localDate": "2019-05-23",
                "phoneNumberId": 1,
                "phoneNumberName": "057128204503-1",
                "local": false,
                "answeredCall": 4,
                "chatTimeList": 607,
                "callCostList": 130000,
                "phoneNumber": "057128204503-1",
                "phoneType": "LANDLINE",
                "tenantPhoneNumberStatus": 1,
                "myChatTimeList": 11,
                "myCallCostList": 130
            }
        ],
        "callCostStatsPhoneNumberChat": {
            "2019-04-30": null,
            "2019-05-01": null,
            "2019-05-02": null,
            "2019-05-03": null,
            "2019-05-04": null,
            "2019-05-05": null,
            "2019-05-06": null,
            "2019-05-07": null,
            "2019-05-08": null,
            "2019-05-09": null,
            "2019-05-10": null,
            "2019-05-11": null,
            "2019-05-12": null,
            "2019-05-13": null,
            "2019-05-14": null,
            "2019-05-15": null,
            "2019-05-16": null,
            "2019-05-17": null,
            "2019-05-18": null,
            "2019-05-19": null,
            "2019-05-20": null,
            "2019-05-21": null,
            "2019-05-22": null,
            "2019-05-23": [
                {
                    "localDate": "2019-05-23",
                    "phoneNumberId": 1,
                    "phoneNumberName": "057128204503-1",
                    "local": false,
                    "answeredCall": 4,
                    "chatTimeList": 607,
                    "callCostList": 130000,
                    "phoneNumber": "057128204503-1",
                    "phoneType": "LANDLINE",
                    "tenantPhoneNumberStatus": 1,
                    "myChatTimeList": 11,
                    "myCallCostList": 130
                }
            ],
            "2019-05-24": null,
            "2019-05-25": null,
            "2019-05-26": null,
            "2019-05-27": null,
            "2019-05-28": null,
            "2019-05-29": null,
            "2019-05-30": null
        },
        "smsCostInfoList": [
             "date" :"2019-05-23",  
             "smsAmount":1 ,         
             "smsBillAmount" :1,     
             "smsCost" : 100 ,       
        ],
        "totalPhoneNumberLocal": [
            {
                "phoneNumberId": 1,
                "phoneNumberName": "057128204503-1",
                "phoneNumber": "057128204503-1",
                "local": false,
                "phoneType": "LANDLINE",
                "tenantPhoneNumberStatus": 1
            }
        ]
    },
    "requestId": "REIHDOFP",
    "resultMsg": "获取成功",
    "errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/callStats/callCostStatsInfo

###请求方法：

GET

###请求参数:

| 参数名         | 类型    | 是否必须 | 描述                                                         | 实例            |
| -------------- | ------- | -------- | ------------------------------------------------------------ | --------------- |
| startDate      | String  | 是       | 开始日期                                                     | 2019-04-30      |
| endDate        | String  | 是       | 结束日期                                                     | 2019-05-30      |
| local          | Boolean | 否       | 是否本地                                                     | true            |
| phoneNumberId  | Long    | 否       | 线路ID                                                       | 1               |
| type           | Integer | 否       | 类型：0-AI 1-人工外呼 2-ai接待  3-人工接待 4-IVR接待，默认0-AI，默认为0 | 0               |
| callInCostType | String  | 否       | ai接待和人工接待的时候才需要传此参数；LOCAL_CALL_BILL 本地呼入计费, OTHER_CALL_BILL 外地呼入计费, LINE_MONTHLY_BILL 线路月租费用，NONE ："无费用"); | LOCAL_CALL_BILL |

###响应：

| 参数名                  | 类型      | 描述                                                         |
| ----------------------- | --------- | ------------------------------------------------------------ |
| code                    | integer   | 响应码                                                       |
| localDate               | String    | 时间，年月日                                                 |
| phoneNumberId           | Long      | 线路id                                                       |
| phoneNumberName         | String    | 线路名                                                       |
| local                   | Boolean   | 是否本地                                                     |
| answeredCall            | Long      | 拨通数                                                       |
| chatTimeList            | Long      | 通话时长，单位为秒                                           |
| billChatTimeList        | Long      | 通话计费时长，单位为分钟                                         |
| callCostList            | Long      | 话费，单位分                                                 |
| phoneNumber             | String    | 线路号码                                                     |
| phoneType               | String    | 线路类型，LANDLINE(1, "L", "固话"),UNFIXED_CALL(2, "U", "无主叫"),MOBILE(0, "M", "手机号码"),CRM_VERBAL_TRICK_TRAINING_CALLER(3, "CVR", "CRM训练主叫账号"),CRM_VERBAL_TRICK_TRAINING_CALLED(4, "CVD", "CRM训练被叫账号"),VOIP_DEVICE(5, "D", "网关设备"),CS_SEAT(11, "CS_SEAT","人工外呼"),MESSAGE(12,"MES","短信"),CALL_POLICY_GROUP(13, "CALL_POLICY_GROUP", "外呼策略组") |
| tenantPhoneNumberStatus | Integer   | 线路是否解绑                                                 |
| myChatTimeList          | long      | 通话时长，单位为分钟                                         |
| myCallCostList          | double    | 话费,单位元                                                  |
| date                    | LocalDate | 日期                                                         |
| smsAmount               | Long      | 短信数量                                                     |
| smsBillAmount           | Long      | 有效计费数                                                   |
| smsCost                 | Long      | 短信费,单位分                                                |
| requestId               | String    | 请求Id                                                       |
| resultMsg               | String    | 响应说明                                                     |

