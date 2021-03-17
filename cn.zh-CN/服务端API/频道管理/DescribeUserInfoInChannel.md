# DescribeUserInfoInChannel

调用DescribeUserInfoInChannel查询用户在频道中实时信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeUserInfoInChannel&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeUserInfoInChannel|操作接口名，系统规定参数，取值：**DescribeUserInfoInChannel**。 |
|AppId|String|是|4eah\*\*\*\*|应用ID，通过控制台创建和查询，仅支持传单个ID。 |
|ChannelId|String|是|1234|频道ID，仅支持传单个ID。 |
|UserId|String|是|testId|用户ID，仅支持传单个ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsChannelExist|Boolean|true|频道是否存在，取值：true\|false。 |
|IsInChannel|Boolean|true|用户当前是否在频道内，取值：true\|false。 |
|Property|Array of Property| |用户在频道内的信息。 |
|Join|Integer|1557909133|时间戳，用户的Session进入会议的时间。 |
|Role|Integer|1|在会议中的角色。

 -   0：通信模式下的用户角色。
-   1：interactive（参与互动）角色。
-   2：live（仅观看）角色。 |
|Session|String|xa744sxx8rtobgj\*\*\*\*|Session ID（会话ID）。 |
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|请求ID。 |
|Timestamp|Integer|1557909133|当前时刻的时间戳（您需要进行UTC时间的时区转换）。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeUserInfoInChannel
&AppId=4eah****
&ChannelId=1234
&UserId=testId
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeUserInfoInChannelResponse>
  <RequestId>6159ba01-6687-4fb2-a831-f0cd8d188648</RequestId>
  <TimeStamp>1557909133</TimeStamp>
  <IsChannelExist>true</IsChannelExist>
  <IsInChannel>true</IsInChannel>
  <Property>
        <Join>1557909133</Join>
        <Session>xa744sxx8rtobgj****</Session>
        <Role>1</Role>
  </Property>
</DescribeUserInfoInChannelResponse>
```

`JSON` 格式

```
{
    "RequestId": "6159ba01-6687-4fb2-a831-f0cd8d188648",
    "TimeStamp": 1557909133,
    "IsChannelExist": true,
    "IsInChannel": true,
    "Property":[{"Join":1557909133, "Session":"xa744sxx8rtobgj****", "Role":1}]
}
```

