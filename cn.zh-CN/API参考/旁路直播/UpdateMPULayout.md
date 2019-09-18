# UpdateMPULayout {#doc_api_rtc_UpdateMPULayout .reference}

调用UpdateMPULayout更新任务的布局。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=UpdateMPULayout&type=RPC&version=2018-01-11)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateMPULayout|操作接口名，系统规定参数，取值：**UpdateMPULayout**。

 |
|AppId|String|是|yourAppId|应用ID，控制台查询。

 |
|LayoutIds.N|RepeatList|是|1|布局ID数据，用户可在一次任务中指定多个布局，系统会根据当时channel（频道）中的人数进行切换。详情请参见[布局](https://help.aliyun.com/document_detail/109587.html)。

 N的取值范围**1**~**15**。

 |
|TaskId|String|是|abcde|任务ID，此ID为旁路直播的标识，需保证唯一。

 字符只允许A-Za-z0-9\_-，长度限制64字节。

 |
|BackgroundColor|Integer|否|0|背景色RGB，默认是**0**（黑色）。

 |
|CropMode|Integer|否|2|视频的裁剪模式：

 -   **0**：不保持比例铺满。
-   **1**：保持比例裁剪。
-   **2**（默认）：保持比例留边。

 |
|UserPanes.N.PaneId|Integer|否|2|布局ID，从左上到右下排序，从0开始。

 N的取值范围**1**~**15**。

 |
|UserPanes.N.SourceType|String|否|camera|对应布局的用户视频输入，**camera**和**shareScreen**两种。

 |
|UserPanes.N.UserId|String|否|UserId|对应布局的用户视频输入，**camera**和**shareScreen**两种。

 N的取值范围**1**~**15**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://rtc.aliyuncs.com?Action=UpdateMPULayout
&AppId=xxxx
&TaskId=xxx
&BackgroundColor=0
&LayoutIds.1=1
&LayoutIds.1=2
&UserPanes.0.PaneId=xxx
&UserPanes.0.UserId=xxx
&UserPanes.0.SourceType=xxx
&UserPanes.1.PaneId=xxx
&UserPanes.1.UserId=xxx
&UserPanes.1.SourceType=xxx
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateMPULayoutResponse>
	  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</UpdateMPULayoutResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"760bad53276431c499e30dc36f6b26be"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/rtc)查看更多错误码。

