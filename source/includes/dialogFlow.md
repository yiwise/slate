# 话术接口

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


##获取话术主流程word文档

###功能说明：

通过接口可以获取指定话术的主流程文档

>JSON响应实例：

```
 {
     "code": 200,
     "data": "https://ai-call-platform-daily.oss-cn-hangzhou.aliyuncs.com/DialogFlowWordFile/dialogFlow_1608.doc?Expires=1559704998&OSSAccessKeyId=LTAICuX7MOmHW6Oy&Signature=2ABiu1yf8VbGc%2B6rIO%2FUPFcQJCs%3D",
     "requestId": "QKFCMKOY",
     "resultMsg": "获取成功",
     "errorStackTrace": null
 }

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/dialogFlow/exportDialogFlowWordDoc

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
 data |String | 导出文档的下载链接 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
