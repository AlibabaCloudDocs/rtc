---
keyword: [RAM, 子账号]
---

# RAM资源授权

在使用RAM账号调用RTC API之前，需要主账号通过创建授权策略对RAM账号进行授权。在授权策略中，使用资源描述符（Alibaba Cloud Resource Name, ARN）指定授权资源。本文为您介绍了可授权的RTC资源类型和API，如果您无需授权就能访问RTC资源，可以跳过本文。

## 可授权的音视频通信资源类型

在进行RAM子账号授权时，音视频通信的资源类型及描述方式如下表所示。

**注意：** accountid必须是主账户阿里云UID。

|资源类型|授权策略中的资源描述方式|说明|
|----|------------|--|
|service|acs:rtc:\*:$accountid:|授权子账户管理RTC服务。例如：变配、查询账户信息等。|
|appid|acs:rtc:\*:$accountid:app/|授权子账户管理自己的应用。例如：停用、启用、配置、查询等。|

## 可授权的RTC API

每个API的资源描述如下表所示。

|API|鉴权规则|
|---|----|
|DescribeApps|acs:rtc:\*:$accountid:app/|
|StartApp|acs:rtc:\*:$accountid:app/$appid|
|StopApp|acs:rtc:\*:$accountid:app/$appid|
|DeleteChannel|acs:rtc:\*:$accountid:app/$appid|
|UpdateChannel|acs:rtc:\*:$accountid:app/$appid|
|DescribeRealTimeRecordDetail|acs:rtc:\*:$accountid:app/$appid|
|DescribeRealTimeRecordList|acs:rtc:\*:$accountid:app/$appid|
|DescribeRecordDetail|acs:rtc:\*:$accountid:app/$appid|
|DescribeRecordList|acs:rtc:\*:$accountid:app/$appid|
|DescribeStatis|acs:rtc:\*:$accountid:app/$appid|

