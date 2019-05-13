# DescribeRtcChannelCntData {#reference_263604 .reference}

调用DescribeRtcChannelCntData查询应用在一段时间内的活跃频道数，即发生通信的频道数。

## 请求参数 {#section_ru0_djs_edm .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeRtcChannelCntData。|
|AppId|String|否|应用id，不填则返回所有AppId的汇总数据。|
|StartTime|String|是|起始时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|EndTime|String|是|结束时间，UTC格式，例如：2018-01-29T00:00:00Z。|
|Interval|Enum|否|时间粒度参数，取值为 3600（小时粒度） 或 86400（天粒度），默认为 3600。|

## 返回参数 {#section_hxq_3r7_2ku .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求Id。|
|ChannelCntDataPerInterval|—|活跃频道统计数据结构。|
|└TimeStamp|String|时间戳，UTC格式，例如：2018-01-29T00:00:00Z。|
|└ChannelCnt|Log|活跃频道数量统计（时间单元累计）。|

## 示例 {#section_vtx_om0_o47 .section}

请求示例

``` {#codeblock_19p_yy0_19i}
https://rtc.aliyuncs.com?Action=DescribeRtcChannelCntData&AppId=xxx&StartTime=2018-01-29T00:00:00Z&EndTime=2018-01-30T00:00:00Z&<公共请求参数>
```

正常返回示例

`JSON`格式

``` {#codeblock_g2d_epx_wgy}
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "ChannelCntDataPerInterval": [
        {
            "TimeStamp": "2018-01-29T00:00:00Z",
            "ActiveChannelCnt": 10
        }
    ]
}
```

## 特殊错误码 {#section_11q_2ae_yx4 .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|MissingParameter|ClientToken is mandatory for this action.|400|参数缺失。|

