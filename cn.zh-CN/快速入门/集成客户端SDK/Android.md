---
keyword: [Android, SDK, 集成]
---

# Android

通过阅读本文，您可以了解Android端集成SDK的方法。

## 环境要求

Android端具体环境要求，更多信息，请参见[使用限制](/cn.zh-CN/产品简介/使用限制.md)。

## 集成SDK

方法一：maven集成（推荐）

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

    **说明：** 此处maven依赖的版本仅供参考，获取最新的maven依赖，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

3.  在/app/src/main/AndroidManifest.xml文件中添加如下代码，获取相应的设备权限。

    ```
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.RECORD_AUDIO"/>
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/> 
    ```

4.  配置防止代码混淆。

    在proguard-rules.pro文件中，添加`-keep`类的配置，可以防止混淆RTC SDK公共类名称。

    ```
    -keep class com.serenegiant.**{*;}
    -keep class org.webrtc.**{*;}
    -keep class com.alivc.**{*;}    
    ```


方法二：手动集成

1.  下载并解压Android SDK，下载地址，请参见[客户端SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  复制SDK文件AliRTCSdk.aar到App模块下的libs文件夹中。

3.  在/app/src/main/AndroidManifest.xml文件中添加如下代码，获取相应的设备权限。

    ```
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.RECORD_AUDIO"/>
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/> 
    ```

4.  配置防止代码混淆。

    在proguard-rules.pro文件中，添加`-keep`类的配置，可以防止混淆RTC SDK公共类名称。

    ```
    -keep class com.serenegiant.**{*;}
    -keep class org.webrtc.**{*;}
    -keep class com.alivc.**{*;}    
    ```


完成集成SDK操作后，您可以实现音视频通信的基本功能。具体操作，请参见[Android端实现基本功能](/cn.zh-CN/快速入门/实现基本功能/Android.md)。

