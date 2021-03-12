---
keyword: Windows Demo
---

# 运行Windows Demo

通过本文，您可以了解快速运行Windows Demo的操作方法，实现加入频道和远端用户进行音视频通信。

在执行Demo步骤之前，您需要从控制台获取鉴权信息，具体操作请参见[生成Token](/cn.zh-CN/控制台指南/接入工具.md)。

您需要下载示例代码，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

1.  下载MFC Demo文件夹和最新版本SDK压缩包。

2.  将SDK解压到MFC Demo文件夹中。

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

    ![配置authinfo界面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0655588951/p98806.png)

4.  运行Demo。

    1.  Demo运行成功进入首页，单击设置进入参数设置界面，服务地址您可以不填。

        **说明：** Windows端Demo如果使用不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。系统支持Windows XP（SP3）、Windows 7、Windows 8.X、Windows 10，不支持Windows XP（SP3）以下版本。

        ![Windows Demo 设置 ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0655588951/p56334.png)

        如果您想和Web端连接，请选中**兼容H5模式**。推送视频流请选中**视频流**，推送音频流请选中**音频流**。

    2.  关闭设置页面，在首页输入相应频道号和用户名，单击**创建/加入房间**按钮，进入下一页面。

        ![Windows Demo输入](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1655588951/p49615.png)

    3.  进入频道页面后，可以看到本地已经开启的预览视图。单击**开始**加入频道，如果该频道中有其他用户，即可开始实时音视频通话。

        ![Windows Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1655588951/p49616.png)

        您也可以勾选**屏幕共享**把自己的屏幕分享给远端用户。


