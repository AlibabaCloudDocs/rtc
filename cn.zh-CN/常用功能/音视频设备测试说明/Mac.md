# Mac

RTC SDK为您提供音视频设备测试的方法，您可以在音视频通话前检查当前设备上的摄像头，麦克风以及扬声器等音视频设备是否正常工作，以保证音视频通话质量。通过阅读本文，您可以了解音视频设备测试的方法。

## 摄像头测试

1.  创建SDK实例后，应用层可以调用接口`getCameraList`获取当前设备上所有可用摄像头，返回设备列表中包含设备ID及设备名称，应用层可选择通过设备名称或设备ID进行判断，并通过接口`setCurrentCamera`或`setCurrentCameraWithID`选中需要测试的设备。

    ```
    NSArray *camList = [self.engine getCameraList];
    
    // 设备名称
    NSString *matchDeviceName = /*测试设备名*/;
    int camCount = (int)camList.count;
    for(int i=0; i<camCount; i++) {
        AliRtcDeviceInfo *deviceInfo = [camList objectAtIndex:i];
        NSString *name = deviceInfo.deviceName;
        if ([name isEqualToString:matchDeviceName]) {
            [self.engine setCurrentCamera:matchDeviceName];
        }
    }
    
    // 设备ID
    NSString *matchDeviceId = /*测试设备ID*/;
    int camCount = (int)camList.count;
    for(int i=0; i<camCount; i++) {
        AliRtcDeviceInfo *deviceInfo = [camList objectAtIndex:i];
        NSString *deviceID = deviceInfo.deviceId;
        if ([deviceID isEqualToString:matchDeviceId]) {
            [self.engine setCurrentCameraWithID:matchDeviceId];
        }
    }
    ```

2.  设置测试摄像头设备之后，通过setLocalViewConfig接口可以设置预览显示窗口，再启动预览，即可通过预览画面是否正常显示，判断当前摄像头设备是否正常工作。

    ```
    // 设置预览窗口
    AliVideoCanvas *canvas = [[AliVideoCanvas alloc] init];
    canvas.renderMode = renderMode;
    canvas.view = (AliRenderView *)view;
    canvas.mirrorMode = mirrorMode;
    [self.engine setLocalViewConfig:canvas forTrack:AliRtcVideoTrackCamera];
    [self.engine startPreview];
    ```


## 麦克风测试

1.  开始测试前，通过接口`getAudioCaptures`获取当前设备上所有可用麦克风设备，返回设备列表中将同时返回设备ID及设备名称，应用层可选择通过设备名称调用接口`startTestAudioRecordWithName`进行麦克风测试，测试开始后会收到`onAudioDeviceRecordLevel`回调，接收麦克风测试时返回的音量值。

    ```
    // 开始测试
    NSArray *audioList = [self.engine getAudioCaptures];
    AliRtcDeviceInfo *deviceInfo = audioList[0];
    [self.engine startTestAudioRecordWithName:deviceInfo.deviceName];
    
    // 回调
    - (void)onAudioDeviceRecordLevel:(int)level {
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"麦克风音量值:%d", level);
        });
    }
    ```

2.  测试完成后，调用接口stopTestAudioRecord停止麦克风测试。

    ```
    [self.engine stopTestAudioRecord];
    ```


## 扬声器测试

1.  开始测试前，通过接口`getAudioRenderers`获取当前设备上所有可用扬声器设备，返回设备列表中将同时返回设备ID及设备名称，应用层可选择通过设备名称调用接口`startTestAudioPlayoutWithName`进行扬声器测试，测试开始后会收到`onAudioDevicePlayoutLevel`回调，接收扬声器测试时返回的音量值。

    ```
    // 开始测试
    NSArray *speakerList = [self.engine getAudioRenderers];
    AliRtcDeviceInfo *deviceInfo = speakerList[0];
    [self.engine startTestAudioPlayoutWithName:deviceInfo.deviceName filePath:path loopCycles:0];
    
    // 回调
    - (void)onAudioDevicePlayoutLevel:(int)level {
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"扬声器音量值:%d", level);
        });
    }
    ```

    **说明：** 目前扬声器测试播放文件只支持Wave格式，传入路径需要为绝对路径，并保证可以被读取访问。

2.  测试完成或接收到文件播放结束事件回调后，调用stopTestAudioPlayout接口停止扬声器测试。

    ```
    [self.engine stopTestAudioPlayout];
    ```


