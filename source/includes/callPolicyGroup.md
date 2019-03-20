# 外呼策略组接口

##获取外呼策略组选择接口

###功能说明：

通过此接口可以获取外呼策略组id和名称对应的键值对列表

>JSON响应实例：

```
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

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/policyGroup/getIdAndNamePairList

###请求方法：

GET


###请求参数:

无

###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|Integer | 响应码 |
 callPolicyGroupId|String | 外呼策略组id |
 tenantId| Long | 公司Id |
 name| String | 外呼策略组名称 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |

