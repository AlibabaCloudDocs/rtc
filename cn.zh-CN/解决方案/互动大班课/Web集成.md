# Web集成

通过阅读本文，您可以了解到Web端互动大班课的集成方法。

## 环境要求

Web端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   您已经注册阿里云账号，并完成实名认证，更多信息，请参见[t12832.md\#]()。
-   您已经开通音视频通信服务，更多信息，请参见[音视频通信服务开通](/cn.zh-CN/快速入门/开通服务.md)。
-   环境中已安装Node.js 6.0或以上版本。具体操作，请参见[安装Node.js]()。
-   如果设备为Mac，需要为浏览器打开屏幕录制权限。

## 操作步骤

1.  获取AppID和AppKey。此处建议记录一下AppID和AppKey，方便后续操作中使用。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  在**AppID/名称**列获取AppID。

    4.  单击**操作**列的**查询AppKey**，获取AppKey。

    **说明：** 如果应用列表中没有您需要的应用，可以单击**创建应用**，创建新的应用。更多信息，请参见[应用管理](/cn.zh-CN/控制台指南/管理应用.md)。

2.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/Demo/Demo体验.md)。

    **说明：**

    -   Demo源码中已经集成AliRTC WEB SDK，可通过npm命令集成。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
3.  配置Demo工程。

    根据[步骤1](#step_adr_9nh_tt0)中获取的AppID和AppKey修改web/src/core/data/config.js文件中`appID`和`appKey`的值。

    ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4877031161/p230778.png)

    **说明：** 此处配置的AppID和AppKey很容易被反编译破解，如果被破解，攻击者可以盗用您的阿里云流量，因此AppID和AppKey仅适用于Demo演示及功能调试。在正式环境中您可以将Token计算代码集成到服务器中，并提供面向App的接口，在需要Token时由App向业务服务器发起请求获取动态Token。更多信息，请参见[生成Token](/cn.zh-CN/常用功能/生成Token.md)。

4.  运行Demo。

    1.  打开后台终端并进入到web目录下。

    2.  安装项目依赖。

        npm install

    3.  运行Demo。

        npm run serve

        运行成功后，浏览器会默认打开Demo应用示例。如果没有自动打开，请在浏览器中访问https://localhost:1024。

        ![003](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4540311161/p227885.png)

    4.  压缩静态资源文件，打包发布。

        npm run build


## Demo源码解析

-   目录结构说明

    ![002](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6530311161/p227872.png)

-   主要功能说明
    -   检查浏览器是否支持。

        ```
        RtcEngine.instance.isSupport().then(re => {}).catch(err=>{});
        ```

    -   获取设备信息。

        ```
        RtcEngine.instance.getDevices().then(re => {})
        ```

    -   指定摄像头。

        ```
        RtcEngine.instance.currentCamera(deviceId)
        ```

    -   指定麦克风。

        ```
        RtcEngine.instance.currentAudioCapture(deviceId)
        ```

    -   开启预览。

        ```
        /**
         * 预览
         * @parame {HtmlVideoElement} video 播放预览画面的video标签
         */
        RtcEngine.instance.startPreview(video).then(re=>{})
        ```

    -   停止预览。

        ```
        RtcEngine.instance.stopPreview(video).then(re=>{})
        ```

    -   设置是否自动推流、自动订阅，需要在加入频道之前设置，此接口针对频道设置。

        ```
        /**
           * 设置是否自动推流、自动订阅，默认自动推流、自动订阅
           * @param { boolean } autoPub true表示自动推流
           * @param { boolean } autoSub true表示自动订阅
           */
        RtcEngine.instance.setAutoPublishSubscribe(autoPub, autoSub)
        ```

    -   注册回调，需要在加入频道之前设置，此接口针对频道设置。

        ```
        /**
           * 注册回调
           * @param {*} channel 频道
           * @param {*} callback 
           */
        RtcEngine.instance.registerCallBack(channel, callback)
        ```

    -   加入频道。

        ```
        /**
           * 加入房间
           * @param {*} channel 频道
           * @param {*} userName 
           */
        RtcEngine.instance.login(channel, userName).then(re=>{})
        ```

    -   开始推流。

        ```
        /**
          * 上麦
          */
        RtcEngine.instance.enterSeat(channel)
        ```

    -   停止推流。

        ```
        /**
          * 下麦
          */
        RtcEngine.instance.leavelSeat()
        ```

    -   设置是否停止发布本地音频。

        ```
        /**
           * 设置是否停止发布本地音频
           * @param {*} enable 
           */
        RtcEngine.instance.muteLocalMic(enable)
        ```

    -   设置是否停止发布本地视频。

        ```
        /**
           * 设置是否停止发布本地视频
           * @param {*} enable 
           */
        RtcEngine.instance.muteLocalCamera(enable)
        ```

    -   设置发布屏幕流。

        ```
        /**
           * 开启屏幕流
           * @param {*} enable 
           */
        RtcEngine.instance.startPublishScreen()
        ```

    -   设置停止发布屏幕流。

        ```
        /**
           * 停止屏幕流
           * @param {*} enable 
           */
        RtcEngine.instance.stopPublishScreen()
        ```

    -   订阅音视频。

        ```
        /**
           * 设置远端渲染，默认订阅音频和视频（小流）
           * @param {*} userId 
           */
        RtcEngine.instance.subscribe(userId).then(re=>{})
        ```

    -   订阅大流。

        ```
        /**
           * 设置远端渲染，默认订阅音频和视频（大流）
           * @param {*} userId 
           */
        RtcEngine.instance.subscribeLarge(userId).then(re=>{})
        ```

    -   设置远端渲染。

        ```
        /**
           * 设置远端渲染
           * @param {*} userId 
           * @param {*} video 
           * @param {*} streamType 
           */
        RtcEngine.instance.setDisplayRemoteVideo(userId, video, streamType)
        ```

    -   获取频道用户列表。

        ```
        /**
           * 获取频道用户列表 
           * @return { array | boolean }
           */
        RtcEngine.instance.getRoomUserList()
        ```

    -   获取用户信息。

        ```
        /**
           * 获取频道用户信息
           * @param {*} channel 频道
           * @return { array | boolean }
           */
        RtcEngine.instance.getUserInfo(channel, userId)
        ```

    -   离开频道。

        ```
        /**
           * 离开频道
           */
        RtcEngine.instance.logout().then(re=>{})
        ```


