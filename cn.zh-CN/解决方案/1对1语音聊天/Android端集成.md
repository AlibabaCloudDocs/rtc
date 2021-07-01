# Android端集成

通过阅读本文，您可以了解1对1语音聊天Android端的集成操作。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   服务端已集成并开启。具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/1对1语音聊天/服务端集成.md)。
-   环境中已安装Android Studio 3.0或以上版本。更多信息，请参见[Android Studio](https://developer.android.google.cn/studio/)。

## 操作步骤

1.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中已通过Maven方式集成AliRTC Android SDK（1.17版本）。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
2.  配置Demo工程。

    1.  打开Android Studio，单击**Open an Existing Project**，选择android文件夹。

    2.  打开android/AlivcVoiceCall/AlivcVoiceCall\_demo/src/main/java/com/aliyun/rtc/voicecall/constant/Constant.java文件。

        ![Constant](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3612208061/p176748.png)

    3.  修改文件中的`BASE_URL`值。

        例如本地服务端IP地址为192.0.2.1，则`BASE_URL`的值为`http://192.0.2.1:8080/1v1-audio`，即`BASE_URL="http://192.0.2.1:8080/1v1-audio"`。本地服务端IP地址查询，请参见[查询IP地址]()。

        ![IP地址](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180031.png)

        **说明：**

        -   服务端IP地址禁止使用127.0.0.1。
        -   移动端和服务端处于同一局域网中。
        -   如果需要部署到正式环境，请绑定域名即`BASE_URL="http://<域名>/1v1-audio"`。
    4.  验证移动端和服务端。

        分别在移动端和服务端浏览器中访问`BASE_URL`地址，如果显示如下图所示，表示移动端访问服务端正常。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8721083061/p176766.png)

3.  运行Demo。

    将Android设备与电脑有线连接，并在Android Studio中选择相对应的设备（暂不支持模拟器运行），单击![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2352221161/p228915.png)，编译并运行。如果编译过程中出现问题或无法正常通话，请参见[Android端运行常见问题]()。

    ![bulid and run](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3612208061/p201076.png)

    **说明：** 将Android设备和电脑有线连接时，需要在Android设备的设置中开启开发者模式和USB调试模式，同时在Android设备上选择同意调试。

4.  进行1对1语音聊天。

    1.  将两台移动端设备安装Demo App。

    2.  将两台设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间号，创建房间并等待对方加入。

    4.  在第二台设备上输入相同房间号加入房间并进行通话。


## Demo目录结构说明

项目结构如下所示：

|文件名|说明|
|---|--|
|AlivcVoiceCall|1队1语音聊天功能实现库。更多信息，请参见[AlivcVoiceCall组件库目录说明](#p_1lr_ya4_iye)。|
|AliyunVideoCommon|公共组建库。|
|app|程序入口。|
|thirdparty-lib|第三方库的引用。|

AlivcVoiceCall组件库目录说明，如下所示：

|文件名|说明|
|---|--|
|constant|常量数据管理类。|
|network|网络请求。|
|ui|应用界面。|
|view|自定义view。|

## 主要功能说明

-   创建并加入房间。

    **说明：** AliRtcEngieEventListener回调在子线程中，如果您想操作UI界面需要切换到主线程。

    ```
          //创建AliRtcEngin实例。
          mEngine = AliRtcEngine.getInstance(getApplicationContext());
          //设置AliRtcAuthInfo用户信息，通过Server Api获取到用户信息和RTC服务器的Token信息，拿到信息后
          //设置给AliRtcAuthInfo就可以调用joinChannel加入频道进行通话。
          AliRtcAuthInfo userInfo = “从server端获取”；
          //调用joinChannel后在AliRtcEngieEventListener.onJoinChannelResult(int i)接受回调信息。
          if (i != 0) {
              //加入房间失败。
          } else {
              //加入房间成功。
          }
    ```

-   用户推流。

    当用户加入房间成功时可以调用推流方法来发布自己的音频信息让对方订阅， 也可以在加入房间之前调用`mEngine.setAutoPublish(true, true);`来实现主动推流和订阅。

    ```
    //true表示允许发布音频流，false表示不允许。
    mEngine.configLocalAudioPublish(true);
    mEngine.publish();
    ```

-   播放伴奏。

    startAudioAccompany方法只能播放一首歌，不支持多首同时播放 playAudioEffect可以播放之前预加载的音效。两个方法可以同时调用，可以一边推送播放背景音效，一个本地试听。

    ```
    //播放当前音效并推送。loopCycles=-1时代表循环播放。
    mEngine.startAudioAccompany(mSelectedBgmData.first.getPath(), false, false, -1);
    int i = mEngine.playAudioEffect(currBgm, file.getPath(), -1, false);
    ```

-   暂停伴奏。

    ```
    mEngine.pauseAudioAccompany();
    mEngine.pauseAudioEffect(soundId);
    ```

-   停止伴奏。

    ```
    mEngine.pauseAudioAccompany();
    mEngine.stopAudioEffect(currBgm);
    ```

-   恢复播放伴奏。

    ```
    mEngine.resumeAudioAccompany();
    mEngine.resumeAudioEffect(currBgm);
    ```

-   静音模式（停止发布本地音频流）。

    ```
    mEngine.muteLocalMic(false);
    ```

-   取消静音模式（发布本地音频流）。

    ```
    mEngine.muteLocalMic(true);
    ```

-   扬声器模式。

    ```
    mEngine.enableSpeakerphone(true);
    ```

-   取消扬声器模式。

    ```
    mEngine.enableSpeakerphone(false);
    ```

-   离开房间。

    ```
    mEngine.leaveChannel();
    ```


