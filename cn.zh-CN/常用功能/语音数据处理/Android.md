# Android

通过本文，您可以了解Android端语音数据处理的功能介绍。

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

通过调用接口[registerAudioObserver](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)注册音频数据回调，注册时通过[AliAudioType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)参数指明当前回调音频数据类型。使用音频回调[AliAudioObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)接收音频媒体数据。并根据业务场景使用相应的数据源。

AliAudioObserver：音频数据回调。

|API|描述|以上版本支持|
|---|--|------|
|[onCaptureRawData](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|音频原始数据|1.17|
|[onCaptureData](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|本地推流音频数据|1.17|
|[onRenderData](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|远端音频数据|1.17|

AliAudioType：音频类型枚举。

|枚举名|描述|
|---|--|
|PUB\_OBSERVER|经过音频3A处理后的音频数据|
|SUB\_OBSERVER|当前订阅到的远端用户混音后的音频数据|
|RAW\_DATA\_OBSERVER|本地采集的原始音频数据|

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
    -   音频类型枚举AliAudioType中的VOLUME\_DATA\_OBSERVER类型为注册用户音量值回调，目前已经废弃，从1.16版本开始请您使用registerAudioVolumeObserver接口。
2.  注册音频数据回调，通过AliAudioType参数指明当前回调音频数据类型。

    **说明：** 如果需要输出多种类型数据，需要分别调用注册。注册完成后，音频数据将通过AliAudioObserver持续回调。

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

3.  需要停止接收视频裸数据时，调用接口unRegisterAudioObserver关闭音频数据输出。

    **说明：** 停止类型需要对应步骤一中注册输出的音频数据类型。

    ```
    // 停止本地采集音频数据输出，停止类型需要对应步骤2中注册输出的音频数据类型AliAudioType
    pEngine->unRegisterAudioObserver(type);
    ```


语音服务操作，详细请参见：[智能语音交互](https://help.aliyun.com/document_detail/84428.html)。

