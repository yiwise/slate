# 开发引导

## 调用说明

### 主动调用 

这种调用方式是客户主动调用接口获取数据或实现功能；

主动调用需在请求头传入 appKey、appSecret、tenantSign（公司签名，后期提供修改）、时间戳 timestamp 和验签字段 signature 用于权限校验；

如下图所示：

![](../images/headers.png)

注意：请在开发对接程序前联系探意技术支持进行注册，如果您还未签约，请先签约开通账户。

### 方法回调 

这种调用方式是当达到预设条件如：任务完成或通话结束时，由探意主动向指定地址发送信息；

注意：请在开发前自主配置好回调地址。

探意机器人 API 是使用 HTTP 并遵循 RESTful 原则设计的 Web 服务接口；

您可以使用几乎任何客户端和任何编程语言与 RESTful API 进行交互。

通过发送简单的 HTTP 请求就可以轻松接入使用。

## 权限认证

> 认证密钥样例

```java
  APP_KEY = "WtSMaXXXXXXXXtvy";
  APP_SECRET = "aXSFnnZbHXXXXXXXXXXXXXXXMguz1Q";    
  TENANT_SIGN = "yiwisexxxx";    
```

API认证采用SHA256加密算法进行加密，使用时间戳、APP_KEY、APP_SECRET、VERSION（当前版本的VERSION=v1）和 TENANT_SIGN（公司签名，后期提供修改）共同生成一个验签字段signature。

目前已有完成JAVA版的样例，具体实现请下载SDK查阅。


> 请在API样例 `openapidemo` 中替换为自己的APP_KEY、APP_SECRET和 TENANT_SIGN.

探意为确保您的账户和信息安全，请在开发对接程序前联系探意技术支持注册接口调用专属密钥。

<aside class="notice">
您必须在您的对接程序中替换对接密钥 <code>APP_KEY 、 APP_SECRET 和 TENANT_SIGN </code> 
</aside>

## 统一请求格式

### 请求方式(Method)

GET/POST

### 编码

UTF-8

### URL格式

`/{version}/{resource}/{function}`

### 变量说明

+ {version} api版本号

+ {resource} 资源名，通常对应一类API

+ {function} 该资源提供的操作方法

### 响应

请求响应的结果为 JSON 格式。

HTTP 头信息:

`Accept:application/json;charset=utf-8`

> 比如查询公司列表的 URL 为：`http://apiOpen/v1/tenant/getTenant`
  
> 表示调用公司信息的get方法，并且返回json格式的字符串。

> 我们目前已经提供的接口，请参考API。

## JAVA SDK DEMO 下载

本页面提供Java的SDK下载。

SDK包内有部分使用说明，各接口的详细使用说明请浏览各API详情页。

如探意未提供您使用语言的SDK，您可以根据API文档开发接口

语言 | GitHub地址 
--------- | ------- 
JAVA | [GitHub地址](https://github.com/yiwise/openapidemo.git) 

## 最佳实践流程图

 ![](../images/OMS3.png)

## 常见问题解答

1. Q: 定时任务和手动任务的异同

  A: 异步，定时任务在设定好启动时间和结束时间时会在到达指定时间时自动启动
    手动任务则需要导入客户之后手动启动任务；
    
    同步，任务到达12-14点或指定暂停时间会自动暂停，并且会占用AI并发量。
    
2. Q: isv账号能否操作多个crm账号下的任务
  
  A: 一个APP_KEY和APP_SECRET目前只能操作一个CRM的账户，CRM暂无子公司这个概念

## 流程说明

### 第一部分:

主要是获取公司相关信息，为创建任务提供数据。

这里一共三个接口分别查询到：

1.公司Id

2.公司的主叫电话号码列表

3.机器人话术相关参数：机器人话术id

### 第二部分:

核心业务部分，主要是任务的创建，启动，停止等操作。

1.创建任务
    创建任务过程中需要传入的几个重要的值：机器人话术id,这个值不能传入有误，传入出错会导致任务拨打有误
2.任务启动
    只有手动任务才需要手动去启动任务，自动任务是自动启动的。 
<aside class="notice">
任务恢复：任务在未完全暂停（子任务还没有全部运行完成），是不能恢复的
</aside>
  
3.任务暂停
    任务在运行中，可调用暂停任务让任务进入暂停状态（可再次运行），并且是在所有当前正在跑的子任务都运行完成之后才会暂停
4.终止任务
    任务终止，终止之后不可以恢复

### 第三部分:

任务运行结束，调用任务回调接口，将本次任务信息发送到指定回调地址。

### 第四部分:

主要是查询任务相关信息。
 
## 枚举类型说明

### 电话卡类型枚举
 
type    | desc 
--------- | ------- 
MOBILE | 手机 
LANDLINE | 阿里云固话 
UNFIXED_CALL | 无主叫固话

### 任务类型枚举

type    | desc 
--------- | ------- 
AUTO | 自动任务
MANUAL | 手动任务 

### 任务状态枚举

type    | desc 
--------- | ------- 
NOT_STARTED | 未开始
IN_PROCESS | 进行中 
COMPLETED | 已完成
RUNNABLE | 可运行
USER_PAUSE | 用户暂停
SYSTEM_SUSPENDED | 系统暂停
TERMINATE | 已终止
IN_QUEUE | 排队中

### 通话结果枚举

type    | desc 
--------- | ------- 
ANSWERED | 已接听
NO_ANSWER | 呼叫号码未接听
BUSY | 呼叫号码占线
POWER_OFF | 呼叫号码关机
OUT_OF_SERVICE | 呼叫号码停机
REFUSED | 呼叫号码拒接
VACANT_NUMBER | 呼叫的号码是空号
CAN_NOT_CONNECT | 呼叫的号码无法接通
FROM_PHONE_ERROR | 主叫号码不可用
SYSTEM_ERROR | 外呼失败

### 意向等级枚举

type    | desc 
--------- | ------- 
A | 较强
B | 一般
C | 无法判断
D | 很少
E | 需要再次跟进
F | 无需再次跟进

### 一级行业枚举
type    | desc 
--------- | ------- 
OTHER | 其他产品推广
FINANCE | 金融类
REALTY | 房产类
COMPANY | 企业服务
INSURANCE | 保险行业
HEALTH | 健康保健
CONFERENCE | 会务营销
ALLIANCE | 招商加盟
EDUCATION | 教育类
CALLBACK | 通知回访
AUTO | 汽车行业
INTERNET | 互联网行业
CULTURAL | 文化行业
CLOTHING | 服装行业
MARKETING | 市场调研
HUMANRESOURCE | 人力资源
TRANSPORT | 交通出行
GOVERNMENT | 市政
WEDDING | 婚庆
SUPPLY_CHAIN | 运输行业
GAME | 游戏行业
COMMUNICATION | 通信行业")


### 二级行业枚举
type    | desc 
--------- | ------- 
OTHER |  "其他产品推广
LOAN | 贷款类
STOCK | 股票类
DEBT_COLLECTION | 金融催缴
CREDIT_CARD | 信用卡
FINICING | 理财
EXCHANGE | 外汇
STOCK_INVESTMENT | 股权投资
OPTION | 个股期权
AUTO_LOAN | 车贷
INSTALLMENT | 分期
ACCOUNT_INVESTMENT | 邀请开户
FINICE | 融资
DEPOSIT | 提现
BLOCK_CHAIN | 区块链
WAKE_UP | 客户唤醒
ALLOCATION | 配资
STOCK_APP | 炒股APP
MANSION | 豪宅
HOUSE | 住宅
DECORATION | 装修
INTERMEDIARY | 中介
SHOP | 商铺
FOUREIGN_REALTY | 海外房产
RENT_OR_SALE | 出租出售
OFFICE_BUILDING | 写字楼
FURNITURE | 家具
COMPLEX | 商业综合体
DIVERSION | 案场导流
ACCOUNTING | 代理记账
TRANSFER | 公司转让
SHOP_MANAGING | 店铺代运营
FOUREIGN_MERCHANT | 外贸
ADVERTISING | 广告推广
TRADEMARK | 产权商标
INSPECTION | 检验认证
ENTERPRISE_INVESTMENT | 企业招商
CHECK | 承诺汇票
ACCOUNT_APP | 财务软件
VERIFICATION | 认证
WIN_WIN | 双创
LEGAL_SERVICE | 法律服务
E_RECEIPT | 电子发票
CONSULTATION | 企业管理咨询
FACILITY_RENT | 设备租凭
PUBLICIST | 公关
GIFT_CARD | 礼品卡
AUTO_INSURANCE | 车险
LIFE_INSURANCE | 人寿险
MEDICAL_INSURANCE | 医疗保险
INSURANCE_SALE | 保险销售
ENDOWMENT_INSURANCE | 养老保险
HEALTH_INSURANCE | 健康险
INJURY_INSURANCE | 工伤
INSURANCE_AGENT | 保险代理
BEAUTY | 美容
HEALTH_PRODUCT | 保健品
HEAKTH_FACILITY | 保健器械
DIET | 减肥
HEALTH_CHECK | 体检
HOSPITAL | 医院
FIT | 健身
DENTIST | 牙医
MEETING | 会议邀约
EXHIBITION | 展会邀约
EXHIBITION_ENTERPRISE | 会议邀约(企业)
FAST_FOOD | 快餐店
SNACK | 小吃店
ESTORE | 网店
ALCOHOL | 酒类
APP | APP招商
INVESTMENT | 投资邀约
BEALTY_INVESTMENT | 美容
RESTARUNT | 饭店
BABY | 母婴
FOOD | 食品
ADULT_EDUCATION | 成人培训
SKILL_EDUCATION | 技能培训
SPEECH | 课程演讲
START_NOTIFICATION | 开课通知
ADMISSION | 招生
ONLINE_EDUCATION | 线上培训
DAILY_EDUCATION | 日托
STATISFICATION | 满意度调查
GOV_NOTIFICATION | 政府通知
INVESTIGATION | 使用情况调查
ADDRESS_VERIFICATION | 确认地址
URGE | 催退收货
NOTIFICATION | 通知
USED_CAR | 二手车
ACCESSORIES | 配件
NEW_CAR | 新车
GAS | 加油
WECHAT_APP | 小程序
SEO | SEO
TAOBAO_COMMENT | 淘宝评论
SOFTWARE | 软件服务
BIG_DATA | 大数据营销
WEB_BUILD | 网站制作
PHOTOGRAPH | 淘宝拍摄
INTERNET_SERVICE | 电商服务
COLLECTION | 藏品收藏
PUBLISHING | 出书
PUBLISHING_RIGHT | 知识产权
MAGAZINE | 杂志销售
PAINTING | 书画
PERSONAL | 私人定制
FOUREIGN_CLOTHING | 外贸
MOVIE | 影视
HIRE | 招聘
AIRLINE_TICKET | 飞机票
TRAVEL_NOTIFICATION | 登机登车提醒
GOV_SERVICE | 市政服务
HOUSEHOLD | 入户
WED_WEB | 婚庆网站
WED_SERVICE | 婚庆服务
WED_INVESTMENT | 活动邀请
LOGISTICS | 物流
PLATFORM_PROMOTION | 游戏平台推广
SINGLE_PLAYER_GAME | 单机游戏
ONLINE_GAME | 网游
GAME_CHANNEL | 游戏渠道
GAME_PROXY | 游戏代理
GAME_OTHER | 其他
BROADBAND | 宽带
PLAN_UPGRADE | 套餐升级
CONTRACT_PHONE | 合约机
COMMUNICATION_OTHER | 其他


## 错误码信息

错误码 | 错误信息
---------- | -------
200|执行成功
401|校验数据错误
403|权限不足
404|资源未找到
412|参数错误
500|未知错误

