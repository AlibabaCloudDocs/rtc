# DescribeQoeMetricData

调用DescribeQoeMetricData获取单次通信中用户的下行体验质量指标。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeQoeMetricData&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/call/describeQoeMetricData HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|9qb1\*\*\*\*|App ID。 |
|ChannelId|String|Query|是|311|频道ID。 |
|CreatedTs|Long|Query|是|1615887685|创建频道时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|Query|否|1615888615|释放频道时间，使用UNIX时间戳表示，单位：秒。参数为空表示获取当前时间。 |
|UserId|String|Query|是|c906531af5f9\*\*\*\*|用户ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|VideoData|Array of QoeMetricDataItem| |视频数据。 |
|Type|String|VIDEO\_CAMERA|影响通信体验的指标类型，取值：

 -   **VIDEO\_CAMERA**：摄像头码率。
-   **VIDEO\_CAMERA\_LARGE**：摄像头大流码率。
-   **VIDEO\_CAMERA\_SMALL**：摄像头小流码率。
-   **VIDEO\_CAMERA\_SUPER**：摄像头超大流码率。
-   **VIDEO\_SCREEN\_SHARE**：共享屏幕流码率。
-   **VIDEO\_STUCK\_CAMERA**：摄像头卡顿。
-   **VIDEO\_STUCK\_CAMERA\_LARGE**：摄像头大流卡顿。
-   **VIDEO\_STUCK\_CAMERA\_SMALL**：摄像头小流卡顿。
-   **VIDEO\_STUCK\_CAMERA\_SUPER**：摄像头超大流卡顿。
-   **VIDEO\_STUCK\_SCREEN\_SHARE**：屏幕共享卡顿。
-   **VIDEO\_VAGUE\_CAMERA**：摄像头模糊。
-   **VIDEO\_VAGUE\_CAMERA\_LARGE**：摄像头大流模糊。
-   **VIDEO\_VAGUE\_CAMERA\_SMALL**：摄像头小流模糊。
-   **VIDEO\_VAGUE\_CAMERA\_SUPER**：摄像头超大流模糊。
-   **VIDEO\_VAGUE\_SCREEN\_SHARE**：屏幕共享模糊。 |
|UserId|String|c906531af5f9\*\*\*\*|用户ID。 |
|Nodes|Array of Node| |视频指标趋势图坐标点列表。 |
|X|String|1548670256|视频指标趋势图中x轴横坐标。 |
|Y|String|123|视频指标趋势图中y轴纵坐标。 |
|AudioData|Array of QoeMetricDataItem| |音频数据。 |
|Type|String|AUDIO|影响通信体验的指标类型，取值：

 -   **AUDIO**：音频码率。
-   **AUDIO\_STUCK**：音频下行卡顿。 |
|UserId|String|c906531af5f9\*\*\*\*|用户ID。 |
|Nodes|Array of Node| |音频指标趋势图坐标点列表。 |
|X|String|1548670256|音频指标趋势图中x轴横坐标。 |
|Y|String|123|音频指标趋势图中y轴纵坐标。 |
|RequestId|String|963F15CA-9D61-4341-B9D0-123E97229829|请求ID。 |

## 示例

请求示例

```
POST api/call/describeQoeMetricData?AppId=9qb1****&ChannelId=311&CreatedTs=1615887685&DestroyedTs=1615888615&UserId=c906531af5f9**** HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeQoeMetricDataResponse>
<code>200</code>
<data>
    <RequestId>963F15CA-9D61-4341-B9D0-123E97229829</RequestId>
</data>
<httpStatusCode>200</httpStatusCode>
<requestId>963F15CA-9D61-4341-B9D0-123E97229829</requestId>
<successResponse>true</successResponse>
</DescribeQoeMetricDataResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "AudioData" : [ ],
    "RequestId" : "963F15CA-9D61-4341-B9D0-123E97229829",
    "VideoData" : [ ]
  },
  "httpStatusCode" : "200",
  "requestId" : "963F15CA-9D61-4341-B9D0-123E97229829",
  "successResponse" : true
}
```

