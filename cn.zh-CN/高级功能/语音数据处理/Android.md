# Android

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

通过调用接口[registerAudioObserver](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)注册音频数据回调，注册时通过[AliAudioType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)参数指明当前回调音频数据类型；使用音频回调[AliAudioObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)接收音频媒体数据，并根据业务场景使用相应的数据源。

registerAudioObserver：注册音频数据回调。

```
public abstract void registerAudioObserver(AliRtcEngine.AliAudioType audioType, AliRtcEngine.AliAudioObserver audioObserver);
```

参数说明

|名称|类型|描述|
|--|--|--|
|audioType|[AliAudioType](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|回调音频数据的类型。|
|audioObserver|[AliAudioObserver](/cn.zh-CN/SDK参考/Android SDK/回调及监听.md)|音频数据回调接口。|

## 语音数据处理

RTC获取音频数据方式如下：

1.  应用在创建AliRtcEngine引擎实例之后，调用接口registerAudioObserver注册音频数据回调，更多信息，请参见[registerAudioObserver](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)。

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
    -   音频类型枚举AliAudioType中的VOLUME\_DATA\_OBSERVER类型为注册用户音量值回调，目前已经废弃，从1.16版本开始请使用[registerAudioVolumeObserver](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)接口替代。
2.  需要停止接收视频裸数据时，调用接口[unRegisterAudioObserver](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)关闭音频数据输出。

    **说明：** 停止类型需要对应[步骤 1](#step_466_xaf_vmv)中注册输出的音频数据类型。

    ```
    // 停止本地采集音频数据输出，停止类型需要对应步骤2中注册输出的音频数据类型AliAudioType
    pEngine->unRegisterAudioObserver(type);
    ```


