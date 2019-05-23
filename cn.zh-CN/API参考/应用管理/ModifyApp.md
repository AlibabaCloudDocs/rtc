# ModifyApp {#reference1053 .reference}

调用ModifyApp修改应用信息，只修改参数中显式指定的属性，没有指定的属性将不会发生改变。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：ModifyApp。|
|AppId|String|是|应用ID，通过控制台开通创建。|
|AppName|String|否|应用名称。|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求ID。|
|AppId|String|应用ID。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=ModifyApp&AppName=coco-conf&<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "AppId": "a2b8e671-2fe5-4642-a2ec-bf93880exxxx"
}
```

## 特殊错误码 {#section_cl7_y2w_15w .section}

|错误代码|描述|Http 状态码|语义|
|----|--|--------|--|
|InvalidAppId.NotFound|The specified AppIddoes not exist.|404|指定的AppId不存在。|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误，请您稍后重试。|

