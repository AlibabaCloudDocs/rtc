# DescribeMPULayoutList

调用DescribeMPULayoutList获取旁路直播布局列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=rtc&api=DescribeMPULayoutList&type=RPC&version=2018-01-11)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeMPULayoutList|操作接口名，系统规定参数，取值：**DescribeMPULayoutList**。 |
|AppId|String|是|yourAppId|应用ID，仅支持传单个ID。

 可通过控制台创建和查询。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LayoutIds|List|\[2,4,6\]|布局ID组。 |
|RequestId|String|760bad53276431c499e30dc36f6b26be|请求ID。 |

## 示例

请求示例

```
https://rtc.aliyuncs.com/?Action=DescribeMPULayoutList
&AppId=yourAppId
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeMPULayoutListResponse>
  <RequestId>760bad53276431c499e30dc36f6b26be</RequestId>
  <LayoutIds>
        <LayoutId>2</LayoutId>
        <LayoutId>4</LayoutId>
        <LayoutId>6</LayoutId>
  </LayoutIds>
</DescribeMPULayoutListResponse>
```

`JSON` 格式

```
{
    "RequestId": "760bad53276431c499e30dc36f6b26be", 
    "LayoutIds":{
        "LayoutId":[2,4,6]
        }
}
```

