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
|LayoutIds.N|RepeatList|是|2|布局ID数据，您可在一次任务中指定多个布局，系统会根据当时频道中的人数进行切换。N表示数组的下标，取值范围1～16，相当于一个旁路任务中最多可以同时设置16种布局。详情请参见[布局说明](~~109587~~)。

 **说明：**

-   N需要从1开始并从小到大，不能中断，要连续。
-   设置的布局窗格数不能相同。例如：官网上的布局ID 2和3不能同时设置，因为他们两个的窗格数相同都是2。 |
|MediaEncode|Integer|是|20|编码选项，请参见下文中的MediaEncode枚举值。 |
|Name|String|是|录制模板|录制配置模板名称。 |
|OssBucket|String|是|rtc-record-oss|录制文件存储的OSS bucket。

 **说明：** 目前仅支持上海区域OSS bucket。 |
|OssFilePrefix|String|是|record/\{AppId\}/\{ChannelId\_TaskId\}/\{EscapedStartTime\}\_\{EscapedEndTime\}|录制文件命名规则。

 **说明：** 为确保录制的文件名称唯一，目前录制文件的命名规则为record/\{AppId\}/\{ChannelId\_TaskId\}/\{EscapedStartTime\}\_\{EscapedEndTime\}。 |
|TaskProfile|String|是|4IN\_1080P|任务计费配置，根据您的不同设置，进行收费。请参见下文中的TaskProfile枚举值。

 **说明：**

-   编码选项MediaEncode的分辨率需要小于等于TaskProfile的分辨率。
-   布局最大窗格数需要小于等于TaskProfile的输入路数。 |
|BackgroundColor|Integer|否|0|背景色RGB。默认是0（黑色）。计算公式为R+G×256+B×65536，R（红）、G（绿）、B（蓝）的取值：**0~255**。 |
|DelayStopTime|Integer|否|180|延时停止录制的时间。单位：秒。默认值为**180**秒。 |
|MnsQueue|String|否|record-callback-queue|录制事件回调消息队列。

 **说明：** 此参数和HttpCallbackUrl必须输入其中某一个，不能两者都输入或都不输入。 |
|HttpCallbackUrl|String|否|http://demo.com/callback|录制事件Http回调地址。

 **说明：** 此参数和MnsQueue必须输入其中某一个，不能两者都输入或都不输入。 |
|Backgrounds.N.Url|String|否|https://www.test.com/image.jpg|背景图片的HTTP或HTTPS地址。 |
|Backgrounds.N.Display|Integer|否|0|背景图片显示。取值：

 -   **0**（None）不显示。
-   **1**（Always）：总是显示。 |
|Backgrounds.N.X|Float|否|0.7576|背景图片坐标X，归一化百分比。 |
|Backgrounds.N.Y|Float|否|0.7576|背景图片坐标Y，归一化百分比。 |
|Backgrounds.N.Width|Float|否|0.2456|背景图片窗格宽，归一化百分比。 |
|Backgrounds.N.Height|Float|否|0.2456|背景图片窗格高，归一化百分比。 |
|Backgrounds.N.ZOrder|Integer|否|0|背景图片叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|Watermarks.N.Url|String|否|https://www.test.com/image.jpg|水印的HTTP或HTTPS地址。 |
|Watermarks.N.Alpha|Float|否|0|水印透明度。0.0表示透明，1.0表示完全不透明。 |
|Watermarks.N.Display|Integer|否|0|水印显示。取值：

 -   **0**（None）不显示。
-   **1**（Always）：总是显示。 |
|Watermarks.N.X|Float|否|0.7576|水印坐标X，归一化百分比。 |
|Watermarks.N.Y|Float|否|0.7576|水印坐标Y，归一化百分比。 |
|Watermarks.N.Width|Float|否|0.2456|水印窗格宽，归一化百分比。 |
|Watermarks.N.Height|Float|否|0.2456|水印窗格高，归一化百分比。 |
|Watermarks.N.ZOrder|Integer|否|0|水印叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|ClockWidgets.N.X|Float|否|0.7576|时钟坐标X，归一化百分比。 |
|ClockWidgets.N.Y|Float|否|0.7576|时钟坐标Y，归一化百分比。 |
|ClockWidgets.N.FontType|Integer|否|0|时钟字体类型，取值：

 -   **0**：NOTO\_SERIF\_CJKSC\_REGULAR
-   **1**：ALIBABA\_PUHUITI\_REGULAR
-   **2**：ALIBABA\_PUHUITI\_BOLD
-   **3**：ALIBABA\_PUHUITI\_Heavy
-   **4**：ALIBABA\_PUHUITI\_LIGHT
-   **5**：ALIBABA\_PUHUITI\_MEDIUM

 默认取值为**0**。 |
|ClockWidgets.N.FontSize|Integer|否|1|时钟字体大小。字体合理范围**\(0, 72\]**。 |
|ClockWidgets.N.FontColor|Integer|否|0|时钟文字颜色（RGB）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：**0**~**255**。 |
|ClockWidgets.N.ZOrder|Integer|否|0|时钟叠放顺序，0为最底层，1层在0层之上，以此类推。 |

**MediaEncode**枚举值如下所示。

|ID

|宽

|高

|码流（kps）

|帧率（fps） |
|----|---|---|---------|---------|
|0

|0

|0

|64

|0 |
|1

|640

|360

|500

|15 |
|54

|360

|640

|500

|30 |
|53

|360

|640

|500

|15 |
|52

|640

|360

|500

|30 |
|10

|960

|540

|700

|24 |
|20

|1280

|720

|1024

|25 |
|22

|720

|1280

|1024

|30 |
|23

|800

|600

|1024

|30 |
|30

|1920

|1080

|2048

|30 |
|31

|1080

|1920

|2048

|30 |
|24

|750

|780

|1024

|30 |
|25

|750

|540

|700

|30 |
|26

|720

|1280

|2048

|30 |
|27

|1280

|720

|2048

|30 |
|28

|1280

|720

|3096

|30 |
|32

|1024

|768

|1024

|24 |
|33

|1280

|960

|1024

|24 |
|34

|1024

|768

|2048

|24 |
|35

|1280

|960

|2048

|24 |
|36

|1280

|720

|1024

|24 |
|37

|1280

|720

|2048

|24 |
|38

|540

|960

|750

|15 |
|39

|540

|960

|1500

|30 |
|40

|1280

|720

|1200

|15 |
|41

|720

|1280

|1200

|15 |
|42

|720

|1280

|1500

|15 |
|43

|540

|960

|1200

|15 |

**TaskProfile**枚举值：

**说明：** Mixed\_Audio（纯音频）不限制最大输入路数，其余规格根据第一个数字判断支持最大输入路数，例如：4IN\_720P代表支持最大输入路数为4。

|-

|1080P

|720P

|360P

|Audio |
|---|-------|------|------|-------|
|1IN

|1IN\_1080P

|1IN\_720P

|1IN\_360P

|无 |
|2IN

|2IN\_1080P

|2IN\_720P

|2IN\_360P

|无 |
|4IN

|4IN\_1080P

|4IN\_720P

|4IN\_360P

|无 |
|9IN

|9IN\_1080P

|9IN\_720P

|9IN\_360P

|无 |
|12IN

|12IN\_1080P

|12IN\_720P

|12IN\_360P

|无 |
|16IN

|16IN\_1080P

|16IN\_720P

|16IN\_360P

|无 |
|Mixed

|无

|无

|无

|Mixed\_Audio |

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

