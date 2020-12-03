# StartRecordTask

调用StartRecordTask录制视频任务。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=StartRecordTask&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartRecordTask|操作接口名，系统规定参数。取值：**StartRecordTask**。 |
|AppId|String|是|yourAppId|应用ID。通过控制台创建和查询，仅支持传单个ID。 |
|ChannelId|String|是|yourChannelId|频道ID。仅支持传单个ID。 |
|TaskId|String|是|yourTaskId|任务ID。仅支持传单个ID。 |
|TemplateId|String|是|76dasgb\*\*\*\*|配置模板ID。 |
|SubSpecUsers.N|RepeatList|否|userID|指定该任务订阅的用户列表，默认订阅频道内全部用户，N表示的是数组的下标，取值范围：**1～16**。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|UserPanes.N.PaneId|Integer|否|2|窗格ID。N的取值：**1~16**。PaneID的取值：**0~15**。

 **说明：** 当指定的PaneId用户找不到的话，会默认显示其他的流，流的确定是根据用户加入频道的顺序。 |
|UserPanes.N.UserId|String|否|TestId|对应布局框格的用户ID。N的取值：**1~16**。 |
|UserPanes.N.SourceType|String|否|camera|对应布局的用户视频输入。取值：

 -   **camera**（默认）：视频流。
-   **shareScreen**：共享屏幕流。

 N的取值：**1~16**。 |
|UserPanes.N.Images.N.Url|String|否|https://www.test.com/image.jpg|图片的HTTP或HTTPS地址。 |
|UserPanes.N.Images.N.Display|Integer|否|1|图片显示，取值：

 -   **0**（None）：不显示。
-   **1**（Always）：总是显示。
-   **2**（Backup）：当前用户无视频流时显示。 |
|UserPanes.N.Images.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|UserPanes.N.Images.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|UserPanes.N.Images.N.Width|Float|否|0.2456|窗格宽，归一化百分比。 |
|UserPanes.N.Images.N.Height|Float|否|0.2456|窗格高，归一化百分比。 |
|UserPanes.N.Images.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|UserPanes.N.Texts.N.Text|String|否|text|文本内容。 |
|UserPanes.N.Texts.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|UserPanes.N.Texts.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|UserPanes.N.Texts.N.FontType|Integer|否|0|字体类型。取值：

 -   **0**（默认）：NOTO\_SERIF\_CJKSC\_REGULAR。
-   **1**：ALIBABA\_PUHUITI\_REGULAR。
-   **2**：ALIBABA\_PUHUITI\_BOLD。
-   **3**：ALIBABA\_PUHUITI\_Heavy。
-   **4**：ALIBABA\_PUHUITI\_LIGHT。
-   **5**：ALIBABA\_PUHUITI\_MEDIUM。 |
|UserPanes.N.Texts.N.FontSize|Integer|否|1|字体大小。字体合理范围**\(0, 72\]**。 |
|UserPanes.N.Texts.N.FontColor|Integer|否|1|文字颜色（RGB）。计算公式为R+G×256+B×65536，R（红）、G（绿）、B（蓝）的取值：**0~255**。 |
|UserPanes.N.Texts.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b\*\*\*\*|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=StartRecordTask
&AppId=yourAppId
&ChannelId=yourChannelId
&TaskId=yourTaskId
&TemplateId=76dasgb****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<StartRecordTaskResponse>
  <RequestId>760bad53276431c499e30dc36f6b****</RequestId>
</StartRecordTaskResponse>
```

`JSON` 格式

```
{
	"RequestId": "760bad53276431c499e30dc36f6b****"
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

|内部错误。 |
|TaskExisted

|task is already existed

|200

|任务已存在。 |
|InvalidLayoutID.Malformed

|The specified layout ID is malformed

|400

|参数LayoutId错误。 |
|InvalidMediaEncode.Malformed

|The specifed MediaEncode is malformed

|400

|参数MediaEncode错误。 |
|InvalidBackgroundColor.Malformed

|The specifed background color is malformed

|400

|参数BackgroundColor错误。 |
|InternalError

|The request processing has failed due to some unknown error, exception or failure.

|500

|内部错误。 |

