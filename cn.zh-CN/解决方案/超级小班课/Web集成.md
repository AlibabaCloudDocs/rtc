# Web集成

您可以阅读本文，了解超级小班课Web端的集成操作。

## 前提条件

开发前的环境要求如下表所示，详情请参见：[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|浏览器|Chrome浏览器60版本及以上，Safari浏览器11版本及以上。浏览器开启视频设备和麦克风设备。|
|Node.js|支持Node.js 6.0版本及以上。具体操作，请参见[安装Node.js]()。|
|屏幕录制|Mac设备需要为浏览器打开屏幕录制权限。|

## Demo运行指引

1.  获取应用ID和AppKey。

    **说明：**

    应用ID和AppKey需要对应，不同的应用ID有不同的AppKey。

    在后续开发中会使用应用ID和AppKey，建议记录到本地文档中，妥善保存。

    1.  登录[RTC控制台](https://rtc.console.aliyun.com/?spm=a2c4g.11186623.2.19.555d7fa2SUK5LD#/overview)。

    2.  在左侧导航栏单击**应用管理**，进入应用管理页面。

    3.  获取应用ID和查询AppKey。

        -   应用ID：可在**应用ID/名称**列表下直接获取。
        -   AppKey：单击**查询AppKey**获取AppKey。
        如果您还未有应用，您可以单击**创建应用**创建。

        ![获取AppKey和应用ID](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2758773061/p176303.png)

2.  下载[Demo](https://github.com/aliyun/alibabacloud-AliRtcVideoLiveRoom-demo)源码并解压。

    解压成功之后如下图所示：

    ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0119850161/p214008.png)

    **说明：**

    -   AliRTC SDK通过npm集成。
    -   源码压缩文件内分为Web端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
3.  修改配置文件。

    打开web/src/core/data/config.js文件，修改AppID和AppKey。

    ![修改配置](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5430860161/p214010.png)

    **说明：**

    本Demo中在客户端代码配置AppID和AppKey的方式，很容易被反编译逆向破解，一旦AppID和AppKey泄露，攻击者就可以盗用您的阿里云流量，因此该配置方式仅适合用于本地Demo的运行和功能调试。

    正确的Token签发方式是将Token的计算代码集成到您的服务端，并提供面向App的接口，在需要Token时由您的App接口向业务服务器发起请求获取动态Token。具体操作，请参见[生成Token](/cn.zh-CN/常用功能/生成Token.md)。

4.  运行Demo。

    1.  打开终端，定位到Demo中的web文件夹下package.json文件所在目录。

    2.  输入以下命令安装项目依赖。

        ```
        npm install 
        ```

    3.  输入以下命令集成SDK 。

        ```
        npm install aliyun-webrtc-sdk -S
        ```

    4.  输入以下命令运行项目 。

        ```
        npm run serve
        ```

    5.  运行成功之后，你的浏览器默认会打开示例应用程序。

        如果没有打开，请在浏览器手动输入地址。

        -   Windows：https://localhost:888。
        -   Mac：https://localhost:1024。
        如果访问页面出现警告：**您的连接不是私密连接**。请单击**高级**，继续访问。

        ![警告页面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5430860161/p223921.png)

    6.  打包发布（若无需发布，请忽略此步骤）。

        打开终端，定位到Demo中的web文件夹所在目录。输入以下命令将压缩静态资源文件，可作为生产环境打包发布。

        ```
        npm run build
        ```

5.  开启超级小班课。

    1.  教师由Web端输入姓名进入教室，为助教和学生发送教室码。

    2.  助教由Web端输入姓名和教室码进入教室，选择需要管理的小组进行管理。

    3.  学生由Web端或移动端（Android或iOS）输入姓名和教室码进行教室听课学习，还可以进行连麦互动。


## Demo源码解析

1.  项目结构说明

    ```
    ├── dist                               #打包文件
    ├── public                             #静态资源
    ├── src                                #项目文件目录
    │   ├── assets                         #静态资源    
    │   ├── components                     #公共组件
    │   ├── core                           #js文件
    │   │   ├── data
    │   │   │   ├── config.js              #相关配置参数
    │   │   ├── util
    │   │   │   ├── utils.js               #一些公共方法
    │   │   ├── rtc-engine.js              #单例
    │   │   ├── rtc-clinet.js              #RTC实例文件
    │   ├── plugins
    │   ├── router                         #路由
    │   ├── views                          #页面
    │   │   ├── login                      
    │   │   │   ├── login.vue              #登录页面
    │   │   ├── student                   
    │   │   │   ├── student.vue            #学生页面
    │   │   ├── assistant                  
    │   │   │   ├── assistant.vue          #助教页面
    │   │   ├── teacher                  
    │   │   │   ├── teacher.vue            #教师页面
    │   ├── vuex
    │   ├── App.vue                        #根组件
    │   ├── main.js                        #入口文件
    ├── vue.config.js                      #vue配置文件
    ```

2.  功能实现流程

    -   检查浏览器是否支持

        ```
        RtcEngine.instance.isSupport().then(re => {}).catch(err=>{});
        ```

    -   获取设备信息

        ```
        RtcEngine.instance.getDevices().then(re => {})
        ```

    -   指定摄像头

        ```
        RtcEngine.instance.currentCamera(deviceId)
        ```

    -   指定麦克风

        ```
        RtcEngine.instance.currentAudioCapture(deviceId)
        ```

    -   开启预览

        ```
        /**
         * 预览
         * @parame {HtmlVideoElement} video 播放预览画面的video标签
         */
        RtcEngine.instance.startPreview(video).then(re=>{})
        ```

    -   停止预览

        ```
        RtcEngine.instance.stopPreview(video).then(re=>{})
        ```

    -   设置是否自动推流自动订阅

        需要在加入频道之前设置，此接口是针对频道设置的。

        ```
        /**
           * 设置是否自动推流和自动订阅 默认自动推流自动订阅
           * @param {*} channel 频道
           * @param { boolean } autoPub true表示自动推流
           * @param { boolean } autoSub true表示自动订阅
           */
        RtcEngine.instance.setAutoPublishSubscribe(channel, autoPub, autoSub)
        ```

    -   注册回调

        需要在加入频道之前设置，此接口是针对频道设置的。

        ```
        /**
           * 注册回调
           * @param {*} channel 频道
           * @param {*} callback 
           */
        RtcEngine.instance.registerCallBack(channel, callback)
        ```

    -   加入频道

        ```
        /**
           * 加入房间
           * @param {*} channel 频道
           * @param {*} userName 
           */
        RtcEngine.instance.login(channel, userName).then(re=>{})
        ```

    -   开始推流

        ```
        /**
           * 开始推流
           * @param {*} channel 频道
           */
        RtcEngine.instance.startPublish(channel).then(re=>{})
        ```

    -   停止推流

        ```
        /**
           * 停止推流
           * @param {*} channel 频道
           */
        RtcEngine.instance.stopPublish(channel).then(re=>{})
        ```

    -   设置是否停止发布本地音频

        ```
         /**
           * 设置是否停止发布本地音频
           * @param {*} channel  频道
           * @param {*} enable 
           */
        RtcEngine.instance.muteLocalMic(channel, enable)
        ```

    -   设置是否停止发布本地视频

        ```
         /**
           * 设置是否停止发布本地视频
           * @param {*} channel  频道
           * @param {*} enable 
           */
        RtcEngine.instance.muteLocalCamera(channel, enable)
        ```

    -   切换开启和停止屏幕流

        ```
        /**
           * 切换开启和停止屏幕流
           * @param {*} channel  频道
           * @param {*} enable 
           */
        RtcEngine.instance.switchPublishScreen(channel, enable)
        ```

    -   订阅音视频

        ```
        /**
           * 设置远端渲染 默认订阅音频 + 视频（小流）
           * @param {*} channel  频道
           * @param {*} userId 
           */
        RtcEngine.instance.subscribe(channel, userId).then(re=>{})
        ```

    -   取消订阅

        ```
        /**
           * 取消订阅
           * @param {*} channel  频道
           * @param {*} userId 
           */
        RtcEngine.instance.unSubScribe(channel, userId).then(re=>{})
        ```

    -   设置远端渲染

        ```
        /**
           * 设置远端渲染
           * @param {*} channel  频道
           * @param {*} userId 
           * @param {*} video 
           * @param {*} streamType 
           */
        RtcEngine.instance.setDisplayRemoteVideo(channel, userId, video, streamType)
        ```

    -   获取频道用户列表

        ```
          /**
           * 获取判断用户列表 频道
           * @param {*} channel 
           * @return { array | boolean }
           */
        RtcEngine.instance.getUserList(channel)
        ```

    -   获取用户信息

        ```
          /**
           * 获取判断用户列表
           * @param {*} channel 频道
           * @return { array | boolean }
           */
        RtcEngine.instance.getUserInfo(channel, userId)
        ```

    -   离开频道

        ```
         /**
           * 离开频道
           */
        RtcEngine.instance.logout().then(re=>{})
        ```


