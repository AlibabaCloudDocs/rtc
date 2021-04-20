---
keyword: [常见问题, Android SDK]
---

# 集成Android SDK时的常见问题

通过阅读本文，您可以了解集成Android SDK时常见的问题及解决方法。

## gradle中未正确引用Android SDK依赖文件导致编译报错

-   问题现象：编译代码时可能会出现以下错误：

    ![gradle中未正确配置RTC库](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9241158951/p129066.png)

-   可能原因：gradle中未正确引用Android SDK依赖文件。
-   解决方案：请按照正确步骤导入aar包和jar包，并在gradle中配置引用。具体操作，请参见[集成Android SDK](/cn.zh-CN/快速入门/集成客户端SDK/Android.md)。

## 隐私权限未申请导致程序运行时报错

-   问题现象：程序运行时可能会出现以下错误：

    ![隐私权限未申请](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9241158951/p129067.png)

-   可能原因：隐私权限未申请。
-   解决方案：
    -   在AndroidManifest.xml文件中添加摄像头、麦克风、网络、访问存储等权限。

        ```
        <uses-permission android:name="android.permission.CAMERA" />
        <uses-permission android:name="android.permission.RECORD_AUDIO" />
        <uses-permission android:name="android.permission.INTERNET" />
        <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
        <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
        <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
        <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>         
        ```

    -   在代码里动态申请权限。

## 未在主线程初始化SDK导致程序运行时报错

-   问题现象：程序运行时可能会出现以下错误：

    ![未初始化SDK](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9241158951/p129068.png)

-   可能原因：未在主线程初始化实例。
-   解决方案：初始化 `AliRtcEngine`实例，并注册回调。相关回调有 `AliRtcEngineEventListener`和`AliRtcEngineNotify`，并且只能在主线程调用。

    ```
    engine = AliRtcEngine.getInstance(getApplicationContext());
    engine.setRtcEngineEventListener(mEventListener);
    engine.setRtcEngineNotify(mEngineNotify);
    ```

    更多回调接口详情，请参见[回调及监听](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)。


## 弱网情况下人声有卡顿

-   问题现象：在线KTV场景下，弱网情况下人声有卡顿。
-   可能原因：为了保证合唱实时性，客户端采用了低延时策略，弱网下丢包率会相应增加。

## 开启耳返模式下声音外放有回声

-   问题现象：在线KTV场景下，开启耳返模式下声音外放有回声。
-   解决方案：您需要带上耳机然后进行合唱，不能通过外放。

