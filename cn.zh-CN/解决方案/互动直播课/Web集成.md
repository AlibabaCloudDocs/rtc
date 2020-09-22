# Web集成

您可以阅读本文，了解Web端互动直播课的集成操作。

## Demo运行指引

1.  前提条件

    开发前的环境要求如下表所示，详情请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

    |支持平台|浏览器|浏览器版本|备注|
    |----|---|-----|--|
    |iOS|Safari|不低于11.1.2|    -   muteLocalMic、muteLocalCamera接口在iOS Safari浏览器存在兼容问题，无法使用。
    -   建议移动端不要使用WebSDK进行推流，请选择native端。
    -   纯订阅模式媒体文件播放失败，请参见[解决方案](/cn.zh-CN/常见问题/H5纯订阅模式媒体文件播放失败问题.md)。 |
    |Android|Chrome|不低于63|需要手机支持H264视频编码标准。|
    |Mac|Chrome|不低于60|—|
    |Mac|Safari|不低于11|—|
    |Windows|Chrome|不低于60|—|

2.  获取Demo源码

    如果您需要互动直播课开源示例项目，请添加钉钉群获取：

    ![顶顶群码](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0460749951/p135857.png)

3.  运行Demo

    1.  解压步骤2中下载的源码包，找到并打开src/core/data/config.js文件，设置config.js文件中的相关参数（baseUrl：跑通Server后的Server地址）。

        ![baseUrl](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9212129951/p129330.png)

        使用Server地址请注意：

        -   Server地址需要`https`地址。
        -   如果服务端地址与页面地址不同，或端口不同，会有跨域问题，推荐使用在服务端增加允许跨域请求头的方式解决。如果在本地运行，可以在**webpack**前端模块打包器中进行配置代理。在vue.config.js文件中添加如下代码：

            ```
              devServer: {
                proxy: {
                  '/api': {
                    target: '<url>',
                    ws: true,
                    changeOrigin: true
                  },
                  '/foo': {
                    target: '<other_url>'
                  }
                }
              }
            ```

    2.  在Terminal中，在您的项目根目录输入install命令以安装项目依赖。

        ```
        npm install
        ```

    3.  输入run serve命令以启动Web程序。

        ```
        npm run serve
        ```

    4.  输入npm run build会压缩静态资源文件，可作为生产环境打包发布。

        ```
        npm run build
        ```

    5.  你的浏览器默认会打开示例应用程序。

        **说明：** 如果没有自动打开，请在浏览器地址栏手动输入URL：https://localhost:888。

        Demo 运行界面如图所示：

        ![运行界面](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9212129951/p129331.png)


## 快速跑通Demo

在运行Demo前，先跑通server端的代码，然后将server地址粘贴到src/core/data/config.js文件中的baseUrl变量。如：https://<域名\>/interactive-live-class。

## 功能实现流程

1.  项目结构说明

    ```
    ├── dist                               #打包文件
    ├── publice                            #静态资源
    ├── src                                #项目文件目录
    │   ├── assets                         #静态资源    
    │   ├── components                     #公共组件
    │   ├── core                           #js文件
    │   │   ├── data
    │   │   │   ├── config.js              #相关参数
    │   │   ├── http
    │   │   │   ├── http.js                #接口请求相关
    │   │   ├── util
    │   │   │   ├── sutils.js              #一些公共方法
    │   │   ├── aliplayer-client.js        #播放器实例文件
    │   │   ├── rtc-clinet.js              #RTC实例文件
    │   ├── plugins
    │   ├── router                         #路由
    │   ├── views                          #页面
    │   │   ├── login                      #登录页
    │   │   ├── student                    #学生页面
    │   │   │   ├── student.vue            #学生页面
    │   │   │   ├── studentOnly.vue        #学生分享页面
    │   │   ├── teacher                    #教师页面
    │   ├── vuex
    │   ├── App.vue                        #根组件
    │   ├── main.js                        #入口文件
    ├── vue.config.js                      #vue配置文件
    ```

    ![目录](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9212129951/p129343.png)

    ![目录结构](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9212129951/p129344.png)

2.  功能实现流程

    -   获取设备信息，设置音视频设备。

        ```
        RTCClient.instance.getDevices().then(re=>{
          try {
            RTCClient.instance.currentAudioCapture(re.audioDevices[0].deviceId);
            RTCClient.instance.currentCamera(re.videoDevices[0].deviceId);
          } catch (error) {
        
          }
        })
        ```

    -   预览。

        ```
        /**
         * 预览
         * @parame {HtmlVideoElement} video 播放预览画面的video标签
         */
         RTCClient.instance.startPreview(video);
        ```

    -   加入频道。

        ```
        /**
         * 会自动获取鉴权信息, 入会, 自动推流
         */
        RTCClient.instance.joinChannel().then((re) => {
          // 入会成功
        }).catch(err => {
          // 入会失败
        })
        ```

    -   离开频道。

        ```
        /**
         * 如果当前预览开启，会自动关闭预览再离会
         */
        RTCClient.instance.leaveChannel().then(re => {
          // 离会成功
        }).catch(err => {
             // 离会失败
        })
        ```

    -   推流与停止推流。

        ```
        // 推摄像头和麦克风
        RTCClient.instance.pubish().then(re => {
          // 推流成功
        }).catch(err => {
             // 推流失败
        })
        
        // 停止所有推流
        RTCClient.instance.unPubish().then(re => {
          // 停止推流成功
        }).catch(err => {
             // 停止推流失败
        })
        ```

    -   订阅。

        ```
        // 如果有屏幕流会自动订阅屏幕流
        RTCClient.instance.subscribe().then(re => {
          // 订阅成功
        }).catch(err => {
             // 订阅失败
        })
        ```

    -   推共享流与停止共享流。

        ```
        RTCClient.instance.publishScreen().then(re => {
          // 推流成功
        }).catch(err => {
             // 推流失败
        })
        
        RTCClient.instance.stopPublishScreen().then(re => {
          // 取消推流成功
        }).catch(err => {
             // 取消推流失败
        })
        ```

    -   静音/取消静音。

        ```
        RTCClient.instance.muteLocalMic()
        ```

    -   关闭摄像头/打开摄像头。

        ```
        /**
         * @parame {HtmlVideoElement} video 打开摄像头时预览用到的video
         */
        RTCClient.instance.muteLocalCamera(video)
        ```


