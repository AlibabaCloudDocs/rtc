# UpdateMPULayout

调用UpdateMPULayout更新任务的布局。

**说明：** 该接口需要在任务正常运行的时候调用，任务未开始、已结束或异常状态都调用无效。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=UpdateMPULayout&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateMPULayout|操作接口名，系统规定参数，取值：**UpdateMPULayout**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 可通过控制台创建和查询。 |
|LayoutIds.N|RepeatList|是|1|布局ID数据，用户可在一次任务中指定多个布局，系统会根据当时channel（频道）中的人数进行切换。详情请参见[布局](https://help.aliyun.com/document_detail/109587.html)。 |
|TaskId|String|是|testId|任务ID，仅支持传单个ID，通过StartMpuTask接口设置。 |
|CropMode|Integer|否|1|视频的裁剪模式。取值：

 -   **1**：保持比例裁剪。
-   **2**（默认）：保持比例留边。 |
|BackgroundColor|Integer|否|0|背景色RGB，默认是**0**（黑色）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：**0**~**255**。 |
|UserPanes.N.PaneId|Integer|否|2|窗格ID，N的取值范围是**1**~**16**。PaneID的取值范围是**0**~**15**。 |
|UserPanes.N.UserId|String|否|TestUserID|对应布局窗格的用户ID，N的取值：**1**~**16**。 |
|UserPanes.N.SourceType|String|否|camera|对应布局的用户视频输入，N的取值：**1**~**16**。

 -   **camera**：相机流。
-   **shareScreen**：共享屏幕流。 |
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
|UserPanes.N.Texts.N.Y|Float|否|0.7576|坐标Y，归一化百分比。 |
|UserPanes.N.Texts.N.FontType|Integer|否|0|字体类型，取值：

 -   **0**：NOTO\_SERIF\_CJKSC\_REGULAR
-   **1**：ALIBABA\_PUHUITI\_REGULAR
-   **2**：ALIBABA\_PUHUITI\_BOLD
-   **3**：ALIBABA\_PUHUITI\_Heavy
-   **4**：ALIBABA\_PUHUITI\_LIGHT
-   **5**：ALIBABA\_PUHUITI\_MEDIUM

 默认取值为0。 |
|UserPanes.N.Texts.N.FontSize|Integer|否|1|字体大小，字体合理范围

\(\*\*0\*\*, \*\*72\*\*\]。 \)|
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
|Watermarks.N.Display|Integer|否|1|图片显示，取值：

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

 -   **0**：NOTO\_SERIF\_CJKSC\_REGULAR
-   **1**：ALIBABA\_PUHUITI\_REGULAR
-   **2**：ALIBABA\_PUHUITI\_BOLD
-   **3**：ALIBABA\_PUHUITI\_Heavy
-   **4**：ALIBABA\_PUHUITI\_LIGHT
-   **5**：ALIBABA\_PUHUITI\_MEDIUM

 默认取值为0。 |
|ClockWidgets.N.FontSize|Integer|否|1|字体大小，字体合理范围

\(\*\*0\*\*, \*\*72\*\*\]。 \)|
|ClockWidgets.N.FontColor|Integer|否|0|文字颜色（RGB）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：**0**~**255**。 |
|ClockWidgets.N.ZOrder|Integer|否|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com?Action=UpdateMPULayout
&AppId=yourAppId
&TaskId=testId
&BackgroundColor=0
&LayoutIds.1=2
&UserPanes.1.PaneId=2
&UserPanes.1.UserId=TestUserID
&UserPanes.1.SourceType=camera
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UpdateMPULayoutResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</UpdateMPULayoutResponse>
```

`JSON` 格式

```
{
  "RequestId": "760bad53276431c499e30dc36f6b26be"
}
```

