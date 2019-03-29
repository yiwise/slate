# 任务信息回调接口
回调指的是电话任务在运行过程中对单通电话通话结果、通话详情和任务完成事件等对isv用户的回调通知，所有回调事件都使用同一回调地址，请根据回调数据中的
"dataType"字段区分不同的回调，目前支持两种回调类型，通话记录结果回调和任务完成回调。

## 回调说明

<aside class="notice">
 请您在对接接口前，务必配置好回调地址,否则回调将无法成功。 
</aside>

最多回调10次，每次回调时长按1分钟，2分钟，4分钟，8分钟间隔依次递增，总回调时长可达24小时。回调成功后，处理方应当返回字符串success在返回的body体中

## 请求方法说明
所有回调方法采用POST请求发起

## dataType支持类型说明
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  ROBOT_CALL_RECORD| String | 单通通话记录 |
  ROBOT_CALL_JOB| String | 任务结果信息 | 
 
## 通话记录回调接口

当一次通话完成后，探意机器人会自动调用回调程序向用户配置的回调地址发送本次通话详情。

 > 入参JSON实例:

 ```
    {
        "dataType":"ROBOT_CALL_RECORD",
        "data":{
            "callRecordId":119,
            "tenantId":1,
            "robotCallJobId":43,
            "dialogFlowId":12,
            "calledPhoneNumber":"17751279857",
            "resultStatus":"ANSWERED",
            "intentLevel":"A",
            "customerConcern":[
                "价格"
            ],
            "fullAudioUrl":"https://ai-call-platform-daily.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId43/RHGKTLBG_TaskId_1305203/ai_user.wav",
            "customerAudioUrl":"https://ai-call-platform-daily.oss-cn-hangzhou.aliyuncs.com/DialogueRecording/TenantId1/CallJobId43/RHGKTLBG_TaskId_1305203/user.wav",
            "analysisBasis":"判断依据",
            "startTime":"2018-10-12 18:46:55",
            "endTime":"2018-10-12 18:47:42",
            "chatDuration":37,
            "chatRound":0,
            "attributes":["有钱"],
            "callDetailList":[
                {
                    "text":"喂，您好, （停顿2s），您好，想问下您位于江北纬七路隧道附近，均价17000的高端商业综合体，我可以给您介绍一下吗？",
                    "type":"ROBOT",
                    "callDetailId": 1
                },
                {
                    "text":"嗯",
                    "type":"PERSON",
                    "callDetailId": 2
                }
            ]
        }
    }
 ```

### 请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  dataType| String | 回调类型（始终为 ROBOT_CALL_RECORD ） | 
  callRecordId| Long | 通话记录id | 
  tenantId| Long | 公司id | 
  dialogFlowId| Long | 话术id |
  robotCallJobId| Long | 任务id |
  calledPhoneNumber| String | 电话号码 |
  resultStatus| String | 通话结果 (ANSWERED, "已接听"),(NO_ANSWER, "未接"),(BUSY, "占线"),(POWER_OFF, "关机"),(OUT_OF_SERVICE, "被叫停机"),(REFUSED, "拒接"),(VACANT_NUMBER, "空号"),(CAN_NOT_CONNECT, "无法接通"), (FROM_PHONE_ERROR, "主叫号码不可用"),(SYSTEM_ERROR, "外呼失败") | 
  intentLevel| String | 意向等级, (A, "A级(较强)"),(B, "B级(一般)"),(C, "C级(无法判断)"),(D, "D级(很少)"),(E, "E级别(需要再次跟进)"),(F, "F级别(无需再次跟进)") | 
  customerConcern| String | 用户关注点 |
  fullAudioUrl| String | 用户和AI合成的录音 |
  customerAudioUrl| String | 用户的录音 |
  analysisBasis| String | 意向分析判断依据 |
  startTime| String | 拨打开始时间 |
  endTime| String | 拨打结束时间 |
  chatDuration| Long | 通话时长(单位秒) |
  chatRound| Long | 通话轮次 |
  attributes| String | 用户属性 |
  callDetailList| List | 对话内容 |
  text| String | 对话说的具体文字内容 |
  type| String | 说话者 (PERSON, "人"), (ROBOT, "机器人") |
  callDetailId| Long | 对话详情id |


## 任务完成详情回调接口
 当一次任务完成后，探意机器人会自动调用回调程序向用户配置的回调地址发送本次任务结束的信息。

> 入参JSON实例:
 
 ```
    {
        "dataType":"ROBOT_CALL_JOB",
        "data":{
            "robotCallJobId":43,
            "tenantId":1,
            "status":"COMPLETED"
        }
    }
 ```
 
### 请求参数:
 
 参数名 | 类型  | 描述  
 --------- | ------- | ------ 
  dataType| String | 回调类型（始终为 ROBOT_CALL_JOB ） | 
  robotCallJobId| Long | 任务id | 
  tenantId| Long | 公司id |
  status| String | 任务状态 ( 始终为 COMPLETED) |
