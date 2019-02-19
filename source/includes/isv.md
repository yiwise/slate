# isv对象操作

##修改ISV对象的公司签名和回调地址
 
###功能说明：
 
 通过此接口可以修改ISV对象的公司签名和回调地址
 
 >入参JSON实例
 
 ```
 
{
    "tenantSign": "yiwise",
    "callbackUrl": "http:999999999"
}
 
 ```
 
 >JSON响应实例：
 
 ```
 {
    "code":200,
    "data":null,
    "requestId":"FVKXTCDG",
    "resultMsg":"修改成功",
    "errorStackTrace":null
 }
 ```
 
###请求：
 
 URL：https://openapi.tanyibot.com/apiOpen/v1/isv/updateIsvInfo
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 实例 
 --------- | ------- |------- | ------ |----------
  tenantSign| String| 是 |客户签名| yiwise |
  callbackUrl| String| 否 | 回调URL| http://www.baidu.com |
  
  
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|integer | 响应码 |
  requestId| String | 请求Id |
  resultMsg| String | 响应说明 |
