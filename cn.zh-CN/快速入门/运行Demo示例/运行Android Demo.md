---
keyword: Android Demo
---

# 运行Android Demo

通过阅读本文，您可以了解运行Android Demo的方法。

您已从控制台获取鉴权信息，具体操作，请参见[接入工具](/cn.zh-CN/控制台指南/接入工具.md)。

**说明：** 从控制台获取的Token仅为开发测试使用，正式上线有被攻击风险。建议您自己搭建服务端生成Token，并使用HTTPS协议。搭建服务端请参见[服务端生成Token](/cn.zh-CN/基础功能/生成Token.md)。

## 环境要求

确保Demo运行在Android 4.4或以上版本的实体设备上。

## 操作步骤

1.  下载并解压SDK及示例代码，下载地址，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  在示例代码的libs文件夹中添加RTC SDK，如果没有libs文件夹，需要手动创建。

    ![lib目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5555588951/p110332.png)

3.  打开AliRtcChatActivity.java文件，配置鉴权信息参数。

    ```
            private void joinChannel() {
            if (mAliRtcEngine == null) {
                return;
            }
            AliRtcAuthInfo userInfo = new AliRtcAuthInfo() ;
            userInfo.setAppid("zwdm****");
            userInfo.setNonce("AK-d8847d08-c8b3-4800-84e3-7f6c4d65f96d");
            userInfo.setGslb(new String[]{"https://rgslb.rtc.aliyuncs.com"});
            userInfo.setTimestamp(1589379613);
            userInfo.setToken("e48d39484c91a26****");
            userInfo.setConferenceId("1234");
            userInfo.setUserId("testId");
            /*
             *设置自动发布和订阅，只能在加入频道之前设置。
             *autoPub：是否自动发布，取值true|false。
             *autoSub：是否自动订阅，取值true|false。
             */
            mAliRtcEngine.setAutoPublishSubscribe(true, true);
            // 加入频道，需要填写鉴权信息和用户名。
            mAliRtcEngine.joinChannel(userInfo,"用户名");
    
        }
    ```

4.  运行Demo。

    Demo运行成功后进入音视频通话界面，您可以看到本地已经开启的预览视图，然后会自动加入频道，等待远端用户的加入。

    ![Android Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5555588951/p49548.png)

    如果该频道中有其他用户即可开始实时音视频通话。

    ![运行成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6555588951/p49549.png)


