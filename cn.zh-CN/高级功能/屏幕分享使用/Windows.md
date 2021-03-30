# Windows

Windows端屏幕分享功能分为屏幕分享（支持指定区域进行分享）和窗口分享，应用侧可根据实际需求分享屏幕内容并进行推流。通过阅读本文，您可以了解到Windows端屏幕分享的方法。

## 屏幕分享

1.  推流端创建SDK实例后，通过接口getScreenShareSourceInfo可以获取当前屏幕分享源，其中参数source\_type指定AliRtcScreenShareDesktop，然后SDK通过source\_list参数返回当前设备所有显示器设备。

    ```
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
    // 获取屏幕分享source
    AliRtcScreenSourceList sourceList;
    pEngine->getScreenShareSourceInfo(AliRtcScreenShareDesktop, sourceList);
    // 遍历所有支持屏幕
    for (int i = 0; i < sourceList.sourceNum; i++) {
    }
    ```

    **说明：** 屏幕分享只有在当前设备接入显示器超过1个时，会返回多个source。

2.  通过接口setScreenShareSource设置屏幕分享source，其中source参数中的sourceId设置为需要分享的屏幕source id（上一步骤中获取），同时如果业务需要只分享屏幕中的部分区域，则设置source参数中的isShareByRegion字段为true，同时将要分享区域的左上角坐标和宽高，赋值给source参数中的shareRegion变量。

    ```
    // 设置屏幕分享源为屏幕分享，并指定分享屏幕source id
    AliRtcScreenSource source;
    source.eType = AliRtcScreenShareDesktop;
    source.sourceId = sourceId;
    
    // 如果需要按区域分享，则设置isShareByRegion为true，并指定分享区域，如分享屏幕左上角100 x 100的区域
    source.isShareByRegion = true;
    source.shareRegion.originX = 0.f;
    source.shareRegion.originY = 0.f;
    source.shareRegion.width = 100.f;
    source.shareRegion.height = 100.f;
    
    // 设置分享内容
    pEngine->setScreenShareSource(source);
    ```

    **说明：** 按区域分享时，设置分享区域最小分辨率为16x16，设置区域小于最小分辨率时重置为最小分辨率；按区域分享时，设置分享区域超过实际桌面分辨率时，将按照完整桌面分辨率分享，桌面分辨率可通过接口getDesktopResolution接口获取，用于分享区域设置校验。

3.  配置分享内容完成后，启动屏幕共享推流。

    ```
    // 配置屏幕分享推流
    pEngine->configLocalScreenPublish(true);
    
    // 启动推流
    pEngine->publish();
    ```

4.  结束分享时，配置屏幕共享流停推。

    ```
    // 配置屏幕分享停止
    pEngine->configLocalScreenPublish(false);
    
    // 启动停推
    pEngine->publish();
    ```


## 窗口分享

1.  推流端创建SDK实例后，通过接口getScreenShareSourceInfo可以获取当前屏幕分享源，其中参数source\_type指定AliRtcScreenShareWindow，然后SDK通过source\_list参数返回当前电脑上所有可见窗口的source id和source title。

    ```
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
    
    // 获取屏幕分享source
    AliRtcScreenSourceList sourceList;
    pEngine->getScreenShareSourceInfo(AliRtcScreenShareWindow, sourceList);
    
    // 遍历所有支持分享窗口
    for (int i = 0; i < sourceList.sourceNum; i++) {
    
    }
    ```

    **说明：** SDK只会返回所有当前可见（没有最小化且Size不为0）的窗口作为分享源。

2.  通过接口setScreenShareSource设置屏幕分享source，其中source参数的sourceId设置为需要分享窗口id（上一步骤中获取）。

    ```
    // 设置屏幕分享源为屏幕分享，并指定分享屏幕source id
    AliRtcScreenSource source;
    source.eType = AliRtcScreenShareWindow;
    source.sourceId = sourceId;
    
    // 设置分享内容
    pEngine->setScreenShareSource(source);
    ```

3.  配置分享内容完成后，启动屏幕共享推流。

    ```
    // 配置屏幕分享推流
    pEngine->configLocalScreenPublish(true);
    
    // 启动推流
    pEngine->publish();
    ```

    **说明：** 设置分享源到启动推流过程中，如果指定的分享窗口发送变化（被关闭、不可见）导致无法分享，推流将会发生失败，业务方调用时需要关注推流结果是否成功；分享过程中，如果分享窗口被最小化，同样会导致SDK无法抓取数据，分享内容异常。

4.  结束分享时，配置屏幕共享流停推。

    ```
    // 配置屏幕分享停止
    pEngine->configLocalScreenPublish(false);
    
    // 启动停推
    pEngine->publish();
    ```


## 订阅端

订阅端用户可通过自动或手动方式订阅推流端屏幕分享视频流，并设置对应View显示，详情请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)。

