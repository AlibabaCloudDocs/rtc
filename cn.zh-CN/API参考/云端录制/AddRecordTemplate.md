# AddRecordTemplate

调用AddRecordTemplate添加录制配置模板。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=AddRecordTemplate&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddRecordTemplate|操作接口名，系统规定参数。取值：AddRecordTemplate。 |
|AppId|String|是|yourAppId|应用ID。通过控制台创建和查询，仅支持传单个ID。 |
|FileSplitInterval|Integer|是|1800|录制文件切割时长（大于等于1800）。单位：秒。 |
|Formats.N|RepeatList|是|mp4|录制文件格式。当前文件格式仅支持：**m3u8、mp4、flv**。

 **说明：** 文件格式仅支持小写。 |
|LayoutIds.N|RepeatList|是|2|布局ID组。 |
|MediaEncode|Integer|是|20|编码选项。 |
|Name|String|是|录制模板|录制配置模板名称。 |
|OssBucket|String|是|rtc-record-oss|录制文件存储的OSS bucket。

 **说明：** 目前仅支持上海区域OSS bucket。 |
|OssFilePrefix|String|是|record/\{AppId\}/\{ChannelId\_TaskId\}/\{EscapedStartTime\}\_\{EscapedEndTime\}|录制文件命名规则。 |
|TaskProfile|String|是|4IN\_1080P|任务计费配置。 |
|BackgroundColor|Integer|否|0|背景色RGB。默认是0（黑色）。计算公式为R+G×256+B×65536，R（红）、G（绿）、B（蓝）的取值：**0~255**。 |
|DelayStopTime|Integer|否|180|延时停止录制的时间。单位：秒。默认值为**180**秒。 |
|MnsQueue|String|否|record-callback-queue|录制事件回调消息队列。 |
|HttpCallbackUrl|String|否|http://demo.com/callback|录制事件Http回调地址。 |
|Backgrounds.N.Url|String|否|https://www.test.com/image.jpg|图片的HTTP或HTTPS地址。 |
|Backgrounds.N.Display|Integer|否|0|图片显示。取值：

 -   **0**（None）不显示。
-   **1**（Always）：总是显示。 |
|Backgrounds.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|Backgrounds.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|Backgrounds.N.Width|Float|否|0.2456|窗格宽，归一化百分比。 |
|Backgrounds.N.Height|Float|否|0.2456|窗格高，归一化百分比。 |
|Backgrounds.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|Watermarks.N.Url|String|否|https://www.test.com/image.jpg|图片的HTTP或HTTPS地址。 |
|Watermarks.N.Alpha|Float|否|0|透明度。0.0表示透明，1.0表示完全不透明。 |
|Watermarks.N.Display|Integer|否|0|图片显示。取值：

 -   **0**（None）不显示。
-   **1**（Always）：总是显示。 |
|Watermarks.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|Watermarks.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|Watermarks.N.Width|Float|否|0.2456|窗格宽，归一化百分比。 |
|Watermarks.N.Height|Float|否|0.2456|窗格高，归一化百分比。 |
|Watermarks.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|ClockWidgets.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|ClockWidgets.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|ClockWidgets.N.FontType|Integer|否|0|字体类型，取值：

 -   **0**：NOTO\_SERIF\_CJKSC\_REGULAR
-   **1**：ALIBABA\_PUHUITI\_REGULAR
-   **2**：ALIBABA\_PUHUITI\_BOLD
-   **3**：ALIBABA\_PUHUITI\_Heavy
-   **4**：ALIBABA\_PUHUITI\_LIGHT
-   **5**：ALIBABA\_PUHUITI\_MEDIUM

 默认取值为**0**。 |
|ClockWidgets.N.FontSize|Integer|否|1|字体大小。字体合理范围**\(0, 72\]**。 |
|ClockWidgets.N.FontColor|Integer|否|0|文字颜色（RGB）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：**0**~**255**。 |
|ClockWidgets.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|该条任务请求ID。 |
|TemplateId|String|76dasgb\*\*\*\*|录制配置模板ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=AddRecordTemplate
&AppId=yourAppId
&FileSplitInterval=1800
&Formats.1=MP4
&LayoutIds.1=2
&MediaEncode=20
&Name=录制模板
&OssBucket=rtc-record-oss
&OssFilePrefix=record/{AppId}/{ChannelId_TaskId}/{EscapedStartTime}_{EscapedEndTime}
&TaskProfile=4IN_1080P
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<AddRecordTemplateResponse>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
  <TemplateId>76dasgb****</TemplateId>
</AddRecordTemplateResponse>
```

`JSON`格式

```
{
	"RequestId": "760bad53276431c499e30dc36f6b26be",
	"TemplateId": "76dasgb****"
}
```

## 特殊错误码

|错误ID

|错误代码

|描述

|Http 状态码 |
|------|------|----|----------|
|InternalError

|The request processing has failed due to some unknown error, exception or failure.

|500

|内部错误 |

