# RemoveTerminals {#reference_264108 .reference}

调用RemoveTerminals删除指定终端

## 请求参数 {#section_m95_rgh_x6c .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：RemoveTerminals。|
|AppId|String|是|应用ID，通过控制台开通创建。|
|ChannelId|String|是|频道Id，用户加入的频道。|
|TerminalIds|\[\]String|是|终端ID列表。|

## 返回参数 {#section_8wp_mw9_0lx .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求Id。|

Terminals

|参数|类型|描述|
|--|--|--|
|Id|String|终端ID。|
|Code|Int|状态码。|
|Message|String|删除终端操作结果。|

## 示例 {#section_0z0_imn_9n2 .section}

请求示例

``` {#codeblock_i9t_zmp_up2}
https://rtc.aliyuncs.com?Action=RemoveTerminals&ChannelId=xxxx&TerminalIds=xxx&AppId=xxxx&<公共请求参数>
```

正常返回示例

`JSON`格式

``` {#codeblock_q7s_vvg_326}
{
   "RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
   "Terminals":[
      {
         "Id":"181131",
         "Code":0,
         "Message":"Success"
      },
      {
         "Id":"181131",
         "Code":0,
         "Message":"Success"
      }
   ]
}
```

## 特殊错误码 {#section_iie_8xu_g6o .section}

|错误ID|错误代码|描述|Http 状态码|语义|
|----|----|--|--------|--|
|0x02030901|MissingParameter|AppIdis mandatory for this action.|400|AppId缺失。|
|0x02030902|MissingParameter|ChannelIdis mandatory for this action.|400|ChannelId缺失。|
|0x02030903|MissingParameter|TerminalIdsis mandatory for this action.|400|TerminalIds缺失。|
|0x02030904|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

