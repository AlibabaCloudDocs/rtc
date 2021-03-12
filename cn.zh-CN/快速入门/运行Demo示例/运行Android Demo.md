---
keyword: Android Demo
---

# 运行Android Demo

您可以阅读本文，了解快速运行Android Demo的操作方法，实现加入频道和远端用户进行音视频通信。

在执行Demo步骤之前，您需要从控制台获取鉴权信息，具体操作请参见[生成Token](/cn.zh-CN/控制台指南/接入工具.md)。

您需要下载示例代码，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

1.  在该目录下的libs文件夹中添加RTC SDK，如果没有libs文件夹，需要手动创建。

    ![lib目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5555588951/p110332.png)

2.  打开AliRtcChatActivity.java文件，配置鉴权信息参数。

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

3.  运行Demo。Demo运行成功后进入音视频通话界面，您可以看到本地已经开启的预览视图，然后会自动加入频道，等待远端用户的加入。

    **说明：** Android端Demo必须在Android 4.4及以上系统的真机上运行。

    ![Android Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5555588951/p49548.png)

    如果该频道中有其他用户即可开始实时音视频通话。

    ![运行成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6555588951/p49549.png)


