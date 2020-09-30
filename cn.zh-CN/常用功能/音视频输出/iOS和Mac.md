# iOS和Mac

本文为您介绍了iOS和Mac端音视频输出功能调用接口的具体步骤。

## 订阅音频裸数据

1.  设置入会模式为音乐模式。

    接口方法：

    ```
    + (instancetype)sharedInstance:(id<AliRtcEngineDelegate>)delegate extras:(NSString *)extras;
    ```

    通过设置extras参数来控制是否为音乐模式。

    ```
    {
      "user_specified_scene_mode" : "SCENE_MUSIC_MODE",
    }
    ```

    **说明：** extras为json字符串，如果当前使用了其他key值的extras配置，可以共存。

    音乐模式示例代码如下所示。

    ```
    NSMutableDictionary *extrasDic = [[NSMutableDictionary alloc] init];
    [extrasDic setValue:@"ENGINE_BASIC_QUALITY_MODE" forKey:@"user_specified_engine_mode"];
    [extrasDic setValue:@"SCENE_MUSIC_MODE" forKey:@"user_specified_scene_mode"];
    NSError *parseError = nil;
    NSData *jsonData = [NSJSONSerialization dataWithJSONObject:extrasDic options:NSJSONWritingPrettyPrinted error:&parseError];
    NSString *extras = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];
    
    AliRtcEngine *engine = [AliRtcEngine sharedInstance:self extras:extras];
    ```

2.  获取音频推流裸数据。

    1.  注册音频裸数据。

        接口方法如下：

        ```
        - (void)subscribeAudioData:(AliRtcAudioSource)audioSource;
        ```

        **说明：** 该接口必须在音频流发布成功之后调用才能生效；调用此接口后，即可开始订阅音频裸数据，裸数据通过回调接口返回。

        参数说明如下：

        |参数|说明|
        |--|--|
        |AliRtcAudioSource|AliRtcAudiosourcePub：推流端数据AliRtcAudiosourceSub：拉流端数据 |

        如果您想停止获取音频裸数据，调用以下接口：

        ```
        - (void)unSubscribeAudioData:(AliRtcAudioSource)audioSource;
        ```

    2.  通过回调获取对应的音频裸数据。

        回调接口如下：

        ```
        - (void)onAudioSampleCallback:(AliRtcAudioSource)audioSource audioSample:(AliRtcAudioDataSample *)audioSample;
        ```

        **说明：** 调用subscribeAudioData接口后，通过此回调获取对应的音频裸数据。

        AliRtcAudioDataSample参数说明如下：

        |参数|说明|
        |--|--|
        |dataPtr|裸数据data|
        |numOfSamples|音频样本点数|
        |bytesPerSample|量化位数|
        |numOfChannels|声道数|
        |samplesPerSec|采样率|

    3.  推流音频裸数据写入本地pcm文件。

        ```
        {
        // 开始订阅（在音频流publish成功之后）
        [self.engine subscribeAudioData:(AliRtcAudiosourcePub)];
        }
        ```

        ```
        // 订阅的音频数据回调
        - (void)onAudioSampleCallback:(AliRtcAudioSource)audioSource audioSample:(AliRtcAudioDataSample *)audioSample {
        
            if (audioSample.dataPtr == 0) {
                //没有音频订阅数据
                return;
            }
        
            if (audioSource == AliRtcAudiosourcePub) {
                // pub数据回调
            }
        
            // 获取buffer 和 bufferSize
            int bufferSize = audioSample.numOfSamples * audioSample.bytesPerSample * audioSample.numOfChannels;
            void *audioSampleBufferPtr = NULL;
        
            if(bufferSize) {
                audioSampleBufferPtr = malloc(bufferSize);
                if(audioSampleBufferPtr) {
                    memcpy(audioSampleBufferPtr, (void *)audioSample.dataPtr, bufferSize);
                }
            }
        
            // 写入文件（此处省略FILE对象的初始化和销毁等，请写在外部）    
            fwrite(audioSampleBufferPtr, 1, bufferSize, file);
        
            if (audioSampleBufferPtr) {
                free(audioSampleBufferPtr);
                audioSampleBufferPtr = NULL;
            }
        }
        ```


## 订阅视频裸数据

1.  注册视频裸数据。

    接口方法如下：

    ```
    - (void)registerVideoSampleObserver;
    ```

    **说明：** 调用此接口后，即可开始订阅视频裸数据，裸数据通过回调接口给出。

    如果想停止获取音频裸数据，调用以下接口：

    ```
    - (void)unregisterVideoSampleObserver;
    ```

2.  通过回调获取视频裸数据。

    回调接口方法如下：

    ```
    /**
    * @brief 订阅的本地采集视频数据回调
    * @param videoSource video source
    * @param videoSample video sample
    */
    - (void)onCaptureVideoSample:(AliRtcVideoSource)videoSource videoSample:(AliRtcVideoDataSample *)videoSample;
    
    /**
    * @brief 订阅的远端视频数据回调
    * @param uid user id
    * @param videoSource video source
    * @param videoSample video sample
    */
    - (void)onRemoteVideoSample:(NSString *)uid videoSource:(AliRtcVideoSource)videoSource videoSample:(AliRtcVideoDataSample *)videoSample;
    ```

    **说明：** 调用registerVideoSampleObserver接口后，通过这两个回调获取对应的视频裸数据。

    -   onCaptureVideoSample为预览数据回调，在开始预览之后可收到数据流。
    -   onRemoteVideoSample为拉流数据回调，subscribe拉流成功后可收到数据流。
3.  预览视频裸数据写入本地yuv文件。

    ```
    {
    // 开始订阅
    [_engine registerVideoSampleObserver];
    }
    ```

    ```
    - (void)onCaptureVideoSample:(AliRtcVideoSource)videoSource videoSample:(AliRtcVideoDataSample *)videoSample {
    
        [self dumpVideoYuvData:@"" videoSource:videoSource videoSample:videoSample];
    }
    
    - (void)onRemoteVideoSample:(NSString *)uid videoSource:(AliRtcVideoSource)videoSource videoSample:(AliRtcVideoDataSample *)videoSample {
        [self dumpVideoYuvData:uid videoSource:videoSource videoSample:videoSample];
    }
    
    - (void)dumpVideoYuvData:(NSString *)uid videoSource:(AliRtcVideoSource)videoSource videoSample:(AliRtcVideoDataSample *)videoSample {
        //创建串行队列
           dispatch_queue_t testqueue = dispatch_queue_create("subVideo", NULL);
    
           //同步执行任务
           dispatch_sync(testqueue, ^{
               if(_dumpYUVVideoData || _remoteYUVVideoData){
    
                   if (videoSource != AliRtcVideosourceCameraLargeType) {
                       return;
                   }
    
                   if (!_subDataMutableDic[uid]) {
                       NSString *time = [self getCurrentTimes];
    
                       NSString *filePath = [NSString stringWithFormat:@"Documents/yuv/%@/",uid];
                       if ([uid isEqualToString:@""]) {
                           filePath = [NSString stringWithFormat:@"Documents/yuv/self/"];
                       }
    
                       NSString *fileName = [NSString stringWithFormat:@"sub_%@_video_%d*%d_%@.yuv",uid,videoSample.width,videoSample.height,time];
                       if ([uid isEqualToString:@""]) {
                           fileName = [NSString stringWithFormat:@"pub_%@_video_%d*%d_%@.yuv",uid,videoSample.width,videoSample.height,time];
                       }
    
                       NSString * dataPath = [SubFilePath getSubDataFilePath:filePath FileName:fileName];
    
                       subYUVFile = fopen([dataPath UTF8String], "ab");
    
                       SubDataModel *cache = [[SubDataModel alloc] init];
                       cache.filePath = dataPath;
                       cache.outputFile = subYUVFile;
                       [_subDataMutableDic setObject:cache forKey:uid];
                   }
    
                   SubDataModel *cache = _subDataMutableDic[uid];
                   subYUVFile = cache.outputFile;
    
                   uint8_t *outputData = NULL;
                   int32_t w = videoSample.width;
                   int32_t h = videoSample.height;
    
                   if (outputData == NULL) {
                       outputData = (uint8_t*)malloc(w*h*3/2);
                   }
    
                   if(videoSample.type == AliRtcBufferType_Raw_Data) {
    
                       if(videoSample.dataYPtr && videoSample.dataUPtr &&  videoSample.dataVPtr) {
                           memcpy(outputData, (uint8_t*)videoSample.dataYPtr,w*h*3/2);
                           memcpy(outputData + w*h, (uint8_t*)videoSample.dataUPtr, w*h/4);
                           memcpy(outputData + w*h*5/4, (uint8_t*)videoSample.dataVPtr, w*h/4);
                       }
    
                   }else if(videoSample.type == AliRtcBufferType_CVPixelBuffer) {
                       if(videoSample.pixelBuffer) {
                           CVPixelBufferRef newBuffer = videoSample.pixelBuffer;
                           if(newBuffer) {
                               CVReturn cvRet = CVPixelBufferLockBaseAddress(newBuffer, 0);
                                if ( cvRet != kCVReturnSuccess ) {
                                    return;
                                }
                                void*  src_y = CVPixelBufferGetBaseAddressOfPlane(newBuffer, 0);
                                void*  src_uv = CVPixelBufferGetBaseAddressOfPlane(newBuffer, 1);
    
                                size_t src_y_stride = CVPixelBufferGetBytesPerRowOfPlane(newBuffer, 0);
                                size_t src_uv_stride = CVPixelBufferGetBytesPerRowOfPlane(newBuffer, 1);
    
                                uint8_t *destData = outputData;
    
                                for (int row = 0; row < h; ++row) {
                                    memcpy(destData, (uint8_t*)src_y + row * src_y_stride,w);
                                    destData += w;
                                }
    
                                for (int row = 0; row < (h + 1) / 2; ++row) {
                                    memcpy(destData, (uint8_t*)src_uv + row * src_uv_stride,w);
                                    destData += w;
                                }
    
                                CVPixelBufferUnlockBaseAddress(newBuffer, 0);
                           }
                       }
                   }
    
                   fwrite(outputData, 1, w*h*3/2, subYUVFile);
    
                   if (outputData) {
                       free(outputData);
                       outputData = NULL;
                   }
               }
           });
    }
    ```


