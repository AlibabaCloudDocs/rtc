# DescribeChannelUsers

调用DescribeChannelUsers查询频道内各种模式下在线用户列表的详细信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeChannelUsers&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeChannelUsers|操作接口名，系统规定参数，取值：**DescribeChannelUsers**。 |
|AppId|String|是|a2hz\*\*\*\*|应用ID，通过控制台创建和查询，仅支持传单个ID。 |
|ChannelId|String|是|testId|要查询的频道ID，仅支持传单个ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelProfile|Integer|1|频道模式。

 -   1：Communication（通信模式）。
-   2：Interactive\_live（直播模式）。 |
|CommTotalNum|Integer|100|通信模式下频道内的用户总数，如果频道是其他模式，该参数为0。 |
|InteractiveUserList|List|\["4455\*\*\*\*", "3267\*\*\*\*", "efbc\*\*\*\*"\]|直播模式下频道内的互动者用户列表，频道是其他模式时，该参数为空。 |
|InteractiveUserNum|Integer|0|直播模式下频道内的互动者用户总数，如果频道是其他模式，该参数为0。 |
|IsChannelExist|Boolean|true|频道是否存在，取值：true\|false。 |
|LiveUserList|List|\["4455\*\*\*\*", "3267\*\*\*\*", "efbc\*\*\*\*"\]|直播模式下频道内的观众用户列表，只返回前1000人，频道是其他模式时，该参数为空。 |
|LiveUserNum|Integer|0|直播模式下频道内的观众用户总数，如果频道是其他模式，该参数为0。 |
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|请求ID。 |
|Timestamp|Integer|1557909133|当前时刻的时间戳（您需要进行UTC时间的时区转换）。 |
|UserList|List|\[\]|通信模式下频道的用户列表，频道是其他模式时，该参数为空。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeChannelUsers
&AppId=a2hz****
&ChannelId=testId
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeChannelUsersResponse>
  <RequestId>6159ba01-6687-4fb2-a831-f0cd8d188648</RequestId>
  <TimeStamp>1557909133</TimeStamp>
  <IsChannelExist>true</IsChannelExist>
  <ChannelProfile>1</ChannelProfile>
  <CommTotalNum>100</CommTotalNum>
  <InteractiveUserNum>0</InteractiveUserNum>
  <LiveUserNum>0</LiveUserNum>
  <UserList>4455****</UserList>
  <UserList>3267****</UserList>
  <UserList>efbc****</UserList>
</DescribeChannelUsersResponse>
```

`JSON`格式

```
{
  "RequestId": "6159ba01-6687-4fb2-a831-f0cd8d188648",
  "TimeStamp": 1557909133,
  "IsChannelExist": true,
  "ChannelProfile": 1,
  "CommTotalNum": 100,
  "InteractiveUserNum": 0,
  "LiveUserNum": 0,
  "UserList": ["4455****", "3267****", "efbc****"],
  "InteractiveUserList": [],
  "LiveUserList": []
}
```

