# DescribeFaultDiagnosisUserList

调用DescribeFaultDiagnosisUserList获取异常诊断的用户明细列表。

**说明：** 支持查询最近48小时且查询范围不超过24小时的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=vdc&api=DescribeFaultDiagnosisUserList&type=ROA&version=2020-12-14)

## 请求头

该接口使用公共请求头，无特殊请求头。请参见公共请求参数文档。

## 请求语法

```
POST /api/diagnosis/describeFaultDiagnosisUserList HTTP/1.1
```

## 请求参数

|名称|类型|位置|是否必选|示例值|描述|
|--|--|--|----|---|--|
|AppId|String|Query|是|0rbd\*\*\*\*|App ID。 |
|StartTs|Long|Query|是|1615806196|查询的开始时间，使用UNIX时间戳表示，单位：秒。 |
|EndTs|Long|Query|是|1615892596|查询的结束时间，使用UNIX时间戳表示，单位：秒。 |
|ChannelId|String|Query|否|311|频道ID。 |
|UserId|String|Query|否|140c1f12\*\*\*\*|用户ID。 |
|FaultTypes|String|Query|否|JOIN\_SLOW,AUDIO\_STUCK|过滤的异常类型，多个用英文逗号（,）分隔。取值：

 -   **JOIN\_SLOW**：进频道慢。
-   **AUDIO\_STUCK**：音频卡顿。
-   **VIDEO\_STUCK**：视频卡顿。
-   **VIDEO\_VAGUE**：视频模糊。
-   **HIGH\_DELAY**：通话延迟高。
-   **FIRST\_FRAME\_SLOW**：接收首屏慢。

 关于异常类型详情，请参见[异常类型说明](~~217966~~)。 |
|PageNo|Integer|Query|是|1|页码。 |
|PageSize|Integer|Query|是|10|每页数量。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|UserList|Array of UserList| |异常用户的明细列表。 |
|ChannelId|String|904|频道ID。 |
|UserId|String|140c1f12\*\*\*\*|用户ID。 |
|CreatedTs|Long|1620788012|第一次加入通话的时间，使用UNIX时间戳表示，单位：秒。 |
|DestroyedTs|Long|1620788861|最后一次离开通话的时间，使用UNIX时间戳表示，单位：秒。 |
|ChannelCreatedTs|Long|1620787721|创建通信的时间戳，使用UNIX时间戳表示，单位：秒。 |
|FaultList|Array of FaultData| |异常列表。 |
|FaultType|String|FIRST\_FRAME\_SLOW|异常类型。 |
|PageNo|Integer|1|页码。 |
|PageSize|Integer|10|每页数量。 |
|TotalCnt|Integer|187|总数量。 |
|RequestId|String|99C8FAD2-F96B-4A24-B2E8-3EC9529BAD2C|请求ID。 |

## 示例

请求示例

```
POST /api/diagnosis/describeFaultDiagnosisUserList?AppId=0rbd****&StartTs=1615806196&EndTs=1615892596&ChannelId=311&UserId=140c1f12****&FaultTypes=JOIN_SLOW,AUDIO_STUCK&PageNo=1&PageSize=10 HTTP/1.1
Host: vdc.cn-shenzhen.aliyuncs.com 
Date: GMT Date
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<DescribeFaultDiagnosisUserListResponse>
    <code>200</code>
    <data>
        <RequestId>99C8FAD2-F96B-4A24-B2E8-3EC9529BAD2C</RequestId>
        <TotalCnt>187</TotalCnt>
        <PageSize>10</PageSize>
        <PageNo>1</PageNo>
        <UserList>
            <DestroyedTs>1620788861</DestroyedTs>
            <FaultList>
                <FaultType>FIRST_FRAME_SLOW</FaultType>
            </FaultList>
            <UserId>140c1f12****</UserId>
            <ChannelCreatedTs>1620787721</ChannelCreatedTs>
            <CreatedTs>1620788012</CreatedTs>
            <ChannelId>311</ChannelId>
        </UserList>
        <UserList>
            <DestroyedTs>1620787669</DestroyedTs>
            <FaultList>
                <FaultType>HIGH_DELAY</FaultType>
            </FaultList>
            <FaultList>
                <FaultType>VIDEO_STUCK</FaultType>
            </FaultList>
            <UserId>c31b3236****</UserId>
            <ChannelCreatedTs>1620786579</ChannelCreatedTs>
            <CreatedTs>1620786588</CreatedTs>
            <ChannelId>905</ChannelId>
        </UserList>
    </data>
    <httpStatusCode>200</httpStatusCode>
    <requestId>99C8FAD2-F96B-4A24-B2E8-3EC9529BAD2C</requestId>
    <successResponse>true</successResponse>
</DescribeFaultDiagnosisUserListResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "code" : "200",
  "data" : {
    "RequestId" : "99C8FAD2-F96B-4A24-B2E8-3EC9529BAD2C",
    "TotalCnt" : 187,
    "PageSize" : 10,
    "PageNo" : 1,
    "UserList" : [ {
      "DestroyedTs" : 1620788861,
      "FaultList" : [ {
        "FaultType" : "FIRST_FRAME_SLOW"
      } ],
      "UserId" : "140c1f12****",
      "ChannelCreatedTs" : 1620787721,
      "CreatedTs" : 1620788012,
      "ChannelId" : "311"
    }, {
      "DestroyedTs" : 1620787669,
      "FaultList" : [ {
        "FaultType" : "HIGH_DELAY"
      }, {
        "FaultType" : "VIDEO_STUCK"
      } ],
      "UserId" : "c31b3236****",
      "ChannelCreatedTs" : 1620786579,
      "CreatedTs" : 1620786588,
      "ChannelId" : "905"
    } ]
  },
  "httpStatusCode" : "200",
  "requestId" : "99C8FAD2-F96B-4A24-B2E8-3EC9529BAD2C",
  "successResponse" : true
}
```

