---
keyword: [ios, 弱网]
---

# iOS

RTC SDK为您提供了网络质量监控的功能，您可以通过网络状况变化时回调获取网络质量，设置对应的音视频规格，以确保基础通信体验。通过阅读本文，您可以了解获取网络质量及设置音视频规格的方法。

## 功能简介

在网络质量不理想的情况下，音视频通信的质量受客观因素影响会下降。当监控到弱网环境时，为保证基础通信体验，建议您使用SDK对应的方法分别在发布端和订阅端进行如下优化。

-   调整视频流规格：通过设置较低档位规格的VideoProfile，减少视频通信的网络资源占用。
-   切换视频为小流：小流有着与大流相同的宽高比，但是分辨率和码率相对较低，网络资源占用的需求较低。
-   仅发布音频流：在极端网络环境下，可以选择只发送音频流，从而保证通信的持续。

您可以通过onNetworkQualityChanged（网络质量变化时回调）方法获得网络质量，然后在根据实际策略进行优化。

```
- (void)onNetworkQualityChanged:(NSString *)uid 
        upNetworkQuality:(AliRtcNetworkQuality)upQuality             
        downNetworkQuality:(AliRtcNetworkQuality)downQuality;
```

|参数|类型|描述|
|--|--|--|
|uid|NSString \*|网络质量发生变化的用户ID，用户ID为空表示本地，其他表示远端。|
|upQuality|[AliRtcNetworkQuality](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|上行网络质量。|
|downQuality|[AliRtcNetworkQuality](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|下行网络质量。|

## 实现方法

以下为常用的设置音视频流规格的方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)。

-   setVideoProfile：设置视频流的参数。

    ```
    - (void)setVideoProfile:(AliRtcVideoProfile)profile forTrack:(AliRtcVideoTrack)track;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |profile|[AliRtcVideoProfile](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频流参数。默认为分辨率480\*640，帧率15的相机流。|
    |track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|需要设置的视频Track类型。默认相机流。|

-   configRemoteCameraTrack：设置是否订阅远端相机流。

    ```
    - (void)configRemoteCameraTrack:(NSString *)uid preferMaster:(BOOL)master enable:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |uid|NSString \*|用户ID。|
    |master|BOOL|YES为订阅大流，NO为订阅次小流。默认为订阅大流。|
    |enable|BOOL|YES为订阅远端相机流，NO为停止订阅远端相机流。默认为不订阅。|

    **说明：** 该接口需要对流进行操作时（如手动订阅，关闭订阅），必须调用subscribe才能生效。

-   configLocalCameraPublish：设置是否允许发布相机流。

    ```
    - (void)configLocalCameraPublish:(BOOL)enable;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |enable|BOOL|YES为允许发布相机流，NO为不允许。默认为允许发布相机流。|

    **说明：** 手动发布时，需要调用publish才能生效。


