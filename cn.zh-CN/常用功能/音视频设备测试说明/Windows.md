# Windows

RTC SDK为您提供音视频设备测试的方法，您可以在音视频通话前检查当前设备上的摄像头，麦克风以及扬声器等音视频设备是否正常工作，以保证音视频通话质量。通过阅读本文，您可以了解音视频设备测试的方法。

## 摄像头测试

1.  创建SDK实例后，应用层可以调用接口`getCameraList`，获取当前设备上所有可用摄像头，返回设备列表中将同时返回设备ID及设备名称，应用层可选择通过设备名称或设备ID进行判断，并通过接口`setCurrentCamera`或`setCurrentCameraById`选中需要测试的设备。

    ```
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(listener, "");
    
    AliRtcDeviceList cameraList;
    pEngine->getCameraList(cameraList);
    
    #if defined(USE_DEVIC_NAME)
    // 可以通过遍历所有摄像头设备名，查找并设置需要测试的设备
    std::string matchDeviceName = /*测试设备名*/;
    for (size_t i = 0; i != cameraList.deviceNames.size(); ++i)
    {
        AliRtc::String deviceName = cameraList.deviceNames.at(i);
        if(std::string(deviceName.c_str()) == matchDeviceName)
        {
            // 设置测试设备
            pEngine->setCurrentCamera(deviceName);
        }    
    }
    #else
    // 可以通过遍历所有摄像头设备ID并查找需要测试的设备
    std::string matchDeviceId = /*测试设备ID*/;
    for (size_t i = 0; i != cameraList.deviceIds.size(); ++i)
    {
        AliRtc::String deviceId = cameraList.deviceIds.at(i);
        if(std::string(deviceId.c_str()) == matchDeviceId)
        {
            // 设置测试设备
            pEngine->setCurrentCameraById(deviceId);
        }    
    }
    #endif
    ```

2.  设置测试摄像头设备之后，通过`setLocalViewConfig`接口可以设置预览显示窗口，然后启动预览，即可通过预览画面是否正常显示，判断当前摄像头设备是否正常工作。

    ```
    // 设置预览窗口
    AliVideoCanvas canvas;
    canvas.hWnd = /*预览显示窗口句柄*/;
    pEngine->setLocalViewConfig(canvas, AliRtcVideoTrackCamera);
    
    // 开启预览检查，确认显示是否正常
    pEngine->startPreview();
    ```


## 麦克风测试

1.  创建SDK实例后，应用层需要继承`AliMediaDeviceTestEventListener`接口，实现`OnAudioDeviceRecordLevel`回调，用于接收麦克风测试时返回的音量值。再通过SDK接口`createMediaDeviceTestInterface`创建设备测试实例，并在创建时传入回调监听实例。

    ```
    // 继承实现设备测试事件回调
    class DeviceTestEventListener : public AliMediaDeviceTestEventListener
    {
    public:
        virtual void OnAudioDeviceRecordLevel(int level)
        {
            // 处理麦克风测试音量回调
        }   
    };
    
    // 创建SDK实例及设备测试实例
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(listener, "");
    DeviceTestEventListener* deviceTestListener = new DeviceTestEventListener();
    AliMediaDeviceTestInterface *pTestInterface = pEngine->createMediaDeviceTestInterface(deviceTestListener);
    ```

2.  开始测试前，通过接口`getAudioCaptures`获取当前设备上所有可用麦克风设备，返回设备列表中将同时返回设备ID及设备名称，应用层可选择通过设备名或设备ID判断并选择需要测试的设备。

    ```
    AliRtcDeviceList audioCaptureList;
    pEngine->getAudioCaptures(audioCaptureList);
    
    #if defined(USE_DEVIC_NAME)
    // 可以通过遍历所有麦克风设备名，查找需要测试的设备
    std::string matchDeviceName = /*测试设备名*/;
    for (size_t i = 0; i != audioCaptureList.deviceNames.size(); ++i)
    {
        AliRtc::String deviceName = audioCaptureList.deviceNames.at(i);
        matchDeviceName = ...  
    }
    #else
    // 可以通过遍历所有麦克风设备ID，查找需要测试的设备
    std::string matchDeviceId = /*测试设备ID*/;
    for (size_t i = 0; i != audioCaptureList.deviceIds.size(); ++i)
    {
        AliRtc::String deviceId = audioCaptureList.deviceIds.at(i);
        matchDeviceId = ...  
    }
    #endif
    ```

3.  选中测试设备后，调用麦克风测试接口启动测试，接口中需要指明测试设备名称或者设备ID，以及音量回调频率（传入0为默认频率，每20ms回调一次音量）。测试开始后，提示您对麦克风设备说话，并将`OnAudioDeviceRecordLevel`回调中返回的采集音量值进行展示，判断当前麦克风设备是否正常工作。

    ```
    // 启动麦克风设备测试
    #if defined(USE_DEVIC_NAME)
    pTestInterface->StartTestAudioRecord(matchDeviceName.c_str(), 0);
    #else
    pTestInterface->StartTestAudioRecordById(matchDeviceName.c_str(), 0); 
    #endif
    ```

4.  测试完成后，调用接口`StopTestAudioRecord`停止麦克风测试，并释放设备测试功能实例。

    ```
    pTestInterface->StopTestAudioRecord();
    pTestInterface->Release();
    pTestInterface = nullptr;
    ```


## 扬声器测试

1.  创建SDK引擎实例后，应用层需要继承`AliMediaDeviceTestEventListener`接口，实现`OnAudioDevicePlayoutLevel`回调，用于接收扬声器测试时返回的音量值，同时实现`OnAudioDevicePlayoutEnd`回调，用于接收播放文件结束事件。然后通过SDK接口`createMediaDeviceTestInterface`创建设备测试实例，并在创建时传入回调监听实例。

    ```
    // 继承实现设备测试事件回调
    class DeviceTestEventListener : public AliMediaDeviceTestEventListener
    {
    public:
        virtual void OnAudioDevicePlayoutLevel(int level)
        {
            // 处理扬声器测试音量回调
        }
    
        virtual void OnAudioDevicePlayoutEnd()
        {
            // 处理扬声器测试播放结束事件
        }
    };
    
    // 创建SDK实例及设备测试实例
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(listener, "");
    DeviceTestEventListener* deviceTestListener = new DeviceTestEventListener();
    AliMediaDeviceTestInterface *pTestInterface = pEngine->createMediaDeviceTestInterface(deviceTestListener);
    ```

2.  开始测试前，通过接口`getAudioCaptures`获取当前设备上所有可用扬声器，返回设备列表中将同时返回设备ID及设备名称，应用层可选择通过设备名或设备ID判断并选中需要测试的设备。

    ```
    AliRtcDeviceList audioRenderList;
    pEngine->getAudioRenderers(audioRenderList);
    
    #if defined(USE_DEVIC_NAME)
    // 可以通过遍历所有麦克风设备名，查找需要测试的设备
    std::string matchDeviceName = /*测试设备名*/;
    for (size_t i = 0; i != audioRenderList.deviceNames.size(); ++i)
    {
        AliRtc::String deviceName = audioRenderList.deviceNames.at(i);
        matchDeviceName = ...  
    }
    #else
    // 也可以通过遍历所有麦克风设备ID，查找需要测试的设备
    std::string matchDeviceId = /*测试设备ID*/;
    for (size_t i = 0; i != audioRenderList.deviceIds.size(); ++i)
    {
        AliRtc::String deviceId = audioRenderList.deviceIds.at(i);
        matchDeviceId = ...  
    }
    #endif
    ```

3.  选中测试设备后，调用扬声器测试接口启动测试，接口中需要指明测试设备名称或设备ID，音量回调频率（传入0为默认频率，每20ms回调一次音量），以及测试使用的音频文件路径。开始测试后，可以将`OnAudioDevicePlayoutLevel`回调中返回的采集音量值进行展示，同时关注扬声器中播放的测试音频，判断当前扬声器设备是否正常工作。

    ```
    // 启动麦克风设备测试
    #if defined(USE_DEVIC_NAME)
    pTestInterface->StartTestAudioPlayout(matchDeviceName.c_str(), 0, wavPath.c_str());
    #else
    pTestInterface->StartTestAudioPlayoutById(matchDeviceId.c_str(), 0, wavPath.c_str());
    #endif
    ```

    **说明：** 目前扬声器测试播放文件只支持Wave格式，传入路径需要为绝对路径，并保证可以被读取访问。

4.  测试完成或接收到文件播放结束事件回调后，调用`StopTestAudioRecord`接口停止麦克风测试，并释放设备测试功能实例。

    ```
    pTestInterface->StopTestAudioPlayout();
    pTestInterface->Release();
    pTestInterface = nullptr;
    ```


