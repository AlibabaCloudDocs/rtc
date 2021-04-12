---
keyword: Web Demo
---

# 运行Web Demo

通过阅读本文，您可以了解运行Web Demo的方法。

您已从控制台获取鉴权信息，具体操作，请参见[接入工具](/cn.zh-CN/控制台指南/接入工具.md)。

**说明：** 从控制台获取的Token仅为开发测试使用，正式上线有被攻击风险。建议您自己搭建服务端生成Token，并使用HTTPS协议。搭建服务端请参见[服务端生成Token](/cn.zh-CN/基础功能/生成Token.md)。

1.  下载并解压SDK及示例代码，下载地址，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  复制SDK文件至示例代码中的index.html同级目录下。

3.  打开并配置Demo中的index.html。

    1.  添加SDK的引用。

        ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4277128161/p262367.png)

        **说明：** 此处SDK文件名称仅供参考，具体名称请以实际为准。

    2.  配置AppId和AppKey。

        ![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4277128161/p262366.png)

4.  运行Demo。

    1.  输入房间号，单击**进入房间**。

        ![Demo运行成功进入房间](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2655588951/p70514.png)

    2.  进入房间后，已经默认开启本地预览并开始推送视频流（摄像头大流和音频）。您可以开启或关闭本地预览，也可以打开或关闭推流。

        房间显示用户名、房间号、推流状态。如果在当前房间内有其他成员，左侧会显示其用户名。

        ![本地预览](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2529688951/p62940.png)

        -   如果您想更改推流状态，您可以直接对推流选项进行热切换，也可以先单击**停止推流**，然后选择**推视频流**或**推共享流**。

            ![切换推流](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2655588951/p93408.png)

        -   如果您想和其他房间成员进行音视频通信，您可以将鼠标移动到左侧该成员用户名上，当出现**共享流 订阅**或**视频流 订阅**时，进行选择操作。

            **说明：** Demo中仅可订阅视频流和共享流，音频流单独订阅您可以自行开发实现，接口说明请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)。

            ![视频流订阅](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2655588951/p70521.png)

            订阅后的用户界面显示在房间右侧，互相订阅后即可开始实时音视频通信。


