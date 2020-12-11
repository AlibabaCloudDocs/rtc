# ModifyMPULayout

调用ModifyMPULayout修改旁路直播布局。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=ModifyMPULayout&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyMPULayout|操作接口名，系统规定参数，取值：**ModifyMPULayout**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|LayoutId|Long|是|10117|布局ID。 |
|Name|String|否|LayoutName|布局名称。 |
|AudioMixCount|Integer|否|3|最大混音个数。取值范围：**0**~**6**。 |
|Panes.N.PaneId|Integer|否|0|布局窗口ID。从左上到右下排序，从0开始。 |
|Panes.N.MajorPane|Integer|否|0|指定主窗格：

 -   **0**：副窗格。
-   **1**：主窗格。

 每个布局只能有一个主窗格。 |
|Panes.N.X|Float|否|0.7576|坐标，归一化百分比。坐标X取值范围：**0.0≤X≤1.0**。 |
|Panes.N.Y|Float|否|0.7576|坐标Y，归一化百分比。坐标Y取值范围：**0.0≤Y≤1.0**。 |
|Panes.N.Width|Float|否|0.2456|窗格宽，归一化百分比。Width取值范围：**0.0<Width≤1.0**。 |
|Panes.N.Height|Float|否|0.2456|窗格高，归一化百分比。Height取值范围：**0.0<Height≤1.0**。 |
|Panes.N.ZOrder|Integer|否|0|叠放顺序。0为最底层，1层在0层之上，以此类推。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=ModifyMPULayout
&AppId=yourAppId
&LayoutId=10117
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifyMPULayoutResponse>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
</ModifyMPULayoutResponse>
```

`JSON` 格式

```
{"RequestId":"760bad53276431c499e30dc36f6b26be"}
```

