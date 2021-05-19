# DescribeFaultDiagnosisUserDetail

调用DescribeFaultDiagnosisUserDetail获取异常诊断的用户详情。

**说明：** 支持查询最近48小时的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeFaultDiagnosisUserDetail&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/diagnosis/describeFaultDiagnosisUserDetail HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|311|频道ID。 |
|CreatedTs|Long|Query|是|1615892596|创建频道的时间，使用UNIX时间戳表示，单位：秒。 |
|UserId|String|Query|是|0a497933\*\*\*\*|用户ID。 |
|FaultType|String|Query|是|JOIN\_SLOW|过滤的异常类型，取值：

 -   **JOIN\_SLOW**：进频道慢。
-   **AUDIO\_STUCK**：音频卡顿。
-   **VIDEO\_STUCK**：视频卡顿。
-   **VIDEO\_VAGUE**：视频模糊。
-   **HIGH\_DELAY**：通话延迟高。
-   **FIRST\_FRAME\_SLOW**：接收首屏慢。

 关于异常类型详情，请参见[异常类型说明](~~217966~~)。 |
|QueryCallUserInfo|Boolean|Query|否|true|是否查询通话用户信息，参数为空表示false。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|CallInfo|Object| |通信基本信息（当QueryCallUserInfo为false时返回）。 |
|AppId|String|0rbd\*\*\*\*|App ID。 |
|ChannelId|String|0011|频道ID。 |
|CallStatus|String|IN|通信状态。取值：

 -   **IN**：进行中。
-   **OUT**：已结束。 |
|CreatedTs|Long|1620957905|创建通信时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1620958150|释放通信时间，使用UNIX时间戳表示，单位：秒。 |
|Duration|Long|245|通信持续时长，单位：秒。 |
|UserDetail|Object| |诊断用户详细信（当QueryCallUserInfo为false时返回）。 |
|UserId|String|0a497933\*\*\*\*|用户ID。 |
|Location|String|浙江省-杭州市|地理位置信息。 |
|OnlinePeriods|Array of OnlinePeriod| |在线时段信息。 |
|JoinTs|Long|1620957919|加入通话时间，使用UNIX时间戳表示，单位：秒。 |
|LeaveTs|Long|1620958150|离开通话时间，使用UNIX时间戳表示，单位：秒。 |
|CreatedTs|Long|1620957919|创建通话时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1620958150|释放通话时间，使用UNIX时间戳表示，单位：秒。通话未结束时值为0。 |
|OnlineDuration|Long|231|在线时长，单位：秒。 |
|Duration|Long|231|通话时长，首次进入到最后离开，单位：秒。 |
|SdkVersion|String|2.2.2105081533277|SDK版本。 |
|Os|String|iOS|浏览器或操作系统类型，例如Chrome、iOS、Android等。

 **说明：** 如果客户端为Web，返回浏览器类型；如果客户端为本地Native端，返回操作系统类型。 |
|Network|String|WiFi|网络类型，例如WiFi、4G等 |
|FaultMetricData|Object| |异常指标。 |
|Nodes|Array of Node| |指标趋势图坐标点列表。 |
|X|String|1620957900|指标趋势图中x轴横坐标，单位时间为1分钟。 |
|Y|String|0.4540|指标趋势图中y轴纵坐标。 |
|FactorList|Array of FactorData| |影响因素列表，参数为空表示影响因素未知。 |
|FactorId|String|2|影响因素ID，取值：

 -   **1**：发布端网络差。
-   **2**：订阅端网络差。
-   **3**：发布端设备性能差。
-   **4**：发布端关闭摄像头。
-   **5**：发布端切到后台运行。 |
|RelatedMetricDatas|Array of MetricData| |关联的指标，当FaultType为AUDIO\_STUCK、VIDEO\_STUCK、VIDEO\_VAGUE、HIGH\_DELAY时返回坐标数据。 |
|Role|String|RECEIVER|来源角色，取值：

 -   **SENDER**：发布端。
-   **RECEIVER**：订阅端。 |
|UserId|String|c31b3236\*\*\*\*|用户ID。 |
|Type|String|AUDIO\_STUCK|指标类型。 |
|Nodes|Array of Node| |指标趋势图坐标点列表。 |
|X|String|1620957937|指标趋势图中x轴横坐标。 |
|Y|String|529.39|指标趋势图中y轴纵坐标。 |
|Ext|Map| |扩展数据。 |
|RelatedEventDatas|Array of EventData| |关联的事件，按时间分组，当FaultType为AUDIO\_STUCK、VIDEO\_STUCK、VIDEO\_VAGUE、HIGH\_DELAY时返回坐标数据。 |
|UserId|String|c31b3236\*\*\*\*|用户ID。 |
|Role|String|SENDER|来源角色，取值：

 -   **SENDER**：发布端。
-   **RECEIVER**：订阅端。 |
|EventDataItems|Array of EventDataItems、| |事件数据列表。 |
|Ts|Long|1614936817|第一个事件发生的时间，使用UNIX时间戳表示，单位：秒。 |
|EventList|Array of EventList| |事件列表。 |
|EventName|String|开始发布|事件名称。 |
|EventType|String|USER|事件类型，取值：

 -   **USER**：用户事件。
-   **SYSTEM**：系统事件。 |
|Ts|Long|1614936817|事件发生的时间，使用UNIX时间戳表示，单位：秒。 |
|RequestId|String|1DB846A6-969D-4873-B592-B4A8D1CA3294|请求ID。 |

## 示例

请求示例

```
POST /api/diagnosis/describeFaultDiagnosisUserDetail?AppId=0rbd****&ChannelId=311&CreatedTs=1615892596&UserId=0a497933****&FaultType=JOIN_SLOW&QueryCallUserInfo=true HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeFaultDiagnosisUserDetailResponse>
    <code>200</code>
    <data>
        <UserDetail>
            <DestroyedTs>1620958150</DestroyedTs>
            <Os>iOS</Os>
            <UserId>0a497933****</UserId>
            <Network>WiFi</Network>
            <SdkVersion>2.2.2105081533277</SdkVersion>
            <Duration>231</Duration>
            <CreatedTs>1620957919</CreatedTs>
            <OnlineDuration>231</OnlineDuration>
            <OnlinePeriods>
                <LeaveTs>1620958150</LeaveTs>
                <JoinTs>1620957919</JoinTs>
            </OnlinePeriods>
            <Location>浙江省-杭州市</Location>
        </UserDetail>
        <FactorList>
            <RelatedMetricDatas>
                <Role>RECEIVER</Role>
                <Type>AUDIO_STUCK</Type>
                <UserId>c31b3236****</UserId>
                <Nodes>
                    <X>1620957937</X>
                    <Y>529.39</Y>
                </Nodes>
                <Nodes>
                    <X>1620957953</X>
                    <Y>359.99</Y>
                </Nodes>
            </RelatedMetricDatas>
            <RelatedMetricDatas>
                <Role>RECEIVER</Role>
                <Type>AUDIO_RTT</Type>
                <UserId>c31b3236****</UserId>
                <Nodes>
                    <X>1620957937</X>
                    <Y>323.5</Y>
                </Nodes>
                <Nodes>
                    <X>1620957939</X>
                    <Y>1002</Y>
                </Nodes>
            </RelatedMetricDatas>
            <FactorId>2</FactorId>
        </FactorList>
        <RequestId>1DB846A6-969D-4873-B592-B4A8D1CA3294</RequestId>
        <CallInfo>
            <DestroyedTs>1620958150</DestroyedTs>
            <AppId>0rbd****</AppId>
            <CallStatus>OUT</CallStatus>
            <Duration>245</Duration>
            <CreatedTs>1620957905</CreatedTs>
            <ChannelId>0011</ChannelId>
        </CallInfo>
        <FaultMetricData>
            <Nodes>
                <X>1620957900</X>
                <Y>0.4540</Y>
            </Nodes>
            <Nodes>
                <X>1620957960</X>
                <Y>0.5175</Y>
            </Nodes>
            <Nodes>
                <X>1620958020</X>
                <Y>0.4775</Y>
            </Nodes>
            <Nodes>
                <X>1620958080</X>
                <Y>0.3375</Y>
            </Nodes>
        </FaultMetricData>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>1DB846A6-969D-4873-B592-B4A8D1CA3294</requestId>
    <successResponse>true</successResponse>
</DescribeFaultDiagnosisUserDetailResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "UserDetail" : {
      "DestroyedTs" : 1620958150,
      "Os" : "iOS",
      "UserId" : "0a497933****",
      "Network" : "WiFi",
      "SdkVersion" : "2.2.2105081533277",
      "Duration" : 231,
      "CreatedTs" : 1620957919,
      "OnlineDuration" : 231,
      "OnlinePeriods" : [ {
        "LeaveTs" : 1620958150,
        "JoinTs" : 1620957919
      } ],
      "Location" : "浙江省-杭州市"
    },
    "FactorList" : [ {
      "RelatedMetricDatas" : [ {
        "Role" : "RECEIVER",
        "Type" : "AUDIO_STUCK",
        "UserId" : "c31b3236****",
        "Nodes" : [ {
          "X" : "1620957937",
          "Y" : "529.39"
        }, {
          "X" : "1620957953",
          "Y" : "359.99"
        } ]
      }, {
        "Role" : "RECEIVER",
        "Type" : "AUDIO_RTT",
        "UserId" : "c31b3236****",
        "Nodes" : [ {
          "X" : "1620957937",
          "Y" : "323.5"
        }, {
          "X" : "1620957939",
          "Y" : "1002"
        } ]
      } ],
      "FactorId" : "2"
    } ],
    "RequestId" : "1DB846A6-969D-4873-B592-B4A8D1CA3294",
    "CallInfo" : {
      "DestroyedTs" : 1620958150,
      "AppId" : "0rbd****",
      "CallStatus" : "OUT",
      "Duration" : 245,
      "CreatedTs" : 1620957905,
      "ChannelId" : "0011"
    },
    "FaultMetricData" : {
      "Nodes" : [ {
        "X" : "1620957900",
        "Y" : "0.4540"
      }, {
        "X" : "1620957960",
        "Y" : "0.5175"
      }, {
        "X" : "1620958020",
        "Y" : "0.4775"
      }, {
        "X" : "1620958080",
        "Y" : "0.3375"
      } ]
    }
  },
  "httpStatusCode" : "200",
  "requestId" : "1DB846A6-969D-4873-B592-B4A8D1CA3294",
  "successResponse" : true
}
```

