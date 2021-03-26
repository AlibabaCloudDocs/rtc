# StartMPUTask

调用StartMPUTask开始旁路直播任务。

当您使用旁路转推服务时，阿里云视频直播服务有如下限制：

-   若未开启转码功能，默认每个账号下每个直播加速域名最多并发推送20个原画直播流。
-   若启用转码功能，默认每个账号下每个直播加速域名最多并发推送10个转码直播流。
-   如有特殊需求，请[提交工单](https://selfservice.console.aliyun.com/ticket/createIndex)申请开通。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=StartMPUTask&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartMPUTask|操作接口名，系统规定参数，取值：**StartMPUTask**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|ChannelId|String|是|yourChannelId|频道ID，仅支持传单个ID。 |
|StreamURL|String|是|rtmp://live-demo.com/live/stream|直播推流地址，仅支持传单个地址。生成规则请参见[推流地址和播放地址](~~199339~~)。

 **说明：**

-   对已开防盗链鉴权的域名，需要在推流地址中包含鉴权串。
-   禁止同一个StreamURL在不同任务中同时使用。
-   任务停止10S之内，禁止使用同一个StreamURL。 |
|TaskId|String|是|yourTaskId|任务ID，仅支持传单个ID。字符只允许**A-Za-z0-9\_-**，长度限制**55**字节。

 **说明：** 此ID为旁路转推的标识，需保证唯一。 |
|TaskProfile|String|否|4IN\_720P|任务计费配置，根据您的不同设置，进行收费。请参见下文中的TaskProfile枚举值。

 **说明：**

-   目前任务计费仅针对于混流转码模式。
-   编码选项MediaEncode的分辨率需要小于等于TaskProfile的分辨率。
-   布局最大窗格数需要小于等于TaskProfile的输入路数。
-   旁路转推服务API变更：此参数于2020年6月1日23:00时由可选项变更为必填项，若缺失该参数，则默认按照最高规格16IN\_1080P计费。 |
|TaskMode|Integer|否|0|任务模式。取值：

 -   **0**：通用模式（默认值）。
-   **1**：虚拟背景模式，此模式下支持对指定流开启人像分割功能。 |
|MixMode|Integer|否|0|混流模式。取值：

 -   **0**：单路转推，不混流转码，仅转推原始单路流，无需配置混流转码参数。
-   **1**：混流转码（默认值），支持混流转码输出。

 **说明：**

-   单路转推模式下有效参数：**StreamType**、**SourceType**。
-   混流转码模式下有效参数：**TaskProfile**、**MediaEncode**、**LayoutIds**、**BackgroundColor**、**SubSpecUsers**、**CropMode**、**UserPanes**、**Backgrounds**、**Watermarks**。 |
|CropMode|Integer|否|1|视频的裁剪方式。取值：

 -   **1**：保持比例裁剪。
-   **2**：保持比例留边（默认值）。 |
|MediaEncode|Integer|否|2|编码选项，请参见下文中的MediaEncode枚举值。 |
|SourceType|String|否|camera|单路转推模式下用户视频输入流。取值：

 -   **camera**：摄像头。
-   **shareScreen**：屏幕共享。 |
|StreamType|Integer|否|0|单路转推模式下转推音频流。取值：

 -   **0**：转推原始流。
-   **1**：仅转推音频流。
-   **2**：仅转推视频流。

 默认转推原始流。 |
|BackgroundColor|Integer|否|0|背景色RGB，默认是**0**（黑色）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：0~255。 |
|SubSpecUsers.N|RepeatList|否|userID|指定该任务订阅的用户列表，默认订阅频道内全部用户，N表示的是数组的下标，取值范围：**1**～**16**。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|SubSpecAudioUsers.N|RepeatList|否|audioUserID|指定订阅房间里哪些用户音频流（输入allStream表示混所有人音频）。N表示的是数组的下标，取值范围：**1**～**16**。

 **说明：** N需要从1开始并从小到大，不能中断，要连续。 |
|LayoutIds.N|RepeatList|否|1|布局ID数据，您可在一次任务中指定多个布局，系统会根据当时频道中的人数进行切换。N表示的是数组的下标，取值范围是1～16，相当于一个旁路任务中最多可以同时设置16种布局。详情请参见[布局](~~109587~~)。

 **说明：**

-   N需要从1开始并从小到大，不能中断，要连续。
-   设置的布局窗格数不能相同。例：官网上的布局ID 2和3 的不能同时设置，他们两个的窗格数相同都是2。 |
|UserPanes.N.PaneId|Integer|否|2|窗格ID，N的取值：**1**~**16**。PaneID的取值：**0**~**15**。

 **说明：** 当指定的PaneId用户找不到的话，会默认显示其他的流，流的确定是根据用户加入频道的顺序。 |
|UserPanes.N.UserId|String|否|TestId|对应布局框格的用户ID。N的取值：**1**~**16**。 |
|UserPanes.N.SourceType|String|否|camera|对应布局的用户视频输入。取值：

 -   **camera**：视频流（默认值）。
-   **shareScreen**：共享屏幕流。

 N的取值：**1**~**16**。 |
|UserPanes.N.SegmentType|Integer|否|0|人像分割类型。取值：

 -   **0**：无人像分割（默认值）。
-   **1**：人像分割，仅在虚拟背景模式有效。 |
|UserPanes.N.Images.N.Url|String|否|https://www.test.com/image.jpg|图片的HTTP或HTTPS地址。 |
|UserPanes.N.Images.N.Display|Integer|否|1|图片显示，取值：

 -   **0（None）**：不显示。
-   **1（Always）**：总是显示。
-   **2（Backup）**：当前用户无视频流时显示。 |
|UserPanes.N.Images.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|UserPanes.N.Images.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|UserPanes.N.Images.N.Width|Float|否|0.2456|窗格宽，归一化百分比。 |
|UserPanes.N.Images.N.Height|Float|否|0.2456|窗格高，归一化百分比。 |
|UserPanes.N.Images.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|UserPanes.N.Texts.N.Text|String|否|text|文本内容。 |
|UserPanes.N.Texts.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|UserPanes.N.Texts.N.Y|Float|否|0.2456|坐标Y，归一化百分比。 |
|UserPanes.N.Texts.N.FontType|Integer|否|0|字体类型，取值：

 -   **0**：NOTO\_SERIF\_CJKSC\_REGULAR（默认值）
-   **1**：ALIBABA\_PUHUITI\_REGULAR
-   **2**：ALIBABA\_PUHUITI\_BOLD
-   **3**：ALIBABA\_PUHUITI\_Heavy
-   **4**：ALIBABA\_PUHUITI\_LIGHT
-   **5**：ALIBABA\_PUHUITI\_MEDIUM |
|UserPanes.N.Texts.N.FontSize|Integer|否|1|字体大小，字体合理范围

\(\*\*0\*\*, \*\*72\*\*\] \)|
|UserPanes.N.Texts.N.FontColor|Integer|否|0|文字颜色（RGB）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：**0**~**255**。 |
|UserPanes.N.Texts.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|Backgrounds.N.Url|String|否|https://www.test.com/image.jpg|图片的HTTP或HTTPS地址。 |
|Backgrounds.N.Display|Integer|否|1|图片显示，取值：

 -   **0（None）**：不显示。
-   **1（Always）**：总是显示。 |
|Backgrounds.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|Backgrounds.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|Backgrounds.N.Width|Float|否|0.2456|窗格宽，归一化百分比。 |
|Backgrounds.N.Height|Float|否|0.2456|窗格高，归一化百分比。 |
|Backgrounds.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|Watermarks.N.Url|String|否|https://www.test.com/image.jpg|图片的HTTP或HTTPS地址。 |
|Watermarks.N.Alpha|Float|否|0|透明度。0.0表示透明，1.0表示完全不透明。 |
|Watermarks.N.Display|Integer|否|0|图片显示，取值：

 -   **0（None）**：不显示。
-   **1（Always）**：总是显示。 |
|Watermarks.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|Watermarks.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|Watermarks.N.Width|Float|否|0.2456|窗格宽，归一化百分比。 |
|Watermarks.N.Height|Float|否|0.2456|窗格高，归一化百分比。 |
|Watermarks.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|ClockWidgets.N.X|Float|否|0.7576|坐标X，归一化百分比。 |
|ClockWidgets.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|ClockWidgets.N.FontType|Integer|否|0|字体类型，取值：

 -   **0**：NOTO\_SERIF\_CJKSC\_REGULAR（默认值）
-   **1**：ALIBABA\_PUHUITI\_REGULAR
-   **2**：ALIBABA\_PUHUITI\_BOLD
-   **3**：ALIBABA\_PUHUITI\_Heavy
-   **4**：ALIBABA\_PUHUITI\_LIGHT
-   **5**：ALIBABA\_PUHUITI\_MEDIUM |
|ClockWidgets.N.FontSize|Integer|否|1|字体大小，字体合理范围

\(\*\*0\*\*, \*\*72\*\*\]。 \)|
|ClockWidgets.N.FontColor|Integer|否|0|文字颜色（RGB）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：**0**~**255**。 |
|ClockWidgets.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|PayloadType|Integer|否|0|载荷类型。取值：

 -   **0**：不使用载荷。
-   **1**：使用VideoSEI。 |
|ReportVad|Integer|否|0|语音激励标志。取值：

 -   **0**：不传递语音激励信息。
-   **1**：传递语音激励信息。 |
|RtpExtInfo|Integer|否|0|RTP扩展头信息。取值：

 -   **0**：不传递。
-   **1**：传递。 |
|TimeStampRef|Long|否|15273582735|时间戳。 |
|VadInterval|Long|否|86400|语音激励的回调间隔。 |

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

**说明：** 当用户使用纯音频直播的时候需要注意的问题，然后直接跳转常见问题中的[纯音频直播](https://helpcdn.aliyun.com/document_detail/159390.html?spm=a2c4g.11174283.6.729.445a3c3d4LDYq5)。

**TaskProfile**枚举值：

**说明：** Mixed\_Audio的最大输入路数为不限，其余规格根据第一个数字判断支持最大输入路数，例如：4IN\_720P代表支持最大输入路数为4。

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
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=StartMPUTask
&AppId=yourAppId
&ChannelId=yourChannelId
&TaskId=yourTaskId
&MediaEncode=2
&BackgroundColor=0
&LayoutIds.1=2
&UserPanes.1.PaneId=0
&UserPanes.1.UserId=TestId
&UserPanes.1.SourceType=camera
&StreamURL=rtmp://123.com/XX
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<StartMPUTaskResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</StartMPUTaskResponse>
```

`JSON`格式

```
{
  "RequestId": "760bad53276431c499e30dc36f6b26be"
}
```

