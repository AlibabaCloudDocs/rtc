# 集成iOS端

您可以阅读本文，了解1对1语音聊天iOS端的集成操作。

## 前提条件

开发前的环境要求如下表所示，详情请参见：[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|iPhone设备|支持iPhone5及以上。|
|系统版本|支持iOS 8.0及以上。|
|CPU架构|支持真机架构armv7+arm64，不支持模拟器i386、x86架构。|
|Xcode版本|支持Xcode9.0及以上。下载[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。|
|其他|不支持Bitcode，不支持屏幕旋转。|

您需要先集成服务端，具体操作，请参见[集成服务端](/cn.zh-CN/解决方案/1对1语音聊天/集成服务端.md)。

**说明：** 您需要持有Apple开发证书或个人账号。

## Demo运行指引

**说明：**

您在集成iOS端时，如果遇到问题，或者Demo体验过程中出现无法创建房间或通话等问题，请参见[iOS端运行常见问题]()。

1.  下载[Demo](https://github.com/aliyun/AliRTC-UserCase-VoiceCallSolution_1To1/tree/master)并解压。

    **说明：**

    -   Demo源码中已经集成AliRTC SDK（版本：1.17）。SDK集成方式通过CocoaPods集成。
    -   源码压缩文件内分为Server端、Android端、iOS端三个文件。
    -   若遇到GitHub代码库下载缓慢的问题，可通过安装加速插件等方式加速下载。
2.  修改配置文件。

    1.  打开解压后的Demo文件夹AliRTC-UserCase-VoiceCallSolution\_1To1-master，找到iOS/demo/⁨AlivcVoiceCallSolo⁩/AlivcVoiceCallSolo⁩/Utils/Http/AliBaseHttpClient.m⁩文件。

        ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184823.png)

    2.  修改文件中的`AppServer`变量，如：`http://<服务器IP> :8080/1v1-audio`，部署到正式环境上建议绑定域名并使用：`http://<域名>/1v1-audio`。

        示例

        假设本地IP为192.0.2.1，那么`BASE_URL="http://192.0.2.1:8080/1v1-audio"`。本地IP查询，请参见[查询IP地址]()。

        **说明：**

        -   不要使用127.0.0.1的IP。
        -   手机和搭建服务器的电脑处在一个局域网中。
    3.  使用手机和电脑的浏览器验证。

        输入正确的URL（`AppServer`变量）地址，即可在浏览器中打开并看到：`Hello RTC!`。电脑端浏览器正确访问说明IP和端口号无误，手机端浏览器正确访问说明目前手机可以正常访问到服务器IP。

        ![验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8721083061/p176766.png)

3.  导入Demo源码。

    打开**Xcode**，单击**Open a project or file**，双击打开demo目录下的AlivcVoiceCallSoloClient.xcworkspace文件。

    ![打开Demo](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3693367951/p126904.png)

4.  选择运行Target为AlivcVoiceCallSoloClient，将一台IOS真机设备使用数据线与电脑链接，在**Xcode**中选择相应的真机设备，真机在设置中打开开发者模式。（暂不支持模拟器运行）

    ![AlivcVoiceCallSoloClient](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3693367951/p113071.png)

5.  修改Bundle Identifier和开发者证书。

    **说明：** Bundle Identifier改成为`com.<公司名>.<项目名>`，避免由于Bundle已被注册从而运行失败。

    **General**选项卡中修改。

    ![修改证书](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p126906.png)

    **Sign & Capabilities**选项卡中修改。

    ![证书](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p126909.png)

6.  在**Sign & Capabilities**选项卡，勾选**Automatically manage signing**，在下方选择自己的**Team**。

    1.  选择**Team**。

        ![选择Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184852.png)

    2.  若以前没添加过账号，单击**Add an Account**添加。

        ![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2457036061/p184855.png)

    3.  完成账号添加。

        ![添加Team](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3457036061/p184858.png)

    4.  在Team里选择新创建的账号即可，并且在完成签名后确保下方没有报错提示。

7.  单击**build and run**按钮编译。

    ![bulid and run](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3693367951/p126911.png)

8.  进行1对1语音聊天。

    1.  将2台真机移动端设备（Android或iOS）装上Demo App。

    2.  将2台设备都连接到同一局域网下，保证可以连接到Server端。

    3.  在第一台真机上输入任意房间号，创建房间并等待对方加入。

    4.  在第二台真机上输入相同房间号加入房间并进行通话。


## Demo源码解析

-   项目结构说明。

    **说明：** Demo是以Cocoapods Lib的方式集成到项目中的。

    -   RTC把开发的业务代码封装到名称为AlivcVoiceCallSolo的库当中，这样AlivcVoiceCallSolo就可以像一个本地的第三方库一样。可以随便移植到其他项目中，只需在Podfile中指定AlivcVoiceCallSolo库的路径即可。如下所示：

        ```
            pod 'AlivcVoiceCallSolo', :path => './AlivcVoiceCallSolo'
        
            ##   pod 'AlivcVoiceCallSolo'  说明项目依赖AlivcVoiceCallSolo库
            ##   path => './AlivcVoiceCallSolo'  指明AlivcVoiceCallSolo库的位置(相对于Podfile)
        ```

        名词解释如下：

        -   pod：表示工程依赖AlivcVoiceCallSolo库。
        -   path：表示AlivcVoiceCallSolo库的路径（相对podfile文件）。
        ![路径](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3693367951/p126913.png)

    -   AlivcVoiceCallSolo组件库目录说明，如下所示：

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

        ![目录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4693367951/p126914.png)

-   功能实现。
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


