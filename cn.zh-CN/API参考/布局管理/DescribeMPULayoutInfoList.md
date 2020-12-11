# DescribeMPULayoutInfoList

调用DescribeMPULayoutInfoList获取旁路直播任务布局参数。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeMPULayoutInfoList&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeMPULayoutInfoList|操作接口名，系统规定参数，取值：**DescribeMPULayoutInfoList**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 您可以在控制台创建和查询。 |
|LayoutId|Long|否|10117|布局ID。 |
|Name|String|否|LayoutName|布局名称。 |
|PageNum|Long|否|1|页码。默认为**1**，取值范围大于**0**。 |
|PageSize|Long|否|10|每页显示数量。默认为**10**，取值范围大于**0**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalPage|Long|1|总页数。 |
|TotalNum|Long|1|总记录数。 |
|Layouts|Array of Layout| |布局列表。 |
|Layout| | | |
|AudioMixCount|Integer|3|最大混音个数。 |
|LayoutId|Long|1100|布局ID。 |
|Name|String|LayoutName|布局名称。 |
|Panes|Array of Panes| |布局的窗格参数。 |
|Panes| | | |
|Height|Float|0.5|窗格高，归一化百分比。 |
|MajorPane|Integer|0|指定主窗格：

 -   **0**：副窗格。
-   **1**：主窗格。

 每个布局只能有一个主窗格。 |
|PaneId|Integer|0|布局ID，从左上到右下排序，从0开始。 |
|Width|Float|0.5|窗格宽，归一化百分比。 |
|X|Float|0.5|坐标X，归一化百分比。 |
|Y|Float|0.5|坐标Y，归一化百分比。 |
|ZOrder|Integer|0|叠放顺序，0为最底层，1层在0层之上，以此类推。 |
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeMPULayoutInfoList
&AppId=yourAppId
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeMPULayoutInfoListResponse>
  <TotalNum>1</TotalNum>
  <TotalPage>1</TotalPage>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
  <Layouts>
        <AudioMixCount>3</AudioMixCount>
        <LayoutId>1100</LayoutId>
        <Name>LayoutName</Name>
        <Panes>
              <MajorPane>0</MajorPane>
              <ZOrder>0</ZOrder>
              <X>0.5</X>
              <Y>0.5</Y>
              <Height>0.5</Height>
              <Width>0.5</Width>
              <PaneId>0</PaneId>
        </Panes>
  </Layouts>
</DescribeMPULayoutInfoListResponse>
```

`JSON` 格式

```
{
    "TotalNum":"1",
    "TotalPage":"1",
    "RequestId":"760bad53276431c499e30dc36f6b26be",
    "Layouts":[
        {
            "AudioMixCount":"3",
            "LayoutId":"1100",
            "Name":"LayoutName",
            "Panes":[
                {
                    "MajorPane":"0",
                    "ZOrder":"0",
                    "X":"0.5",
                    "Y":"0.5",
                    "Height":"0.5",
                    "Width":"0.5",
                    "PaneId":"0"
                }
            ]
        }
    ]
}
```

