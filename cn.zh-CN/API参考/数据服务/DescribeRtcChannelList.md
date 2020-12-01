# DescribeRtcChannelList

调用DescribeRtcChannelList获取频道通信记录列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRtcChannelList&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRtcChannelList|操作接口名，系统规定参数，取值：**DescribeRtcChannelList**。 |
|PageNo|Long|是|1|第几页，取值：大于**0**。

 默认为1。 |
|PageSize|Long|是|20|显示数量，取值：大于**0**。

 默认为10。 |
|TimePoint|String|是|2018-01-29T00:00:00Z|查询时间点，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。

 时间粒度为天。 |
|AppId|String|否|aoe\*\*\*\*|应用ID，可通过控制台创建和查询，仅支持传单个ID。 |
|SortType|String|否|desc|排序顺序，默认按StartTime逆序排序。 |
|ServiceArea|String|否|cn|服务区域，默认查询所有区域。

 -   **cn**：中国。
-   **us**：美国。 |
|UserId|String|否|testUser|用户ID，仅支持传单个ID。 |
|ChannelId|String|否|testChannel|频道ID，仅支持传单个ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ChannelList|Array of ChannelList| |通信记录。 |
|ChannelList| | | |
|CallArea|List|cn|通信区域。取值：

 -   **cn**：中国。
-   **us**：美国。 |
|ChannelId|String|testChannel|频道ID。 |
|EndTime|String|2018-01-29T02:00:00Z|会话结束时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|StartTime|String|2018-01-29T01:00:00Z|会话起始时间，UTC格式，格式为yyyy-MM-ddTHH:mm:ssZ。 |
|TotalUserCnt|Long|2|累计用户数量。 |
|PageNo|Long|1|页码。 |
|PageSize|Long|100|显示数量。 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。 |
|TotalCnt|Long|1000|总页数。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRtcChannelList
&PageSize=20
&PageNo=1
&TimePoint=2018-01-29T00:00:00Z
&ChannelId=testChannel
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRtcChannelListResponse>
  <PageSize>1</PageSize>
  <RequestId>68F57D4C-557B-44FB-A0B7-D002E153555E</RequestId>
  <TotalCnt>24</TotalCnt>
  <PageNo>1</PageNo>
  <ChannelList>
        <ChannelList>
              <TotalUserCnt>2</TotalUserCnt>
              <EndTime>2020-04-14T13:09:00+08:00</EndTime>
              <StartTime>2020-04-14T13:08:00+08:00</StartTime>
              <ChannelId>testChannel</ChannelId>
              <CallArea>
                    <CallArea>cn</CallArea>
              </CallArea>
        </ChannelList>
  </ChannelList>
</DescribeRtcChannelListResponse>
```

`JSON` 格式

```
{
	"PageSize": 1,
	"RequestId": "68F57D4C-557B-44FB-A0B7-D002E153555E",
	"TotalCnt": 24,
	"PageNo": 1,
	"ChannelList": {
		"ChannelList": [
			{
				"TotalUserCnt": 2,
				"EndTime": "2020-04-14T13:09:00+08:00",
				"StartTime": "2020-04-14T13:08:00+08:00",
				"ChannelId": "testChannel",
				"CallArea": {
					"CallArea": [
						"cn"
					]
				}
			}
		]
	}
}
```

