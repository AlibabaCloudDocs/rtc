# iOS和Mac

RTC SDK提供了获取音频数据的功能，您可以将获取到的语音数据根据实际需求进行处理。通过阅读本文，您可以了解到获取音频数据的方法。

## 使用场景

您可以将本地发布端或订阅端的音频数据通过阿里云语音识别服务转换成文字，实现流程如下所示：

1.  阿里云RTC会将音频数据发送至音频识别SDK中。
2.  音频识别SDK将音频数据发送至音频识别服务进行实时语音处理并返回识别结果。
3.  音频识别SDK为用户提供识别结果。

更多信息，请参见[智能语音交互](https://help.aliyun.com/document_detail/84428.html)。

方案架构图

![方案架构图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8159101061/p162782.png)

## 调用时序图

![调用时序图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8159101061/p162783.png)

## 接口及使用

通过调用接口[subscribeAudioData](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)得到回调数据，从回调接口[onAudioSampleCallback](/cn.zh-CN/SDK参考/iOS和Mac SDK/回调及监听.md)获取音频数据，并根据业务场景使用相应的数据源。

onAudioSampleCallback接口参数如下：

|参数|类型|描述|
|--|--|--|
|audioSource|[AliRtcAudioSource](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音频裸数据源类型。|
|audioSample|[AliRtcAudioDataSample \*](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|音频裸数据。|

## 语音数据处理

RTC获取音频数据方式如下：

1.  设置入会模式为音乐模式。

    接口方法：

    ```
    + (instancetype)sharedInstance:(id<AliRtcEngineDelegate>)delegate extras:(NSString *)extras;
    ```

    设置extras参数为音乐模式，更多信息，请参见[extras参数配置说明](/cn.zh-CN/SDK参考/extras参数配置说明.md)。

    ```
    {
      "user_specified_scene_mode" : "SCENE_MUSIC_MODE",
    }
    ```

    **说明：** extras为json字符串，如果当前使用了其他key值的extras配置，可以共存。

    音乐模式示例代码如下所示：

    ```
    NSMutableDictionary *extrasDic = [[NSMutableDictionary alloc] init];
    [extrasDic setValue:@"ENGINE_BASIC_QUALITY_MODE" forKey:@"user_specified_engine_mode"];
    [extrasDic setValue:@"SCENE_MUSIC_MODE" forKey:@"user_specified_scene_mode"];
    NSError *parseError = nil;
    NSData *jsonData = [NSJSONSerialization dataWithJSONObject:extrasDic options:NSJSONWritingPrettyPrinted error:&parseError];
    NSString *extras = [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];
    AliRtcEngine *engine = [AliRtcEngine sharedInstance:self extras:extras];
    ```

2.  获取音频发布端裸数据。

    1.  注册音频裸数据，调用以下接口：

        ```
        - (void)subscribeAudioData:(AliRtcAudioSource)audioSource;
        ```

        **说明：** 该接口必须在音频流发布成功之后调用才能生效。调用此接口后，即可开始订阅音频裸数据，裸数据通过回调接口返回。

    2.  停止获取音频裸数据，调用以下接口：

        ```
        - (void)unSubscribeAudioData:(AliRtcAudioSource)audioSource;
        ```

    3.  通过回调获取对应的音频裸数据，回调接口如下所示：

        **说明：** 调用subscribeAudioData接口后，通过此回调获取对应的音频裸数据。

        ```
        {
        // 开始订阅（在音频流publish成功之后）
        [self.engine subscribeAudioData:(AliRtcAudiosourcePub)];
        }
        
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


