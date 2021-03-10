# Windows

RTC SDK为您提供网络测速的接口方法，您可以在音视频通话前进行网络测速，并根据当前的网络质量切换网络，获取更高质量的音视频通话。通过阅读本文，您可以了解网络测速的方法。

1.  使用网络测速功能时，应用层需要继承并实现`onLastmileDetectResultWithQuality`回调，用于接收测试结果返回。

    ```
        /**
        * @brief 最后一公里网络质量探测回调
        * @param networkQuality 网络质量
        */
        virtual void onLastmileDetectResultWithQuality(AliRtcNetworkQuality networkQuality) 
        {
            // 接收网络测速
        };
    ```

2.  创建SDK引擎实例后，在加入频道之前，调用接口`startLastmileDetect`启动测速功能。开始测速后，测试结果将从`onLastmileDetectResultWithQuality`中回调返回。

    **说明：** 网络测试功能必须在加入频道前使用，加入频道前您需要主动停止网络测速。

    ```
     /**
     * @brief 开始最后一公里网络质量探测
     * @return 成功返回0，失败返回非0值
     */
     virtual int startLastmileDetect() = 0;
    
     AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(listener, "");
     pEngine->startLastmileDetect();
    ```

3.  结束网络测速时，调用接口stopLastmileDetect停止测速。

    ```
     /**
     * @brief 停止最后一公里网络质量探测
     */
     virtual int stopLastmileDetect() = 0;
    
     pEngine->stopLastmileDetect();
    ```


