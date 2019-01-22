# 意向标签组接口

##获取已使用的意向标签组列表接口

###功能说明：

通过此接口可以获取已使用的所有意向标签组

>JSON响应实例：

```
{
	"code": 200,
	"data": [
	  {
	    "intentLevelTagId": 0,
	    "name": "内置意向分类标签"
	  }, {
	    "intentLevelTagId": 1,
      "name": "自定义标签分组"
	  }
	],
	"requestId": "VCWAHVEJ",
	"resultMsg": "获取成功",
	"errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/intentLevelTag/getUsedIntentLevelTagList

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 intentLevelTagId|Long | 意向标签分组Id |
 name|String | 意向标签分组名称 |


##获取意向标签内容

###功能说明：

通过接口可以获取指定意向标签分组的内容


>JSON响应实例：

```
{
  "code": 200,
  "data": {
    "intentLevelTagId": 0,
    "name": "内置意向分类标签",
    "details": [
      {
        "code": 0,
        "name": "A类"
      },
      {
       "code": 1,
        "name": "B类"
      },
      {
        "code": 2,
        "name": "C类"
      },
      {
        "code": 3,
        "name": "D类"
      },
      {
        "code": 4,
        "name": "E类"
      },
      {
        "code": 5,
        "name": "F类"
      }
    ]
  },
  "requestId": "ILNBEQJF",
  "resultMsg": "获取成功",
  "errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/intentLevelTag/getIntentLevelTag

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例 
--------- | ------- |------- | ------ |----------
 intentLevelTagId| Long| 是 |标签分组Id| 0 |

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 intentLevelTagId|Long | 意向标签分组Id |
 name|String | 意向标签分组名称 |
 code| Integer | 意向等级 |
 name| String | 意向名称 |
 
