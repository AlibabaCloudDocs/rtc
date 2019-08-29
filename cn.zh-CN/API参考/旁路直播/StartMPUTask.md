# StartMPUTask {#doc_api_rtc_StartMPUTask .reference}

调用StartMPUTask开始任务。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=StartMPUTask&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartMPUTask|操作接口名，系统规定参数，取值：**StartMPUTask**。

 |
|AppId|String|是|yourAppId|应用ID，创建应用后生成。

 |
|ChannelId|String|是|yourChannelId|频道ID。

 |
|LayoutIds.N|RepeatList|是|1|布局ID数据，用户可在一次任务中指定多个布局，系统会根据当时channel中的人数进行切换。详情请参见[布局](~~109587~~)。

 N的取值范围**1**~**15**。

 |
|MediaEncode|Integer|是|2|编码选项，具体请参见本文中的MediaEncode枚举值。

 |
|StreamURL|String|是|yourStreamURL|直播推流地址，生成规则请参见[推流地址与播流地址（原画）](~~87396~~)。

 对已开防盗链鉴权的域名，需要在推流地址中包含鉴权串。

 |
|TaskId|String|是|yourTaskId|任务ID，此ID为旁路直播的标识，需保证唯一。

 字符只允许A-Za-z0-9\_-，长度限制64字节。

 |
|BackgroundColor|Integer|否|0|背景色RGB，默认是**0**（黑色）。

 |
|CropMode|Integer|否|0|视频的裁剪方式，默认值为**2**。

 -   **0**：不保持比例铺满。
-   **1**：保持比例裁剪。
-   **2**：保持比例留边。

 |
|TaskProfile|String|否|4IN\_720P|任务计费配置，根据您的不同设置，进行收费。TaskProfile设置：

 -   **4IN\_720P**。
-   **2IN\_720P**。
-   **1IN\_720P**。
-   **4IN\_360P**。
-   **2IN\_360P**。
-   **1IN\_360P**。
-   **Mixed\_Audio**。
-   **1IN\_Audio**。

 |
|UserPanes.N.PaneId|Integer|否|2|布局ID，从左上到右下排序，从0开始。N的取值范围**1**~**15**。

 |
|UserPanes.N.SourceType|String|否|camera|对应布局的用户视频输入，**camera**和**shareScreen**两种。N的取值范围**1**~**15**。

 |
|UserPanes.N.UserId|String|否|UserId|对应布局框格的用户ID。N的取值范围**1**~**15**。

 |

MediaEncode枚举值如下所示。

|ID

|分辨率

|码流

|帧率

|
|----|-----|----|----|
|0

|audio only

|—

|—

|
|1

|360p

|500Kbps

|15fps

|
|10

|540p

|700Kbps

|24fps

|
|20

|720p

|1Mbps

|25fps

|
|30

|1080p

|2Mbps

|30fps

|

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=StartMPUTask
&AppId=xxxx
&ChannelId=xxx
&TaskId=xxx
&MediaEncode=2
&BackgroundColor=0
&LayoutIds.1=1
&LayoutIds.2=2
&UserPanes.0.PaneId=xxx
&UserPanes.0.UserId=xxx
&UserPanes.0.SourceType=xxx
&UserPanes.1.PaneId=xxx
&UserPanes.1.UserId=xxx
&UserPanes.1.SourceType=xxx
&StreamURL=xxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StartMPUTaskResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</StartMPUTaskResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"760bad53276431c499e30dc36f6b26be"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

