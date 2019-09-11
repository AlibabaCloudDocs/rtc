# RAM资源授权 {#concept_645597 .concept}

在使用RAM账号调用RTC API之前，需要主账号通过创建授权策略对RAM账号进行授权。在授权策略中，使用资源描述符（Alibaba Cloud Resource Name, ARN）指定授权资源。

## 可授权的音视频通信资源类型 {#section_mcm_4xl_mev .section}

在进行RAM子账号授权时，音视频通信的资源类型及描述方式如下表所示。

|资源类型|授权策略中的资源描述方式|说明|
|----|------------|--|
|service|acs:rtc::$accountid:|授权子账户管理RT 服务。例如：变配、查询账户信息等。|
|appid|acs:rtc::$accountid:app/|授权子账户管理自己的应用。例如：停用、启用、配置、查询等。|

## 可授权的音视频通信接口 {#section_ba9_ifc_1v7 .section}

当子账号调用RTC API对主账号的资源进行访问时，RTC 后台会进行权限检查。

下表列举了RTC中可授权的API及其鉴权规则。

|API|鉴权规则|
|---|----|
|DescribeApps|acs:rtc:\*:$accountid:app/|
|StartApp|acs:rtc::$accountid:app/$appid|
|StopApp|acs:rtc::$accountid:app/$appid|
|CreateChannel|acs:rtc::$accountid:app/$appid|
|DeleteChannel|acs:rtc::$accountid:app/$appid|
|UpdateChannel|acs:rtc::$accountid:app/$appid|
|DescribeRealTimeRecordDetail|acs:rtc::$accountid:app/$appid|
|DescribeRealTimeRecordList|acs:rtc::$accountid:app/$appid|
|DescribeRecordDetail|acs:rtc::$accountid:app/$appid|
|DescribeRecordList|acs:rtc::$accountid:app/$appid|
|DescribeStatis|acs:rtc::$accountid:app/$appid|

