# 集成Android端

您可以阅读本文，了解1对1语音聊天Android端的集成操作。

## 前提条件

开发前的环境要求如下表所示，详情请参见：[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|系统版本|支持Android 4.1及以上。|
|API版本|不低于16。|
|CPU架构|支持真机架构armeabi、armeabi-v7a、arm64-v8a （不支持模拟器x86架构）。|
|Android Studio版本支持|支持Android Studio3.0及以上。下载[Android Studio](https://developer.android.google.cn/studio/)。|

您需要先集成服务端，具体操作，请参见[集成服务端](/cn.zh-CN/解决方案/1对1语音聊天/集成服务端.md)。

## Demo运行指引

**说明：** 您在集成Android端时，如果遇到问题，或者Demo体验过程中出现无法创建房间或通话等问题，请参见[Android端运行常见问题]()。

1.  下载[Demo](https://github.com/aliyun/AliRTC-UserCase-VoiceCallSolution_1To1/tree/master)并解压。

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180033.png)

    **说明：**

    -   Demo源码中已经集成AliRTC SDK（版本：1.17）。SDK集成方式通过Maven集成。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
2.  在Android Studio打开Android端工程。

    打开**Android Studio**，单击**Open an existing Android Studio project**并选择AliRTC-UserCase-VoiceCallSolution\_1To1-master目录下的android文件夹。

    ![导入源码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180032.png)

3.  修改配置文件。

    1.  打开Android Studio，在Demo中找到android/AlivcVoiceCall/AlivcVoiceCall\_demo/src/main/java/com/aliyun/rtc/voicecall/constant/Constant.java文件。

        ![Constant](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3612208061/p176748.png)

    2.  修改文件中的`BASE_URL`变量，如：`http://<服务器IP> :端口:8080/1v1-audio`，部署到正式环境上建议绑定域名并使用：`http://<域名>/1v1-audio`。

        示例

        假设本地IP为192.0.2.1，那么`BASE_URL="http://192.0.2.1:8080/1v1-audio"`。本地IP查询，请参见[查询IP地址]()。

        ![IP地址](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9566605061/p180031.png)

        **说明：**

        -   不要使用127.0.0.1的IP。
        -   手机和搭建服务器的电脑处在一个局域网中。
    3.  使用手机端和电脑端浏览器验证。

        输入正确的URL（`BASE_URL`变量）地址，即可在浏览器中打开并看到：`Hello RTC!`。电脑端浏览器正确访问说明IP和端口号无误，手机端浏览器正确访问说明目前手机可以正常访问到服务器IP。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8721083061/p176766.png)

4.  选择一台已连接的真机设备。（暂不支持模拟器运行）

    将一台Android真机设备（需在系统设置中开启开发者模式和USB调试功能）使用数据线与电脑连接，在手机端同意调试后在Android Studio中选择接入的真机设备。

5.  单击**build and run**按钮编译，Android真机会安装并启动1对1语音聊天App。

    ![bulid and run](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3612208061/p201076.png)

6.  进行1对1语音聊天。

    1.  将2台真机移动端设备（Android或iOS）装上Demo App。

    2.  将2台设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台真机上输入任意房间号，创建房间并等待对方加入。

    4.  在第二台真机上输入相同房间号加入房间并进行通话。


## Demo源码解析

1.  项目结构说明。

    项目业务代码都封装在AlivcVoiceCall库里面，可以通过引用本地库的形式引用到项目中使用。

    项目名解释，如下所示：

    -   AlivcVoiceCall：功能实现库。
    -   AliyunVideoCommon：公共库。
    -   app：Demo启动入口。
    -   thirdparty-lib：第三方库的引用。
    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2939174951/p126897.png)

    UI中存放App页面，constant中存放常量数据，view中存放自定义view，network中存放网络请求。

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2939174951/p126900.png)

2.  功能实现流程。

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


