# 人工坐席接口

##获取人工坐席列表接口

###功能说明：

通过此接口可以获取用户所有的有效坐席组列表信息

>JSON响应实例：

```
{
    "code": 200,
    "data": {
        "number": 1,
        "pageSize": 20,
        "totalElements": 1,
        "pages": 1,
        "content": [
            {
                "createUserId": null,
                "updateUserId": null,
                "createTime": "2019-01-11 17:09:04",
                "updateTime": "2019-01-11 17:09:04",
                "csStaffGroupId": 1,
                "groupName": "CS坐席组1",
                "dialogFlowId": 1,
                "groupCapacity": 10,
                "tenantId": 756,
                "groupType": "CS",
                "enabledStatus": "ENABLE",
                "dialogFlowName": "内置"
                "csStaffList": null
            }
        ]
    },
    "requestId": "EJKEIHZQ",
    "resultMsg": "查询成功",
    "errorStackTrace": null
}

```

###请求：

URL：https://openapi.tanyibot.com/apiOpen/v1/csRobot/staffGroupList

###请求方法：

GET


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 实例
--------- | ------- |------- | ------ |----------
 pageNum| Integer| 是 |页码| 0 |
 pageSize| Integer| 是 |每页记录数| 0 |


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|integer | 响应码 |
  number| Integer | 第几页 |
  pageSize| Integer | 每页页面条数 |
  totalElements| Integer | 数据总条数 |
  pages| Integer | 页面总数 |
 csStaffGroupId | Long | 坐席组Id |
 groupName | String | 坐席组名称 |
 requestId| String | 请求Id |
 resultMsg| String | 响应说明 |
