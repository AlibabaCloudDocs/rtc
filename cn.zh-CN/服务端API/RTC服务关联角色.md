# RTC服务关联角色

本文为您介绍RTC服务关联角色（AliyunServiceRoleForRTC）的应用场景以及如何删除服务关联角色。

RTC服务关联角色（AliyunServiceRoleForRTC），是在特定情况下，为了完成RTC自身的某个功能，需要获取其他云服务的访问权限，而提供的RAM角色。更多信息，请参见[服务关联角色](https://help.aliyun.com/document_detail/160674.html)。

## RTC服务关联角色介绍

角色名称：AliyunServiceRoleForRTC

角色权限策略：AliyunServiceRolePolicyForRTC

权限说明：

```
{
      "Action": [
        "mns:PublishMessage",
        "mns:SendMessage",
        "live:DescribeLiveDomainDetail",
        "live:DescribeLiveUserDomains",
        "live:DescribeLiveDomainConfigs",
        "oss:GetObject",
        "oss:PutObject"
      ],
      "Resource": "*",
      "Effect": "Allow"
    }
```

## 应用场景

RTC服务关联角色应用场景如下所示。

-   RTC在不同组件之间传递数据时需要访问消息服务（MNS）的资源，通过服务关联角色功能获取访问权限。
-   RTC的旁路转推功能需要访问视频直播服务（ApsaraVideo Live）的资源，通过服务关联角色功能获取访问权限。
-   RTC的云端录制功能需要访问对象存储服务（OSS）的资源，通过服务关联角色功能获取访问权限。

## 删除服务关联角色

如果您需要删除服务关联角色（AliyunServiceRoleForRTC），可以通过以下两种方式。

-   您可以从控制台主动删除。关于主动删除服务关联角色，详情请参见[删除RAM角色](https://help.aliyun.com/document_detail/116250.html#task-188137)。
-   删除服务关联角色，具体操作，请参见[删除服务关联角色](https://help.aliyun.com/document_detail/160674.html#title-7ia-f5z-yst)

**说明：** 如果RTC录制模板存在，会导致删除服务关联角色（AliyunServiceRoleForRTC）失败。

