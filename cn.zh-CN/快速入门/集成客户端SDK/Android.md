---
keyword: [Android, SDK]
---

# Android

本文为您介绍了Android端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

## 前提条件

开发前的环境要求如下表所示，详情请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

|类别|说明|
|--|--|
|系统版本|支持Android 4.1及以上|
|API版本|不低于16|
|CPU架构|支持真机架构armeabi、armeabi-v7a、arm64-v8a|

## 集成SDK

方法一：maven 自动集成（推荐）。

1.  在根目录的build.gradle中添加maven仓库地址：

    ```
    allprojects {
        repositories {
            google()
            jcenter()
            //添加RTC需要的maven地址
            maven {
                url "http://maven.aliyun.com/nexus/content/groups/public/"
            }
        }
    }
    ```

2.  在项目的/app/build.gradle文件中，添加如下行：

    ```
    dependencies {   
            ...   
        //依赖的RTC SDK  
        implementation 'com.aliyun.rtc:AliRTC-Full:1.17.9.2005112'
    }
    ```


方法二：手动集成。

您需要下载SDK，下载链接请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。解压后的文件需导入到Android Studio工程libs文件下，文件类型和路径如下表所示。

|文件或文件夹名称|文件路径|
|--------|----|
|AliRTCSdk.arr|/app/libs/|

## 添加项目权限

根据场景需要，在 /app/src/main/AndroidManifest.xml文件中添加如下行，获取相应的设备权限：

```
<uses-permission android:name="android.permission.CAMERA"/>
<uses-permission android:name="android.permission.RECORD_AUDIO"/>
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/> 
```

## （可选）防止代码混淆

如果您的应用设置了混淆配置，需要进行以下配置。在proguard-rules.pro文件中，添加`-keep`类的配置，这样可以防止混淆AliRtcSDK公共类名称。

```
-keep class com.serenegiant.**{*;}
-keep class org.webrtc.**{*;}
-keep class com.alivc.**{*;}    
```

## 后续步骤

完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Android端实现基本功能](https://help.aliyun.com/document_detail/125524.html#task-1180891)。

