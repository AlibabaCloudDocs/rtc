# DescribeApps {#reference2140 .reference}

调用DescribeApps查询应用列表。

## 请求参数 { .section}

|参数|类型|是否必选|描述|
|--|--|----|--|
|Action|String|是|操作接口名，系统规定参数，取值：DescribeApps。|
|AppId|String|否|应用ID，通过控制台开通创建，长度最大8个字节，不填则返回该用户下所有应用信息。|
|Status|Integer|否|状态： -   1：可用。
-   2：停用。
-   3：欠费停用。

 |
|Order|String|否|不填则默认desc取最近记录： -   递增：asc。
-   递减：desc。

 |
|PageNum|Integer|否|不填则默认1页，取值必须大于0。|
|PageSize|Integer|否|不填则默认为10， 取值必须大于0|

## 返回参数 { .section}

|参数|类型|描述|
|--|--|--|
|RequestId|String|该条任务请求ID。|
|AppList|App\[\]|信息列表。|
|TotalNum|Integer|返回结果数。|
|TotalPage|Integer|返回分页数。|

App

|参数|类型|描述|
|--|--|--|
|AppId|String|应用ID。|
|AppName|String|应用名称。|
|CreateTime|String|创建时间。|
|Status|Integer|状态： -   1：可用。
-   2：停用。
-   3：欠费停用。

 |
|ServiceAreas|String\[\]|示例：\[US, CN\]。|
|AppType|String| -   conference：会议。
-   universal：通用型。

 |
|BillType|String|按时长计费：payByDuration。|

## 示例 { .section}

请求示例

```
https://rtc.aliyuncs.com?Action=DescribeApps&PageNum=1&PageSize=2&<公共请求参数>
```

正常返回示例

`JSON`格式

```language-json
{
    "RequestId": "6159ba01-6687-4fb2-a831-f0cd8d188648",
    "TotalNum": 2,
    "TotalPage": 1,
    "AppList": [
        {
            "Status": 1,
            "AppName": "coco-conf",
            "CreateTime": "2017-08-30 10:47:25.0",
            "AppId": "af2ace82-dc55-40b1-9fa3-688787214b1d",
            "ServiceAreas": "[\"CN\"]",
            "AppType": "universal",
            "BillType": "payByDuration"
        }
    ]
}
```

## 特殊错误码 {#section_fmp_nlk_gif .section}

|错误代码|描述|Http 状态码| |
|----|--|--------|--|
|InvalidStatus.Malformed|The specified parameter Status is not valid.|400|参数Status无效。|
|InternalError|The request processing has failed due to some unknown error.|500|内部错误。|

