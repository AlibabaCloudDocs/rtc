# StartMPUTask {#reference3035 .reference}

调用StartMPUTask开始任务。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：StartMPUTask。|
|AppId|String|是|应用ID，创建应用后生成。|
|ChannelId|String|是|频道ID。|
|TaskID|String|是|任务ID, 此ID为旁路直播的标识，需保证唯一。|
|TaskProfile|String|是|任务计费配置，根据您的不同设置，进行收费。TaskProfile设置： -   4IN\_720P。
-   2IN\_720P。
-   1IN\_720P。
-   4IN\_360P。
-   2IN\_360P。
-   1IN\_360P。
-   Mixed\_Audio。
-   1IN\_Audio。

 |
|MediaEncode|Integer|是|编码选项，具体请参见本文中的MediaEncode枚举值。|
|BackgroundColor|Integer|是|背景色RGB，默认是0（黑色）。|
|LayoutIds|RepeatList|是|布局ID数据，用户可在一次任务中指定多个布局，系统会根据当时channel中的人数进行切换。详情请参见[布局](../../../../cn.zh-CN/录制&旁路直播/布局.md#)。|
|UserPanes|RepeatList|否|用户指定的布局参数。用户可以指定某个窗格\(pane\)展示一个指定的userID。|
|StreamURL|String|是|直播推流地址，生成规则请参见[推流地址与播流地址](https://helpcdn.aliyun.com/document_detail/87396.html)，对已开防盗链鉴权的域名，需要在推流地址中包含鉴权串。|

MediaEncode枚举值

|ID|分辨率|码流|帧率|
|--|---|--|--|
|0|audio only|—|—|
|1|360p|500Kbps|15fps|
|10|540p|700Kbps|24fps|
|20|720p|1Mbps|25fps|
|30|1080p|2Mbps|30fps|

UserPanes结构

|参数|类型|是否必选|描述|
|--|--|----|--|
|PaneId|Integer|是|布局ID，从左上到右下排序，从0开始。|
|UserId|String|是|对应布局框格的用户ID。|
|SourceType|String|是|对应布局的用户视频输入，camera和shareScreen两种。|

## 返回参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|RequestId|String|是|该条任务请求Id。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=StartMPUTask&AppId=xxxx&ChannelId=xxxTaskId=xxx&MediaEncode=2&BackgroundColor=0&LayoutIds.1=1&LayoutIds.2=2&UserPanes.0.PaneId=xxx&UserPanes.0.UserId=xxx&UserPanes.0.SourceType=xxx&UserPanes.1.PaneId=xxx&UserPanes.1.UserId=xxx&UserPanes.1.SourceType=xxx&StreamURL=xxx&<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
  "RequestId": "760bad53276431c499e30dc36f6b26be", 
}
```

## 特殊错误码 {#section_hc4_6v9_bcy .section}

|错误ID|错误代码|描述|Http 状态码|语义|
|----|----|--|--------|--|
|0x0702000C|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|0x07100001|TaskExisted|Task is already existed.|200|任务已存在。|
|0x0701000C|InvalidLayoutID.Malformed|The specified layoutID is malformed.|400|参数LayoutId错误。|
|0x0701000D|InvalidMediaEncode.Malformed|The specifed MediaEncode is malformed.|400|参数MediaEncode错误|
|0x0701000E|InvalidBackgroundColor.Malformed|The specifed BackgroundColoris malformed.|400|参数BackgroundColor错误。|
|0x0702000D|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|0x0702000E|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

