# Android

RTC SDK为您提供网络测速的接口方法，您可以在音视频通话前进行网络测速，并根据当前的网络质量切换网络，获取更高质量的音视频通话。通过阅读本文，您可以了解网络测速的方法。

1.  使用网络测速功能时，应用层需要实现`AliRtcEngineEventListener`的`onNetworkQualityProbeTest`回调，用于接收测试结果返回。

    ```
    private AliRtcEngineEventListener mEventListener = new AliRtcEngineEventListener() {
            @Override
            public void onNetworkQualityProbeTest(AliRtcEngine.AliRtcNetworkQuality aliRtcNetworkQuality) {
                //AliRtcNetworkQuality返回测速后的网络质量
            }
    };
    ```

2.  创建SDK引擎实例后，在加入频道之前，调用接口`startNetworkQualityProbeTest`启动测速功能，开始测速后，测试结果将从`onNetworkQualityProbeTest`中回调返回。

    **说明：** 网络测试功能必须在加入频道前使用，加入频道前您需要主动停止网络测速。

    ```
     AliRtcEngine mAliRtcEngine =AliRtcEngine.getInstance(this);
     int i = mAliRtcEngine.startNetworkQualityProbeTest();
    ```

3.  结束网络测速时，调用接口`stopNetworkQualityProbeTest`停止测速。

    ```
    mAliRtcEngine.stopNetworkQualityProbeTest();
    ```


