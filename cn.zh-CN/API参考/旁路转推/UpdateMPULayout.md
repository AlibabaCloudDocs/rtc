# UpdateMPULayout

调用UpdateMPULayout更新任务的布局。

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
|CropMode|Integer|否|2|视频的裁剪模式。取值：

 -   **0**：不保持比例铺满。
-   **1**：保持比例裁剪。
-   **2**（默认）：保持比例留边。 |
|BackgroundColor|Integer|否|0|背景色RGB，默认是**0**（黑色）。

 计算公式为`R + G × 256 + B × 65536`，R（红）、G（绿）、B（蓝）的取值：0~255。 |
|UserPanes.N.PaneId|Integer|否|2|窗格ID，N的取值范围是**1**~**16**。PaneID的取值范围是**0**~**15**。 |
|UserPanes.N.UserId|String|否|TestUserID|对应布局窗格的用户ID，N的取值：**1**~**16**。 |
|UserPanes.N.SourceType|String|否|camera|对应布局的用户视频输入，N的取值：**1**~**16**。

 -   **camera**：相机流。
-   **shareScreen**：共享屏幕流。 |

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

