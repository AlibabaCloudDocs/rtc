# Windows

本文为您介绍Windows端音视频输出功能调用接口的具体步骤。

## 输出视频媒体

1.  当应用需要输出视频媒体数据时，需先继承AliRtcEventListener接口，实现onCaptureVideoSample和onRemoteVideoSample回调，用于接收本地采集视频裸数据，以及订阅到的远端视频裸数据。

    ```
    //接收裸数据回调 
    void onCaptureVideoSample(AliRtcVideoSource videoSource, AliRtcVideoDataSample *videoSample) {
    //处理本地采集视频数据 
    }
    void onRemoteVideoSample(const AliRtc::String &uid, AliRtcVideoSource videoSource, AliRtcVideoDataSample *videoSample) { 
    //处理远端视频数据
    }
    ```

    **说明：** 目前Windows端数据输出只支持输出YUV（I420）格式数据，应用侧可通过SDK提供的AliConvertVideoData静态接口，转换到RGBA格式。

2.  应用在创建AliRtcEngine引擎实例之后，调用接口registerVideoSampleObserver注册视频裸数据输出，注册后开启预览或订阅拉流时，视频数据将通过onCaptureVideoSample和onRemoteVideoSample持续回调。

    ```
    AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
    // 注册视频裸数据输出
    pEngine->registerVideoSampleObserver();
    //开始预览/推流及订阅其他用户视频
    .....
    ```

    **说明：** 本地采集视频数据需要在开启摄像头（打开预览或推送视频流）前提下才会有回调输出，远端视频数据同样需要在订阅其他用户的视频流成功后才会有回调输出。

3.  需要停止接收视频裸数据时，调用接口unRegisterVideoSampleObserver关闭视频裸数据输出即可。

    ```
    // 停止视频裸数据输出
    pEngine->unRegisterVideoSampleObserver();
    ```


## 输出音频媒体

1.  当应用需要输出音频媒体数据时，首先需要先继承AliRtcEventListener接口，实现onAudioSampleCallback回调，用于接收音频媒体数据。

    音频数据通过回调中audioSample参数返回，数据格式为PCM数据，目前SDK支持输出不同环节的音频数据，回调中通过type参数指明当前回调音频数据类型。

    具体含义如下：

    -   AliRtcAudiosourceRawData：本地采集的原始音频数据。
    -   AliRtcAudiosourcePub：经过音频3A处理后的音频数据。
    -   AliRtcAudiosourceRawData：当前订阅到的远端用户混音后的音频数据。
    ```
    // 音频媒体数据结构 
    typedef struct tagAliRtcAudioDataSample { unsigned char *data{nullptr}; 
    //音频数据 int numOfSamples{0}; 
    //采样数 int bytesPerSample{0}; 
    //采样位数（字节）int numOfChannels{0}; 
    //声道数 int samplesPerSec{0}; 
    //采样率 }AliRtcAudioDataSample;
    // 接收并处理音频数据回调 void void onAudioSampleCallback(AliRtcAudioSource type, AliRtcAudioDataSample *audioSample) {
    };
    ```

2.  应用在创建AliRtcEngine引擎实例之后，注册音频数据回调，其中参数AliAudioType指定需要输出的音频数据类型（类型参见上一步骤说明），如果需要输出多种类型数据，需要分别调用注册。注册完成后，音频数据将通过AliAudioObserver持续回调。

    ```
    AliRtcEngine mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());    
    // 开始本地采集音频数据输出(type输出其他类型参见枚举AliAudioType)
    mAliRtcEngine.registerAudioObserver(type,
                    new AliRtcEngine.AliAudioObserver() {
                        @Override
                        public void onCaptureRawData(long dataPtr, int numSamples, int bytesPerSample, int numChannels, int sampleRate, int samplesPerSec) {
                        }
    
                        @Override
                        public void onCaptureData(long dataPtr, int numSamples, int bytesPerSample, int numChannels, int sampleRate, int samplesPerSec) {
                        }
    
                        @Override
                        public void onRenderData(long dataPtr, int numSamples, int bytesPerSample, int numChannels, int sampleRate, int samplesPerSec) {
    
                        }
                    });
    
    // 开始音频推流及订阅其他用户视频
    .....
    ```

    **说明：**

    -   本地采集音频数据需要在开启麦克风（开始推送音频流）前提下才会有回调输出，远端视频数据同样需要在订阅其他用户的音频流成功后才会有回调输出。
    -   音频类型枚举AliRtcAudioSource中的AliRtcAudioSourceVolume类型为注册用户音量值回调，注册订阅该类型时，用户音量将通过onAudioVolumeCallback回调返回，与音频数据输出回调不同。
3.  需要停止接收视频裸数据时，调用接口unsubscribeAudioData关闭音频数据输出，停止类型需要对应步骤2中注册输出的音频数据类型。

    ```
    // 停止本地采集音频数据输出
    pEngine->unsubscribeAudioData(AliRtcAudiosourceRawData);
    ```


