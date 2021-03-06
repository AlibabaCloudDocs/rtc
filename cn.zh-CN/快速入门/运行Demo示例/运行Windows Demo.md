---
keyword: Windows Demo
---

# 运行Windows Demo

通过阅读本文，您可以了解运行Windows Demo的方法。

您已从控制台获取鉴权信息，具体操作，请参见[接入工具](/cn.zh-CN/控制台指南/接入工具.md)。

**说明：** 从控制台获取的Token仅为开发测试使用，正式上线有被攻击风险。建议您自己搭建服务端生成Token，并使用HTTPS协议。搭建服务端请参见[服务端生成Token](/cn.zh-CN/基础功能/生成Token.md)。

## 环境要求

|类型|说明|
|--|--|
|终端设备|如果使用不自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。|
|系统版本|Windows XP（SP3）、Windows 7、Windows 8.X、Windows 10，不支持Windows XP（SP3）以下版本。|

## 操作步骤

1.  下载并解压SDK及示例代码，下载地址，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  复制SDK文件至示例代码中的MFC Demo目录下。

3.  打开Demo中的RTCSampleMainInterface.cpp文件并定位到第1107行代码，配置鉴权信息AuthInfo。

    ```
    authinfo.channel = CStringToAliString(m_sLoginInfo.s_strRoomID);
    authinfo.user_id = "a9e28****";
    authinfo.appid = "aoe****";
    authinfo.nonce = "AK-e5babe72e81a54fb9f580d4****";
    authinfo.token = "39cf7cde****";
    authinfo.gslb.AddString("https://rgslb.rtc.aliyuncs.com");
    authinfo.agent.AddString("");
    authinfo.timestamp = 1585363086;//过期时间戳，例如：1560588594代表过期时间为2019-06-15 16:49:54。
    ```

4.  运行Demo。

    1.  Demo运行成功进入首页，单击**设置**进入参数设置界面，服务地址可不填。

        ![Windows Demo 设置 ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0655588951/p56334.png)

        如果您想和Web端连接，请选中**兼容H5模式**。推送视频流请选中**视频流**，推送音频流请选中**音频流**。

    2.  关闭**设置**页面，在首页输入相应**频道号**和**用户名**，单击**创建/加入房间**。

        ![Windows Demo输入](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1655588951/p49615.png)

    3.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户，可开始实时音视频通话。

        ![Windows Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1655588951/p49616.png)

        您也可以选中**共享屏幕**把自己的屏幕分享给远端用户。


