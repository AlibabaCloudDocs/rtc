# Android {#task_1096283 .task}

本文为您介绍了Android端集成SDK操作，帮助您快速集成SDK并能使用音视频通信基本功能。

开发前的环境要求如下表所示，详情请参见[使用限制](../../../../cn.zh-CN/产品简介/使用限制.md#)。

|类别|说明|
|--|--|
|系统版本|最低支持Android 4.1|
|API版本|不低于16|
|CPU架构|支持真机架构armeabi、armeabi-v7a|

您需要下载[Android SDK](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/125204/cn_zh/1564562210629/AliRTCSdk_1.11.5.1907174.zip)。解压后的文件需导入到Android Studio工程libs文件下，文件类型如下表所示。

|文件/文件夹名称|文件类型|
|--------|----|
|AliRTCSdk|jar|
|utdid4all-1.5.0-proguard|jar|
|Sophonsdk|aar|
|alivc-core-rtc|aar|
|webrtclib|aar|

1.  使用Android Studio软件创建一个新的Empty Acitivity，并根据下图所示进行配置。 

    **说明：** 本文档的Android Studio版本为3.4.1。

    ![创建Project](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/763460/156457359950610_zh-CN.png)

2.  把解压的SDK文件导入到app/libs目录下。 

    ![引jar包](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/763460/156457359950658_zh-CN.png)

3.  在app/src/build.gradle文件中添加如下配置。 

    ``` {#codeblock_ch2_k58_64e .language-json}
    android {
        ...
        repositories {
            flatDir {
                dirs 'libs'
            }
        }
    }
    dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar','*.aar'])
    ...
    ```

    ![配置build.gradle](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/763460/156457359950719_zh-CN.png)

4.  在app/src/main/AndroidManifest.xml文件中添加摄像头、麦克风、网络，访问存储权限。在代码里面需要添加动态权限申请。 

    ``` {#codeblock_ler_the_4km .language-java}
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>        
    ```

5.  （可选）混淆配置。 如果您的应用设置了混淆配置，需要进行以下配置。在proguard-rules.pro文件中，添加`-keep`类的配置，这样可以防止混淆AliRtcSDK公共类名称。 

    ``` {#codeblock_y71_uhf_ojj .language-java}
    -keep class com.serenegiant.**{*;}
    -keep class org.webrtc.**{*;}
    -keep class com.alivc.**{*;}           
    ```

6.  单击**Sync Project With Gradle Files**，同步项目文件，直到同步完成。

完成集成SDK操作，您可以实现音视频通信的基本功能，详情请参见[Android端实现基本功能](cn.zh-CN/快速入门/实现基本功能/Android.md#)。

