# iOS

阿里云RTC为您提供了输入外部音视频流的功能。通过阅读本文，您可以了解输入外部音视频流的方法。

## 输入外部视频流

**说明：** SDK允许先推流然后开启外部视频输入，但这种情况下，默认开始推流时，先推送出的是本地原始采集源（摄像头或屏幕捕获）的视频数据，直到启用外部输入。

1.  调用[setExternalVideoSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)打开外部视频输入开关。

    ```
    int ret = [self.engine setExternalVideoSource:YES useTexture:NO sourceType:AliRtcVideosourceCameraLargeType renderMode:AliRtcRenderModeAuto];
    ```

2.  调用[pushExternalVideoFrame](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)输入视频数据。

    **说明：**

    -   此处需要重新开启线程调用pushExternalVideoFrame。
    -   视频流类型仅支持AliRtcVideosourceCameraLargeType（大分辨率视频流）。
    ```
    float pcmHzFloat;
    int yuvDataWidth;
    int yuvDataHeight;
    NSThread * yuvInputThread;
    FILE * yuvInputFile;
    
    - (void)inputYUVRun {
    
        int width = yuvDataWidth;
        int height = yuvDataHeight;
        int dataSize = width*height*3/2;
    
        char *yuv_read_data = (char *)malloc(dataSize);
    
        while (true) {
    
            if ([yuvInputThread isCancelled]) {
                break;
            }
    
            size_t read = fread(yuv_read_data,dataSize, 1, yuvInputFile);
    
            if (read > dataSize) {
                break;
            }
            if (read == 0) {
    
                fseek(yuvInputFile, 0,SEEK_SET);
                NSLog(@"input yuv reset head!");
                if (yuvInputThread) {
                    continue;
                } else {
                    break;
                }
            }
    
            bool push_error = false;
    
            while (true) {
    
                if (![yuvInputThread isExecuting]) {
                    push_error = YES;
                    break;
                }
    
                AliRtcVideoDataSample *dataSample = [[AliRtcVideoDataSample alloc] init];
                dataSample.dataPtr = (long)yuv_read_data;
                dataSample.format = AliRtcVideoFormat_I420;
                dataSample.width = width;
                dataSample.height = height;
                dataSample.strideY = width;
                dataSample.strideU = width/2;
                dataSample.strideV = width/2;
                dataSample.dataLength = dataSample.strideY * dataSample.height * 3/2;
    
                //加判断是否开启输入屏幕共享
                int ret = 0;
                if (yuvShareState != YES) {
                } else {
                    ret = [self.engine pushExternalVideoFrame:dataSample sourceType:AliRtcVideosourceScreenShareType];
                }
    
                if (ret == AliRtcErrAudioBufferFull &&
                    [yuvInputThread isCancelled] == NO) {
    
                } else {
                    if (ret < 0) {
                        push_error = true ;
                    }
                }
    
                //加判断频率, 默认为60hz(30毫秒)
                if (pcmHzFloat > 0) {
                    float hz = 1.0/pcmHzFloat;
                    [NSThread sleepForTimeInterval:hz];   // 指定频率
                } else {
                    [NSThread sleepForTimeInterval:0.03];   // 默认30毫秒 (加延迟操作播放出流畅的画面)
                }
    
                break;
            }
    
            if (push_error) {
                break ;
            }
        }
    
        free(yuv_read_data);
    
        fclose(yuvInputFile);
        yuvInputFile = NULL ;
    }
    ```


## 输入外部音频流

1.  调用[setExternalAudioSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)启用外部音频输入，并调用[setMixedWithMic](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)设置外部音频输入是否与麦克风混合。

    ```
    int ret = [self.engine setExternalAudioSource:YES withSampleRate:pcmSampleRate channelsPerFrame:pcmChannels];
    
    // 完全替代麦克风采集
    [self.engine setMixedWithMic:NO];
    ```

2.  调用[pushExternalAudioFrameRawData](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)输入音频数据。

    **说明：** 如果返回值为AliRtcErrAudioBufferFull，表示当前buffer队列饱和，建议您等待20ms，再继续输送数据。

    ```
    int pcmSampleRate;
    int pcmChannels;
    NSThread * pcmInputThread;
    FILE * pcmInputFile;
    
    - (void)inputPCMRun {
    
        // 40ms
        int readbufSize = (pcmSampleRate/100)*4*sizeof(int16_t)*pcmChannels ;
    
        while (true) {
    
            if ([pcmInputThread isCancelled]) {
                break;
            }
    
            size_t read = fread(pcmData, 1, readbufSize, pcmInputFile) ;
    
            if (read > readbufSize) {
                break;
            }
            if (read == 0) {
                fseek(pcmInputFile, 0, SEEK_SET) ;
                NSLog(@"input pcm reset head!");
                if (pcmInputThread) {
                    continue;
                } else {
                    break;
                }
            }
    
            bool push_error = false;
    
            while (true) {
                if (![pcmInputThread isExecuting]) {
                    push_error = YES;
                    break;
                }
    
                int rc = [self.engine pushExternalAudioFrameRawData:pcmData samples:read timestamp:0];
    
                if ( rc == AliRtcErrAudioBufferFull && [pcmInputThread isCancelled ] == NO ) {
                    [NSThread sleepForTimeInterval:0.08] ;
                } else {
                    if (rc < 0) {
                        push_error = true ;
                    }
    
                    break;
                }
    
            }
    
            if (push_error) {
                break;
            }
        }
    
        fclose(pcmInputFile);
        pcmInputFile = NULL ;
    }
    ```


