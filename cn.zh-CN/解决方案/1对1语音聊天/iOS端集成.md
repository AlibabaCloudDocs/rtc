# iOS端集成

通过阅读本文，您可以了解1对1语音聊天iOS端的集成操作。

## 环境要求

iOS端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 前提条件

-   服务端已集成并开启。具体操作，请参见[服务端集成](/cn.zh-CN/解决方案/1对1语音聊天/服务端集成.md)。
-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。

## 操作步骤

1.  下载并解压Demo，更多信息，请参见[Demo源码下载](/cn.zh-CN/.md)。

    **说明：**

    -   Demo源码中已通过Pod方式集成AliRTC iOS SDK（1.17版本）。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   如果GitHub代码库下载缓慢，可安装加速插件等方式加速下载。
2.  配置Demo工程。

    1.  打开iOS/demo/⁨AlivcVoiceCallSolo⁩/AlivcVoiceCallSolo⁩/Utils/Http/AliBaseHttpClient.m⁩文件。

        ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184823.png)

    2.  修改文件中的`AppServer`值。

        例如本地服务端IP地址为192.0.2.1，则`AppServer`的值为`http://192.0.2.1:8080/1v1-audio`。本地服务端IP地址查询，请参见[查询IP地址]()。

        **说明：**

        -   服务端IP地址禁止使用127.0.0.1。
        -   移动端和服务端处于同一局域网中。
        -   如果需要部署到正式环境，请绑定域名即`AppServer`的值为`http://<域名>/1v1-audio`。
    3.  验证移动端和服务端。

        分别在移动端和服务端浏览器中访问`AppServer`地址，如果显示如下图所示，表示移动端访问服务端正常。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8721083061/p176766.png)

3.  运行Demo。

    1.  使用Xcode打开demo目录下的AlivcVoiceCallSoloClient.xcworkspace工程文件。

    2.  选择运行的Target为AlivcVoiceCallSoloClient，然后将iOS设备与电脑有线连接，并在Xcode中选择相对应的设备（暂不支持模拟器运行）。

        ![AlivcVoiceCallSoloClient](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3693367951/p113071.png)

    3.  单击**General**页签，修改**Bundle Identifier**，建议将Bundle Identifier改成com.<公司名\>.<项目名\>，避免由于Bundle已被注册从而运行失败。

        ![修改证书](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p126906.png)

    4.  单击**Signing & Capabilities**页签，选中**Automatically manage signing**，然后单击**Team**下拉框，根据实际情况选择Team。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

        **说明：** 如果之前没有添加过账号，可以选择**Add an Account...**，根据提示添加账号，然后在此处选择新添加的账号。

    5.  单击![004](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2963821161/p228524.png)，编译并运行。如果编译过程中出现问题或无法正常通话，请参见[iOS端运行常见问题]()。

        ![bulid and run](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3693367951/p126911.png)

4.  进行1对1语音聊天。

    1.  将两台移动端设备安装Demo App。

    2.  将两台设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台设备上输入任意房间号，创建房间并等待对方加入。

    4.  在第二台设备上输入相同房间号加入房间并进行通话。


## Demo目录结构说明

RTC把开发的业务代码封装到AlivcVoiceCallSolo库中，因此只需在Podfile中指定AlivcVoiceCallSolo库的路径，AlivcVoiceCallSolo就可以以本地第三方库的形式移植到其他项目中。如下所示：

```
    pod 'AlivcVoiceCallSolo', :path => './AlivcVoiceCallSolo'
    ##   pod 'AlivcVoiceCallSolo'  说明项目依赖AlivcVoiceCallSolo库
    ##   path => './AlivcVoiceCallSolo'  指明AlivcVoiceCallSolo库的位置(相对于Podfile)
```

AlivcVoiceCallSolo组件库目录说明，如下所示：

![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4693367951/p126914.png)

|文件名|说明|
|---|--|
|AlivcVoiceCallSolo.podspec|组件的描述文件。|
|AlivcVoiceCallSolo.bundle|存放资源的bundle。|
|AlivcVoiceCallChannelViewController|首页。|
|AlivcVoiceCallChattingViewController|聊天页。|
|AlivcDismissTransition|转场动画。|
|AlivcPanInteractiveTransition|
|AlivcPresentTransition|
|AlivcVoiceCallSettingViewController|设置页。|
|AlivcVideoCallUserAuthrization|工具类。|
|NSBundle+AlivcVoiceCallSolo|
|UIViewController+Alert|
|AliBaseHttpClient|网络请求。|
|AliRequestList|

## 主要功能说明

-   创建并加入频道。

    ```
      //实例化AliRtcEngine并设置代理。
       _engine = [AliRtcEngine sharedInstance:self extras:@""];
       //获取授权信息。
       //AliRtcAuthInfo:各项参数均需要客户AppServer（客户的server端）通过OpenAPI来获取，然后AppServer下发至客户端，客户端将各项参数赋值后，即可joinChannel。
       AuthInfo *authInfo = "从server端获取" 
      [_engine  joinChannel:authInfo name:name onResult:^(NSInteger errCode) {
                        //加入频道回调处理
                        if (errCode == 0) {
                            //加入房间成功
                        } else {
                         //加入房间失败
                        }
                    }];
    ```

-   离开频道。

    ```
    //离开频道。
    [self.engine leaveChannel];
    //销毁SDK实例。
    [AliRtcEngine destroy];
    ```

-   播放伴奏。

    ```
    NSString *path = “文件的路径”
    NSString *url = [path stringByAddingPercentEscapesUsingEncoding:NSUTF8StringEncoding];
    //预加载音效文件。
    [self.engine preloadAudioEffectWithSoundId:soundId filePath:url];
    //播放音效。
    [self.engine playAudioEffectWithSoundId:soundId filePath:url cycles:1 publish:YES];   
    ```

-   暂停伴奏。

    ```
    [self.engine pauseAudioEffectWithSoundId:soundId];           
    ```

-   停止伴奏。

    ```
    [self.engine stopAudioEffectWithSoundId:soundId];         
    ```

-   恢复播放伴奏。

    ```
    [self.engine resumeAudioEffectWithSoundId:soundId];       
    ```

-   静音模式。

    ```
    [self.engine muteLocalMic:YES];         
    ```

-   取消静音模式。

    ```
    [self.engine muteLocalMic:NO];       
    ```

-   开启扬声器。

    ```
    [self.engine enableSpeakerphone:YES];               
    ```

-   关闭扬声器。

    ```
    [self.engine enableSpeakerphone:NO];           
    ```


