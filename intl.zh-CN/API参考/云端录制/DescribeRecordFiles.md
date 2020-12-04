# DescribeRecordFiles

调用DescribeRecordFiles查询录制生成的文件列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeRecordFiles&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRecordFiles|操作接口名，系统规定参数。取值：**DescribeRecordFiles**。 |
|AppId|String|是|yourAppId|应用ID。仅支持传单个ID，您可以在控制台创建和查询。 |
|ChannelId|String|否|yourChannelId|频道ID。仅支持传单个ID。 |
|PageSize|Integer|否|10|每页显示个数。取值必须大于**0**。默认为**10**。 |
|PageNum|Integer|否|1|第几页。取值必须大于0。默认查询第1页。 |
|TaskIds.N|RepeatList|否|testId|录制任务ID。最多支持10个任务批量查询。 |
|StartTime|String|否|2020-11-01T17:36:00Z|开始时间。格式为：*yyyy-MM-dd*T*HH:mm:ss*Z（UTC时间）。 |
|EndTime|String|否|2020-11-02T17:36:00Z|结束时间。格式为：*yyyy-MM-dd*T*HH:mm:ss*Z（UTC时间）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordFiles|Array of RecordFile| |文件列表。 |
|AppId|String|yourAppId|应用ID。仅支持传单个ID，您可以在控制台创建和查询。 |
|ChannelId|String|yourChannelId|频道ID。仅支持传单个ID。 |
|CreateTime|String|2020-10-02T17:36:00Z|创建时间。格式为：*yyyy-MM-dd*T*HH:mm:ss*Z（UTC时间）。 |
|Duration|Float|1800|录制文件时长。 |
|StartTime|String|2020-11-01T17:36:00Z|开始时间。格式为：*yyyy-MM-dd*T*HH:mm:ss*Z（UTC时间）。 |
|StopTime|String|2020-11-02T17:36:00Z|开始时间。格式为：*yyyy-MM-dd*T*HH:mm:ss*Z（UTC时间）。 |
|TaskId|String|yourTaskId|任务ID。仅支持传单个ID。 |
|Url|String|http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002\_11-17-online/example.m3u8|录制文件OSS Url。 |
|RequestId|String|760bad53276431c499e30dc36f6b\*\*\*\*|请求ID。 |
|TotalNum|Long|1|返回结果数。 |
|TotalPage|Long|1|返回分页数。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeRecordFiles
&AppId=yourAppId
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeRecordFilesResponse>
  <TotalNum>3</TotalNum>
	  <RequestId>AB2D3461-2F88-43DC-B60F-2F4C9BDB6522</RequestId>
	  <TotalPage>1</TotalPage>
	  <RecordFiles>
		    <TaskId>11-17-online</TaskId>
		    <AppId>9qb1zcyc</AppId>
		    <CreateTime>2020-11-17T05:08:12Z</CreateTime>
		    <StartTime>2020-11-17T04:40:28Z</StartTime>
		    <Duration>1482.29</Duration>
		    <ChannelId>record-002</ChannelId>
		    <Url>http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002_11-17-online/2020-11-17-12-40-28_2020-11-17-13-05-10.m3u8</Url>
		    <StopTime>2020-11-17T05:05:11Z</StopTime>
	  </RecordFiles>
	  <RecordFiles>
		    <TaskId>11-17-online</TaskId>
		    <AppId>9qb1zcyc</AppId>
		    <CreateTime>2020-11-17T04:40:37Z</CreateTime>
		    <StartTime>2020-11-17T04:10:27Z</StartTime>
		    <Duration>1800.01</Duration>
		    <ChannelId>record-002</ChannelId>
		    <Url>http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002_11-17-online/2020-11-17-12-10-28_2020-11-17-12-40-28.m3u8</Url>
		    <StopTime>2020-11-17T04:40:28Z</StopTime>
	  </RecordFiles>
	  <RecordFiles>
		    <TaskId>11-17-online</TaskId>
		    <AppId>9qb1zcyc</AppId>
		    <CreateTime>2020-11-17T04:10:34Z</CreateTime>
		    <StartTime>2020-11-17T03:40:28Z</StartTime>
		    <Duration>1799.95</Duration>
		    <ChannelId>record-002</ChannelId>
		    <Url>http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002_11-17-online/2020-11-17-11-40-28_2020-11-17-12-10-28.m3u8</Url>
		    <StopTime>2020-11-17T04:10:28Z</StopTime>
	  </RecordFiles>
    </DescribeRecordFilesResponse>
```

`JSON` 格式

```
{
    "TotalNum": 3,
    "RequestId": "AB2D3461-2F88-43DC-B60F-2F4C9BDB6522",
    "TotalPage": 1,
    "RecordFiles": [
        {
            "TaskId": "11-17-online",
            "AppId": "9qb1zcyc",
            "CreateTime": "2020-11-17T05:08:12Z",
            "StartTime": "2020-11-17T04:40:28Z",
            "Duration": 1482.29,
            "ChannelId": "record-002",
            "Url": "http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002_11-17-online/2020-11-17-12-40-28_2020-11-17-13-05-10.m3u8",
            "StopTime": "2020-11-17T05:05:11Z"
        },
        {
            "TaskId": "11-17-online",
            "AppId": "9qb1zcyc",
            "CreateTime": "2020-11-17T04:40:37Z",
            "StartTime": "2020-11-17T04:10:27Z",
            "Duration": 1800.01,
            "ChannelId": "record-002",
            "Url": "http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002_11-17-online/2020-11-17-12-10-28_2020-11-17-12-40-28.m3u8",
            "StopTime": "2020-11-17T04:40:28Z"
        },
        {
            "TaskId": "11-17-online",
            "AppId": "9qb1zcyc",
            "CreateTime": "2020-11-17T04:10:34Z",
            "StartTime": "2020-11-17T03:40:28Z",
            "Duration": 1799.95,
            "ChannelId": "record-002",
            "Url": "http://rtc-demo.oss-cn-shanghai.aliyuncs.com/record/10-15-1/9qb1zcyc/record-002_11-17-online/2020-11-17-11-40-28_2020-11-17-12-10-28.m3u8",
            "StopTime": "2020-11-17T04:10:28Z"
        }
    ]
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/rtc)查看更多错误码。

## 特殊错误码

|错误代码

|描述

|Http 状态码

|语义 |
|------|----|----------|----|
|InternalError

|The request processing has failed due to some unknown error, exception or failure.

|500

|内部错误 |

