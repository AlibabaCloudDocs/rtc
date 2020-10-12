# Windows

通过本文，您可以了解Windows端语音数据处理的功能介绍。

## 场景

语音识别

阿里云的语音识别指的是将本地发布端或订阅端的音频数据转化为文字，实现流程如下：

1.  阿里云RTC会将音频数据发送至音频识别SDK中。
2.  音频识别SDK将音频数据发送至音频识别服务进行实时语音处理并返回识别结果。
3.  音频识别SDK为用户提供识别结果。

详细请参见[智能语音交互](https://help.aliyun.com/document_detail/84428.html)。

方案架构图

![方案架构图](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8159101061/p162782.png)

## 调用时序图

![调用时序图](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8159101061/p162783.png)

## 接口及使用

通过继承AliRtcEventListener回调类，实现[onAudioSampleCallback](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调接收音频媒体数据，并根据业务场景使用相应的数据源。

onAudioSampleCallback：订阅的音频数据回调。

|参数|类型|描述|
|--|--|--|
|type|[AliRtcAudioSource](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频源类型|
|audioSample|[AliRtcAudioDataSample \*](/cn.zh-CN/SDK参考/Windows SDK/数据类型.md)|音频数据|

AliRtcAudioSource：音频裸数据源类型。

|枚举名|描述|
|---|--|
|AliRtcAudiosourceRawData|本地采集的原始音频数据。|
|AliRtcAudiosourcePub|经过音频3A处理后的音频数据。|
|AliRtcAudiosourceSub|当前订阅到的远端用户混音后的音频数据。|

## 语音数据处理

RTC获取音频数据方式如下：

1.  应用在创建AliRtcEngine引擎实例之后，注册音频数据回调。

    **说明：** 指定参数AliAudioType输出指定的音频数据类型（类型参见下一步骤说明）。

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
2.  注册音频数据回调，通过audioSample参数指明当前回调音频数据类型。

    **说明：** 如果需要输出多种类型数据，需要分别调用注册。注册完成后，音频数据将通过AliAudioObserver持续回调。

    音频数据通过回调中audioSample参数返回，数据格式为PCM数据，目前SDK支持输出不同环节的音频数据，回调中通过type参数指定当前回调音频数据类型。

    ```
    // AliRtcAudioDataSample音频媒体数据结构
    typedef struct tagAliRtcAudioDataSample { unsigned char *data{nullptr}; //音频数据 
    int numOfSamples{0}; //采样数 
    int bytesPerSample{0}; //采样位数（字节）
    int numOfChannels{0}; //声道数 
    int samplesPerSec{0}; //采样率 
    
    // 接收并处理音频数据回调 
    void void onAudioSampleCallback(AliRtcAudioSource type, AliRtcAudioDataSample *audioSample) {};
    ```

3.  需要停止接收视频裸数据时，调用接口unsubscribeAudioData关闭音频数据输出。

    **说明：** 停止类型需要对应步骤一中注册输出的音频数据类型。

    ```
    // 停止本地采集音频数据输出
    pEngine->unsubscribeAudioData(AliRtcAudiosourceRawData);
    ```


语音服务操作，详细请参见：[智能语音交互](https://help.aliyun.com/document_detail/84428.html)。

