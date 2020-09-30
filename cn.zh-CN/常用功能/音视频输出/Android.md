# Android

本文为您介绍Android端音视频输出功能调用接口的具体步骤。

## 输出视频媒体

1.  当应用需要输出视频媒体数据时，需先注册AliVideoObserver回调，实现onLocalVideoSample和onRemoteVideoSample回调，用于接收本地采集视频裸数据，以及订阅到的远端视频裸数据。

    ```
    //接收本地数据回调 void onLocalVideoSample(AliVideoSourceType sourceType, AliVideoSample videoSample); 
    //接收远端数据回调 void onRemoteVideoSample(String callId, AliVideoSourceType sourceType, AliVideoSample videoSample);
    ```

    **说明：** 目前Android端数据输出默认本地数据回调只支持输出YUV（NV21）格式数据，远端数据只支持输出YUV（I420）。应用侧如果有其他格式需求，您可以自行转换到其他格式。

2.  应用在创建AliRtcEngine引擎实例之后，调用接口registerVideoSampleObserver注册视频裸数据输出，注册后开启预览或订阅拉流时，视频数据将通过onCaptureVideoSample和onRemoteVideoSample持续回调。

    ```
    AliRtcEngine mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
    
    // 注册视频裸数据输出
    mAliRtcEngine.registerVideoSampleObserver(new AliRtcEngine.AliVideoObserver() {
                    @Override
                    public void onLocalVideoSample(AliRtcEngine.AliVideoSourceType sourceType, AliRtcEngine.AliVideoSample videoSample) {
                    }
                    @Override
                    public void onRemoteVideoSample(String callId, AliRtcEngine.AliVideoSourceType sourceType, AliRtcEngine.AliVideoSample videoSample) {
                    }
                });
    
    //开始预览/推流及订阅其他用户视频
    .....
    ```

    **说明：** 本地采集视频数据需要在开启摄像头（打开预览或推送视频流）前提下才会有回调输出，远端视频数据同样需要在订阅其他用户的视频流成功后才会有回调输出。

3.  需要停止接收视频裸数据时，调用接口unRegisterVideoSampleObserver关闭视频裸数据输出即可。

    ```
    // 停止视频裸数据输出
    mAliRtcEngine.unRegisterVideoSampleObserver();
    ```


## 输出音频媒体

1.  当应用需要输出音频媒体数据时，首先需要先注册registerAudioObserver接口，实现AliAudioObserver回调，用于接收音频媒体数据。数据格式为PCM数据，目前SDK支持输出不同环节的音频数据，注册通过AliAudioType参数指明当前回调音频数据类型。

    具体含义如下：

    -   PUBOBSERVER：经过音频3A处理后的音频数据。
    -   SUBOBSERVER：当前订阅到的远端用户混音后的音频数据。
    -   RAWDATAOBSERVER：本地采集的原始音频数据。
    ```
    // AliAudioObserver接口数据回调 
    public interface AliAudioObserver { 
    /* @param dataPtr 音频数据 
    @param numSamples 采样数 
    @param bytesPerSample 采样位数（字节）
    @param numChannels 声道数 
    @param sampleRate 采样率 
    @param samplesPerSec 采样位数（字节）
    */
    void onCaptureRawData(long dataPtr, int numSamples, int bytesPerSample, int numChannels, int sampleRate, int samplesPerSec); 
    void onCaptureData(long dataPtr, int numSamples, int bytesPerSample, int numChannels, int sampleRate, int samplesPerSec); 
    void onRenderData(long dataPtr, int numSamples, int bytesPerSample, int numChannels, int sampleRate, int samplesPerSec); 
    } 
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
    -   音频类型枚举AliAudioType中的VOLUME\_DATA\_OBSERVER类型为注册用户音量值回调，目前已经废弃，从1.16版本开始请您使用registerAudioVolumeObserver接口。
3.  需要停止接收视频裸数据时，调用接口unRegisterAudioObserver关闭音频数据输出，停止类型需要对应步骤2中注册输出的音频数据类型。

    ```
    // 停止本地采集音频数据输出，停止类型需要对应步骤2中注册输出的音频数据类型AliAudioType
    pEngine->unRegisterAudioObserver(type);
    ```


