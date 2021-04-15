---
keyword: Android SDK
---

# Android SDK

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## gradle中未正确配置对RTC库的引用

![gradle中未正确配置RTC库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9241158951/p129066.png)

解决办法：

请按照正确步骤导入aar包和jar包，并在gradle中配置引用，详情请参见[集成Android SDK](/cn.zh-CN/快速入门/集成客户端SDK/Android.md)。

## 隐私权限未申请

![隐私权限未申请](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9241158951/p129067.png)

解决办法：

-   您需要添加摄像头、麦克风、网络，访问存储权限。在AndroidManifest.xml文件中添加权限。

    ```
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>         
    ```

-   您需要在代码里动态申请权限。


## 未在主线程初始化SDK

![未初始化SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9241158951/p129068.png)

解决办法：

初始化 `AliRtcEngine`实例，并注册回调。相关回调有 `AliRtcEngineEventListener`和`AliRtcEngineNotify`，并且只能在主线程调用，详情请参见[回调及监听](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)。

```
engine = AliRtcEngine.getInstance(getApplicationContext());
engine.setRtcEngineEventListener(mEventListener);
engine.setRtcEngineNotify(mEngineNotify);
```

## 弱网情况下人声有卡顿

为了保证合唱的实时性，客户端采用了低延时策略，弱网下丢包率会相应增加。

## 开启耳返模式下，声音外放出现回声

您需要带上耳机然后进行合唱，不能通过外放。

