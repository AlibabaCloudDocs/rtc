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
|TaskId|String|是|yourTaskId|任务ID。仅支持传单个ID，需保证唯一。由1~55位大小写字母、数字、下划线、短划线（-）组成。 |
|TemplateId|String|是|76dasgb\*\*\*\*|配置模板ID。 |
|TaskProfile|String|否|4IN\_1080P|任务计费配置，根据您的不同设置，进行收费。请参见下文中的TaskProfile枚举值。

 **说明：**

-   编码选项MediaEncode的分辨率需要小于等于TaskProfile的分辨率。
-   布局最大窗格数需要小于等于TaskProfile的输入路数。 |
|MediaEncode|Integer|否|20|编码选项，请参见下文中的MediaEncode枚举值。 |
|SourceType|String|否|camera|单流录制模式下视频源，取值：

 -   **camera**：摄像头。
-   **shareScreen**：屏幕共享。

 **说明：** 如果视频源为shareScreen，且仅推摄像头流，则录制摄像头流；如果同时推屏幕共享流，则录制屏幕共享流。 |
|StreamType|Integer|否|0|单流录制模式，取值：

 -   **0**（默认值）：录制原始流。
-   **1**：仅录制音频流。 |
|MixMode|Integer|否|1|录制模式，取值：

 -   **0**：单流录制，不允许中间修改任务参数（不允许调用UpdateRecordTask接口修改任务参数）。
-   **1**（默认值）：合流录制，支持多画面合流输出。

 **说明：**

-   单流录制模式下有效参数：StreamType、SourceType。
-   合流录制模式下有效参数：TaskProfile、MediaEncode、LayoutIds、BackgroundColor、SubSpecUsers、CropMode、UserPanes、Backgrounds、Watermarks。 |
|SubSpecUsers.N|RepeatList|否|userID|指定该任务订阅的用户列表，默认订阅频道内全部用户，N表示的是数组的下标，取值范围：**1～16**。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|SubSpecAudioUsers.N|RepeatList|否|1|指定订阅房间里有哪些用户音频流（输入allStream表示混所有人音频流）。N表示的是数组的下标，取值范围：1～16。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|SubSpecShareScreenUsers.N|RepeatList|否|1|指定订阅房间里有哪些用户屏幕共享流（输入allStream表示混所有人屏幕共享流）。N表示的是数组的下标，取值范围：1～16。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|SubSpecCameraUsers.N|RepeatList|否|1|指定订阅房间里有哪些用户摄像头流（输入allStream表示混所有人摄像头流）。N表示的是数组的下标，取值范围：1～16。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|UnsubSpecAudioUsers.N|RepeatList|否|1|指定非订阅房间里有哪些用户音频流（输入allStream表示混所有人音频流）。N表示的是数组的下标，取值范围：1～16。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|UnsubSpecShareScreenUsers.N|RepeatList|否|1|指定非订阅房间里有哪些用户屏幕共享流（输入allStream表示混所有人屏幕共享流）。N表示的是数组的下标，取值范围：1～16。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|UnsubSpecCameraUsers.N|RepeatList|否|1|指定非订阅房间里有哪些用户摄像头流（输入allStream表示混所有人摄像头流）。N表示的是数组的下标，取值范围：1～16。

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

**MediaEncode枚举值：**

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

**TaskProfile枚举值：**

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
|RequestId|String|760bad53276431c499e30dc36f6b\*\*\*\*|请求ID。 |

**录制结果回调**

录制产生的结果文件写入到用户MNS队列或者将结果文件通过JSON格式以HTTP POST方式回调，参数定义如下所示：

|参数名称

|类型

|说明 |
|------|----|----|
|AppId

|String

|应用ID。 |
|ChannelId

|String

|频道ID。 |
|TaskId

|String

|录制任务ID。 |
|Event

|String

|事件类型，目前仅支持FileCreated事件。 |
|MsgId

|String

|消息ID。 |
|StartTime

|String

|录制开始时间。 |
|StopTime

|String

|录制结束时间。 |
|Url

|String

|录制到OSS的文件HTTP地址。 |

示例说明：

```

{
    "AppId": "9q****",
    "ChannelId": "record-004",
    "Duration": 1792.257,
    "Event": "FileCreated",
    "MsgId": "83eaaf62-19e8-45df-929b-79f4753b****",
    "StartTime": "2020-09-02T10:23:54Z",
    "StopTime": "2020-09-02T10:53:46Z",
    "TaskId": "task-005",
    "Url": "http://rtc-record.oss-cn-shanghai.aliyuncs.com/record/0902-1/9q****/record-004_task-005/2020-09-02-18-23-56_2020-09-02-18-53-56.m3u8"
}

```

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

`XML`格式

```
<StartRecordTaskResponse>
  <RequestId>760bad53276431c499e30dc36f6b****</RequestId>
</StartRecordTaskResponse>
```

`JSON`格式

```
{"RequestId":"760bad53276431c499e30dc36f6b****"}
```

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

