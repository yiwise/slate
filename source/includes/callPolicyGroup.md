# 外呼策略组接口

## 获取外呼策略组选择接口

### 功能说明：

通过此接口可以获取外呼策略组id和名称对应的键值对列表

> JSON 响应实例：

```json
{
    "code":200,
    "data":[
        {
            "callPolicyGroupId":18,
            "tenantId":123,
            "name":"杭州线路集合"
        }
    ],
    "requestId":"xxxxxx",
    "resultMsg":"执行成功",
    "errorStackTrace":null
}

```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/policyGroup/getIdAndNamePairList

### 请求方法：

GET

### 请求参数：

无

### 响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|code | 响应码 |
 callPolicyGroupId|String | 外呼策略组id |
 tenantId| Long | 公司Id |
 name| String | 外呼策略组名称 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

## 获取外呼策略组列表接口

### 功能说明：

通过此接口可以获取用户所有的外呼策略组信息

> JSON 响应实例：

```json
{
    "code": 200,
    "data": [
        {
            "createUserId": 1,
            "updateUserId": 1,
            "createTime": "2019-05-08 18:36:36",
            "updateTime": "2019-05-08 18:41:31",
            "callPolicyGroupId": 62,
            "tenantId": 0,
            "name": "openapi-test1",
            "remark": null,
            "phoneType": "NOT_MOBILE",
            "dispatchType": "LOCATION_MATCH_FIRST",
            "detailList": [
                {
                    "createUserId": 1,
                    "updateUserId": 1,
                    "createTime": "2019-05-08 18:41:31",
                    "updateTime": "2019-05-08 18:41:31",
                    "callPolicyGroupDetailId": 378,
                    "callPolicyGroupId": 62,
                    "tenantId": 0,
                    "phoneNumberId": 433,
                    "tenantPhoneNumberId": 743,
                    "sort": 1,
                    "phoneNumberInfo": {
                        "createTime": null,
                        "updateTime": null,
                        "tenantPhoneNumberId": 743,
                        "localBillRate": 230,
                        "otherBillRate": 500,
                        "tenantId": 0,
                        "concurrency": 0,
                        "phoneNumberId": 433,
                        "phoneType": "LANDLINE",
                        "accountFare": 10000,
                        "enabledStatus": 1,
                        "monthlyBillRate": 0,
                        "callInLocalBillRate": 0,
                        "callInOtherBillRate": 0,
                        "callInBillMode": "MONTHLY",
                        "lastHeartBeatTime": null,
                        "concurrenceLimit": 0,
                        "phoneNumber": "123456789",
                        "phoneName": "",
                        "remark": "\n再等一会in",
                        "sipAccount": "******",
                        "province": null,
                        "city": null,
                        "ownerName": "杭州一知智能科技有限公司",
                        "locationDisplayType": "DEFAULT",
                        "ownerTenantId": 0
                    },
                    "lineStatus": {
                        "status": "IDLE",
                        "isLineAvailable": true,
                        "hint": null,
                        "occupiedJobList": null
                    }
                }
            ]
        }
    ],
    "requestId": "IMNBPIIF",
    "resultMsg": "执行成功",
    "errorStackTrace": null
}
```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/policyGroup/list

### 请求方法：

GET

### 请求参数:

无

### 响应：

|          参数名          |      类型      | 描述                                                                                                                                                                       |
|:-----------------------:|:-------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| code                    |    Integer    | 响应码                                                                                                                                                                      |
| callPolicyGroupId       |      Long     | 外呼策略组ID                                                                                                                                                               |
| tenantId                |      Long     | 公司ID                                                                                                                                                                     |
| name                    |     String    | 外呼策略组名称                                                                                                                                                             |
| remark                  |     String    | 备注                                                                                                                                                                       |
| phoneType               |     String    | 外呼策略组类型                                                                                                                                                             |
| dispatchType            |     String    | 优先级策略，(SORT_FIRST, "排序优先级优先"),(LOCATION_MATCH_FIRST, "归属地匹配优先")                                                                                        |
| callPolicyGroupDetailId |      Long     | 外呼策略组详情ID（一条详情记录对应一条线路）                                                                                                                               |
| phoneNumberId           |      Long     | 线路ID（代表实际的线路）                                                                                                                                                   |
| tenantPhoneNumberId     |      Long     | 用户线路ID（代表绑给用户的虚拟线路）                                                                                                                                       |
| sort                    |    Integer    | 优先级（越小越高）                                                                                                                                                         |
| localBillRate           |      Long     | 本地外呼费率，单位（厘）                                                                                                                                                   |
| otherBillRate           |      Long     | 外地外呼费率，单位（厘）                                                                                                                                                   |
| concurrency             |    Integer    | 线路当前的并发量                                                                                                                                                           |
| phoneType               |     String    | 电话类型 (MOBILE，"手机"),(LANDLINE，"固话"),(UNFIXED_CALL，"无主叫"),(VOIP_DEVICE，"网关设备"), (CS_SEAT，"人工外呼"),(MESSAGE，"短信"),(CALL_POLICY_GROUP，"外呼策略组") |
| accountFare             |      Long     | 账户余额，单位（厘）                                                                                                                                                       |
| enabledStatus           |    Integer    | 是否启用，1为启用，0为禁用                                                                                                                                                 |
| monthlyBillRate         |      Long     | 呼入月租费率，单位（厘）                                                                                                                                                   |
| callInLocalBillRate     |      Long     | 呼入本地通话费用，单位（厘）                                                                                                                                               |
| callInOtherBillRate     |      Long     | 呼入外地通话费用，单位（厘）                                                                                                                                               |
| callInBillMode          |     String    | 呼入计费方式 (MONTHLY，"按月租计费"),(CHAT_TIME，"按通话时长(分钟)计费")                                                                                                   |
| lastHeartBeatTime       | LocalDateTime | 最后外呼时间                                                                                                                                                               |
| concurrenceLimit        |    Integer    | 并发数限制                                                                                                                                                                 |
| phoneNumber             |     String    | 电话号码                                                                                                                                                                   |
| phoneName               |     String    | 线路名称                                                                                                                                                                   |
| remark                  |     String    | 备注                                                                                                                                                                       |
| sipAccount              |     String    | SIP账号                                                                                                                                                                    |
| province                |     String    | 省份                                                                                                                                                                       |
| city                    |     String    | 城市                                                                                                                                                                       |
| ownerName               |     String    | 归属公司名称                                                                                                                                                               |
| locationDisplayType     |     String    | 线路归属地显示方式（DEFAULT，"默认显示配置归属地"）,（RANDOM，"全国随机显示"）,（NO_DISPLAY，"不显示"）                                                                             |
| ownerTenantId           |      Long     | 归属公司ID                                                                                                                                                                 |
| requestId               |     String    | 请求Id                                                                                                                                                                 |
| resultMsg               |     String    | 响应说明                                                                                                                                                                 |

## 创建外呼策略组接口

### 功能说明：

创建新的外呼策略组

> JSON 入参实例：

```json
{
    "name": "openapi-test",
    "remark": null,
    "dispatchType": "LOCATION_MATCH_FIRST",
    "detailList": [
        {
            "tenantPhoneNumberId": 743
        }
    ]
}
```

> JSON 响应实例：

```json
{
	"code": 200,
	"data": null,
	"requestId": "RKXNIQAF",
	"resultMsg": "创建成功",
	"errorStackTrace": null
}
```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/policyGroup/create

### 请求方法：

POST

### 请求参数:

|        参数名       |  类型  | 是否必须 | 描述                                                                                 | 实例                   |
|:-------------------:|:------:|:--------:|--------------------------------------------------------------------------------------|------------------------|
| name                | String |    是    | 外呼策略组名称                                                                       | "openapi-test1"        |
| remark              | String |    否    | 备注                                                                                 | "hangzhou-2019"        |
| dispatchType        | String |    是    | 优先级策略，(SORT_FIRST, "排序优先级优先"),(LOCATION_MATCH_FIRST, "归属地匹配优先"); | "LOCATION_MATCH_FIRST" |
| tenantPhoneNumberId |  Long  |    是    | 用户线路ID                                                                           | 743                    |

### 响应：

|   参数名  |   类型  |   描述   |
|:---------:|:-------:|:--------:|
|    code   | Integer | 响应码   |
| requestId |  String | 请求Id   |
| resultMsg |  String | 响应说明 |

## 更新外呼策略组接口

### 功能说明：

更新新的外呼策略组

> JSON 入参实例：

```json
{
    "callPolicyGroupId": 62,
    "name": "openapi-test1",
    "remark": null,
    "dispatchType": "LOCATION_MATCH_FIRST",
    "detailList": [
        {
            "tenantPhoneNumberId": 743
        }
    ]
}
```

> JSON 响应实例：

```json
{
	"code": 200,
	"data": null,
	"requestId": "RKXNIQAF",
	"resultMsg": "更新成功",
	"errorStackTrace": null
}
```

### 请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/policyGroup/update

### 请求方法：

POST

### 请求参数:

|        参数名       |  类型  | 是否必须 | 描述                                                                                 | 实例                   |
|:-------------------:|:------:|:--------:|--------------------------------------------------------------------------------------|------------------------|
| callPolicyGroupId   |  Long  |    是    | 外呼策略组ID                                                                         | 62                     |
| name                | String |    否    | 外呼策略组名称                                                                       | "openapi-test1"        |
| remark              | String |    否    | 备注                                                                                 | "hangzhou-2019"        |
| dispatchType        | String |    否    | 优先级策略，(SORT_FIRST, "排序优先级优先"),(LOCATION_MATCH_FIRST, "归属地匹配优先"); | "LOCATION_MATCH_FIRST" |
| tenantPhoneNumberId |  Long  |    是    | 用户线路ID                                                                           | 743                    |

### 响应：

|   参数名   |   类型   |   描述   |
|:---------:|:-------:|:--------:|
|    code   | Integer | 响应码   |
| requestId |  String | 请求Id   |
| resultMsg |  String | 响应说明 |
