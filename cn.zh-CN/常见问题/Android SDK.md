# Android SDK {#concept_111345_zh .concept}

本文为您介绍了集成SDK时，集成工具报错的处理方法，帮助您快速定位问题，并集成SDK。

## gradle中未正确配置对RTC库的引用 {#section_a0k_bo1_or5 .section}

![Android SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170951/156698612149496_zh-CN.png)

解决办法：

请按照正确步骤导入aar包和jar包，并在gradle中配置引用，详情请参见[集成Android SDK](../../../../cn.zh-CN/快速入门/集成客户端SDK/Android.md#)。

## 隐私权限未申请 {#section_p10_8o3_ce2 .section}

![Android SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170951/156698612249497_zh-CN.png)

解决办法：

您需要添加摄像头、麦克风、网络，访问存储权限。在AndroidManifest.xml文件中添加权限。

``` {#codeblock_p3h_a6y_p1e .language-xml}
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>           
```

## 未在主线程初始化SDK {#section_klc_8kj_3up .section}

![Android SDK](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170951/156698612249498_zh-CN.png)

解决办法：

初始化 `AliRtcEngine`实例，并注册回调。相关回调有 `AliRtcEngineEventListener`和`AliRtcEngineNotify`，并且只能在主线程调用。

``` {#codeblock_59v_0mu_qyp .language-java}
mEngine = AliRtcEngine.getInstance(getApplicationContext());
mEngine.setRtcEngineEventListener(mEventListener);
mEngine.setRtcEngineNotify(mEngineNotify);
```

