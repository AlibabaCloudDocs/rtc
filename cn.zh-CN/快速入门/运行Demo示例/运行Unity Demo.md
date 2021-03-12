# 运行Unity Demo

本章节为您介绍了Unity Demo的集成操作步骤。

您需要开通阿里云RTC服务并在控制台成功创建应用，具体操作请参见[入门概述](/cn.zh-CN/快速入门/入门概述.md)。

获取Token，详情请参见[服务端生成Token](/cn.zh-CN/常用功能/生成Token.md)。

## 创建Unity项目

1.  打开Unity，单击**新建**。

2.  输入项目名称、项目保存位置，并选择3D模版。

3.  单击**创建**。

    ![创建Unity](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4655588951/p88566.png)


## 集成SDK

1.  下载[Unity SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

    解压后包含sample和sdk两个目录，sample目录为Unity对接工程，sdk目录为Unity版本SDK。

2.  在项目Assets目录下新建Plugins目录。

3.  复制SDK中以下目录文件到项目Plugins目录。

    |平台|文件或文件夹|项目路径|
    |--|------|----|
    |Android|/Android/AliRtcCwrapper.aar|/Assets/Plugins/Android|
    |/Android/AliRTCSdk.jar|/Assets/Plugins/Android|
    |/Android/alivc-core-rtc.aar|/Assets/Plugins/Android|
    |/Android/Sophonsdk.aar|/Assets/Plugins/Android|
    |/Android/utdid4all-1.5.0-proguard.jar|/Assets/Plugins/Android|
    |/Android/webrtclib.aar|/Assets/Plugins/Android|
    |iOS|/iOS/AliRTCSdk.framework|/Assets/Plugins/iOS|
    |/iOS/libAliRTCSdkCInterface.a|/Assets/Plugins/iOS|
    |macOS|/macOS/AliRTCSdkCWrapper.bundle|/Assets/Plugins/macOS|
    |Windows|/x86/AliRTCSdk.dll|/Assets/Plugins/x86|
    |/x86/AliRTCSdkCWrapper.dll|/Assets/Plugins/x86|
    |/x64/AliRTCSdk.dll|/Assets/Plugins/x64|
    |/x64/AliRTCSdkCWrapper.dll|/Assets/Plugins/x64|

4.  在项目Assets目录下新建Scripts目录。

5.  复制SDK中以下目录文件到项目Scripts目录。

    |文件|项目路径|
    |--|----|
    |/Scripts/AliRtcEngine.cs|/Assets/Scripts|
    |/Scripts/IAliRtcEngineBase.cs|/Assets/Scripts|
    |/Scripts/VideoDisplaySurface.cs|/Assets/Scripts|


## 实现音视频通话功能

1.  添加UI控制。

    您可以创建用户界面，以Unity Sample为例，创建本地视频窗口GameObject（LocalVideoCube）和远端视频窗口GameObject（RemoteVideoCube），以及控制按钮ControlButton。

    ![实现通话1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4655588951/p88565.png)

2.  UI界面保存到/Assets/Scenes/SampleScene.unity。

3.  创建控制音视频通信功能的Home.cs文件，并将该文件添加到主Main Camera，使得Home.cs文件在Main Camera启动时就被加载。

4.  获取权限（仅Android操作）。

    在UNITY\_2018\_3\_OR\_NEWER及以上版本，Android设备需要在Unity中设置主动向用户获取麦克风和相机权限，需要调用CheckPermission主动获取权限。

    ```
    private ArrayList permissionList = new ArrayList();
    void Start ()
    {
    #if (UNITY_2018_3_OR_NEWER && UNITY_ANDROID)
        permissionList.Add(Permission.Microphone);
        permissionList.Add(Permission.Camera);
    #endif
    }
    
    void Update ()
    {
    #if (UNITY_2018_3_OR_NEWER && UNITY_ANDROID)
        CheckPermission();
    #endif
    
    }
    
    private void CheckPermission()
    {
    #if (UNITY_2018_3_OR_NEWER && UNITY_ANDROID)
        foreach (string permission in permissionList)
        {
            if (Permission.HasUserAuthorizedPermission(permission))
            {
    
            }
            else
            {
                Permission.RequestUserPermission(permission);
            }
        }
    #endif
    }
    ```

    此外，集成Android平台时，需要AndroidManifest.xml文件和project.properties文件来管理项目权限和项目属性，可以直接拷贝AliRTCSdkEngine.plugin目录到/Assets/Plugins/Android。

    ![通话2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4655588951/p88567.png)

5.  初始化IAliRtcEngine。

    执行创建IAliRtcEngine，根据需要注册侦听通知回调，设置自动推流订阅模式。

    ```
    string extra = "";
    IAliRtcEngine mRtcEngine = IAliRtcEngine.GetEngine (extra);
    mRtcEngine.OnJoinChannelNotify = onJoinChannelNotify;
    mRtcEngine.OnPublishNotify = onPublishNotify;
    mRtcEngine.OnSubscribeNotify = onSubscribeNotify;
    mRtcEngine.OnRemoteUserOnLineNotify = onRemoteUserOnLineNotify;
    mRtcEngine.OnRemoteUserOffLineNotify = onRemoteUserOffLineNotify;
    mRtcEngine.OnRemoteTrackAvailableNotify = onRemoteTrackAvailableNotify;
    mRtcEngine.OnSubscribeChangedNotify = onSubscribeChangedNotify;
    mRtcEngine.OnLeaveChannelResultNotify = onLeaveChannelResultNotify;
    mRtcEngine.SetAutoPublish(true, true);
    ```

6.  打开本地预览。

    进入频道前需要启动本地视频采集预览显示，获取UI中VideoCube对象，添加VideoDisplaySurface到VideoCube上。

    **说明：** VideoDisplaySurface是SDK封装用于视频渲染的C\#类，任何Unity中GameObject物体上需要显示视频内容，必须要绑定VideoDisplaySurface。

    VideoDisplaySurface主要有以下三个功能：

    -   void SetUserId\(string uid\)：设置渲染视频的用户ID，本地uid填空字符串`""`。
    -   void SetVideoTrack\(AliRTCVideoTrack track\)：设置视频流类型，有camera（相机流）和screen（共享流）两种，用于区分同一用户ID推送的两种不同的是视频流。
    -   void SetEnable\(bool enable\)：控制视频是否显示。
    添加surface后，调用IAliRtcEngine接口设置本地预览和开启预览。

    ```
    GameObject go = GameObject.Find("LocalVideoCube");
    VideoDisplaySurface surface = go.GetComponent<VideoDisplaySurface>();
    surface.SetUserId("");
    surface.SetVideoTrack(AliRTCVideoTrack.VIDEO_TRACK_CAMERA);
    surface.SetEnable(true);
    mRtcEngine.SetLocalViewConfig(true);
    mRtcEngine.ConfigExternalVideoRendering(true);
    mRtcEngine.StartPreview();
    ```

7.  获取频道鉴权信息。

    该步骤主要通过和AppServer进行通信，获取进入的频道名称以及对应的鉴权信息，成功获取到的信息需要保存在AliRTCAuthInfo结构中。

8.  加入频道。

    成功获取到入会鉴权信息后，通过调用接口JoinChannel加入频道，需要传递参数有AliRTCAuthInfo和用户名称。调用加入频道接口后，SDK会通过OnJoinChannelNotify通知回调是否入会成功，参数errorCode为0表示入会成功，其他表示失败。

    ```
    mRtcEngine.JoinChannel(authInfo, "userName");
    
    private void onJoinChannelNotify (int errorCode)
    {
        if (errorCode == 0)
        {
            Debug.Log("加入频道成功");
        }
        else
        {
            Debug.Log("加入频道失败");
        }
    }
    ```

9.  远端用户视频显示。

    订阅远端用户的音视频流相关的回调是onSubscribeChangedNotify，控制远端用户视频的显示在该回调中实现。

    onSubscribeChangedNotify有三个参数：

    -   userId表示远端用户ID。
    -   audioTrack有mic（麦克风）和none两种类型，none表示当前没有远端音频流。
    -   videoTrack有camera、screen、both和none四种类型，分别表示该用户的视频流状态，both表示同时订阅远端用户的camera（相机流）和screen（共享流），none表示当前没有远端视频流。
    在回调中，检查参数videoTrack是否为camera、screen、both三者中的一种，如果是需要使用GameObject对象进行显示，并添加VideoDisplaySurface，如果videoTrack为none，需要控制GameObject对象取消显示。

    ```
    private void onSubscribeChangedNotify (string userId, int audioTrack, int videoTrack)
    {
        if (videoTrack == (int)AliRTCVideoTrack.VIDEO_TRACK_CAMERA)
        {
            GameObject go = GameObject.Find("RemoteVideoCube");
            if (!ReferenceEquals(go, null))
            {
                VideoDisplaySurface surface = go.GetComponent<VideoDisplaySurface>();
                surface.SetUserId(userId);
                surface.SetVideoTrack(AliRTCVideoTrack.VIDEO_TRACK_CAMERA);
                surface.SetEnable(true);
            }
    
        }
        else if (videoTrack == (int)AliRTCVideoTrack.VIDEO_TRACK_NONE)
        {
            GameObject go = GameObject.Find("RemoteVideoCube");
            if (!ReferenceEquals(go, null))
            {
                VideoDisplaySurface surface = go.GetComponent<VideoDisplaySurface>();
                surface.SetEnable(false);
            }
    
        }
    }
    ```

10. 离开频道。

    结束音视频通话时调用接口LeaveChannel离开频道，离开频道前需要关闭本地预览以及移除远端视频显示。

    ```
    mRtcEngine.StopPreview();
    GameObject go = GameObject.Find("LocalVideoCube");
    VideoDisplaySurface surface = go.GetComponent<VideoDisplaySurface>();
    surface.SetEnable(false);
    go = GameObject.Find("RemoteVideoCube");
    surface = go.GetComponent<VideoDisplaySurface>();
    surface.SetEnable(false);
    mRtcEngine.LeaveChannel();
    ```

11. 销毁IAliRtcEngine。

    调用IAliRtcEngine的Destroy方法退出App或者释放内存。


## Unity Editor中调试

Unity Editor中调试只需要确保放入macOS或Windows所需的文件或文件夹到/Assets/Plugins目录即可。

## 工程导出设置

-   Mac平台：

    Unity编译导出Mac平台应用，macOS10.15以下版本无需做额外设置，只需选中Target Platform为Mac OS， 勾上Development Build即可；macOS10.15及以上版本需要选择Player Settings，在Player的Other Settings选项中，将Camera Usage Description文本框中添加open camera字符串，Microphone Usage Description文本框中添加open microphone字符串。

    ![mac](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88568.png)

-   iOS平台：

    设置Graphics APIs为OpenGLES2，去掉多线程渲染Multithreaded Rendering。

    ![iOS1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88569.png)

    ![ios2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88570.png)

    iOS导出为xcode工程，在xcode工程中需要先关闭bitcode，在info.plist文件中添加麦克风和相机访问，并且在Embed Framework中添加AliRTCSdk.framework，开启background模式，以上设置也可以在Unity打包后处理脚本中添加导出的工程设置。

-   Android平台：

    Android应用导出前，切换到Android Platform，选择Player Settings，在Player的Other Settings选项中，设置Graphics APIS为OpenGLES2，去掉多线程渲染Multithreaded Rendering，Scripting Backend选择IL2CPP。

    ![Android1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88571.png)

    ![Android2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88572.png)

    **说明：** 默认Android打包ARMv7版本，如果打包ARM64版本，需要选中Target Architectures中ARM64选项。

    选中该Export Project后导出目录需要有子级文件夹，例如可导出在以下目录：Aliyun/UnityRTC。

    ![Android3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88573.png)

-   Windows平台：

    Windows应用导出前，切换到PC Platform，选择Player Settings，在Player的Scripting Backend选项选中Mono。

    ![windows](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5655588951/p88574.png)


