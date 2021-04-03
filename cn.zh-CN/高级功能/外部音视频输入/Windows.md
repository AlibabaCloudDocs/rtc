# Windows

阿里云RTC为您提供了输入外部音视频流的功能。通过阅读本文，您可以了解输入外部音视频流、视频流数据输出以及外部音频输入播放的方法。

## 使用限制

支持Windows SDK 1.16.2及以上版本。

## 使用场景

使用场景包括但不限于以下：

-   需要将本地媒体文件（视频/音频）及第三方音视频数据，通过SDK传输到远端播放渲染，可使用音视频外部输入推流实现。
-   需要在使用音频外部输入的同时，本地播放（耳返）输入内容，可使用外部音频输入播放实现。
-   需要将通信过程中视频数据保存或输出处理（外部渲染，修改内容）时，可使用视频数据裸数据输出实现。

## 输入外部视频数据推流

1.  调用[setExternalVideoSource](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)启用外部视频输入推流。

    **说明：** 目前Windows端不支持texture模式。

2.  应用侧通过接口[configLocalCameraPublish](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)或[configLocalScreenPublish](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)配置指定track推流，然后调用接口[publish](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)开始推视频流。

    **说明：** SDK允许先推流然后开启外部视频输入，即步骤1和步骤2时序对换，但这种情况下，默认开始推流时，先推送出的是原始采集源（摄像头或屏幕捕获）的视频数据，直到启用外部输入。

3.  应用侧持续调用接口[pushExternalVideoFrame](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)，向SDK投递视频裸数据，进行推流，参数frame传入裸数据相关信息，参数sourceType指明推流track类型，与步骤1中设置开启的track类型保持一致。

    **说明：**

    -   投递视频帧数据的频率由应用方控制，依据视频源帧率保持间隔投递，直至输入停止。建议应用侧独立开启线程，进行数据投递，保证数据输入及时性。
    -   目前Windows端支持输入YUV数据（格式I420），需要在参数frame的裸数据信息中，指定format为AliRtcVideoFormatI420， bufferType为AliRtcBufferTypeRawData。
    -   赋值裸数据信息时，需要数据指针、视频宽高信息、stride信息等完整传入；旋转角度rotation目前暂未支持设置，请保持默认值0；时间戳取当期时间，单位为毫秒。
4.  数据源输入结束或应用中止外部视频输入，调用接口[setExternalVideoSource](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)关闭外部视频输入。


代码示例：

```
AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
.....

//1.启用外部视频输入
pEngine->setExternalVideoSource(true, false, AliRtcVideoSourceCamera); //camera track启用外部输入
bPushExternalVideo = true;

//2.配置开始推流
pEngine->configLocalCameraPublish(true);
pEngine->publish();

.....

//3.独立线程推送外部视频数据
int frameRate = 30； // 30 fps
do
{
    size_t frameLength = videoWidth * videoHeight * 3 / 2;
    void* cacheBuf = (void*)malloc(frameLength);

    /*
    从外部数据源拷贝推送视频数据到cacheBuf
    */

    AliRtcVideoDataSample sample;
    sample.data = (unsigned char*)cacheBuf;
    sample.format = AliRtcVideoFormatI420;
    sample.width = videoWidth;
    sample.height = videoHeight;
    sample.strideY = videoWidth;
    sample.strideU = videoWidth / 2;
    sample.strideV = videoWidth / 2;
    sample.dataLen = frameLength;
    sample.rotation = 0;

    pEngine->pushExternalVideoFrame(&sample, AliRtcVideoSourceCamera);

    //控制帧数据投递频率
    Sleep(1000 / frameRate);            
} while (bPushExternalVideo);

.....

//4.停止外部视频输入
pEngine->setExternalVideoSource(false, false, AliRtcVideoSourceCamera);
bPushExternalVideo = false;
```

## 视频裸数据输出

1.  应用需先继承AliRtcEventListener类，实现[onCaptureVideoSample](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)和[onRemoteVideoSample](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)回调，用于接收本地采集视频裸数据，以及订阅到的远端视频裸数据。

    **说明：** 目前Windows端只支持输出YUV（I420）格式数据，可通过SDK提供的AliConvertVideoData静态接口，转换到RGBA格式。

2.  调用接口[registerVideoSampleObserver](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)启动视频裸数据输出，启动后视频数据将通过[onCaptureVideoSample](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)和[onRemoteVideoSample](/cn.zh-CN/SDK参考/Windows SDK/回调及监听.md)持续回调。

    **说明：** 本地采集视频数据需要在开启摄像头（打开预览或正在推送视频流）前提下才会有回调输出，远端视频数据同样需要在订阅其他用户的视频流成功后才会有回调输出。

3.  需要停止接收视频裸数据时，调用接口[unRegisterVideoSampleObserver](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)关闭视频裸数据输出。


代码示例：

```
AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
.....

//1. 注册视频裸数据输出
pEngine->registerVideoSampleObserver();

//开始预览/推流及订阅其他用户视频
.....

//2. 接收裸数据回调
void onCaptureVideoSample(AliRtcVideoSource videoSource, AliRtcVideoDataSample *videoSample)
{
    //处理本地采集数据回调
}

void onRemoteVideoSample(const AliRtc::String &uid, AliRtcVideoSource videoSource, AliRtcVideoDataSample *videoSample)
{
    //处理远端数据回调
}

//3.停止视频裸数据输出
pEngine->unRegisterVideoSampleObserver();
```

## 输入外部音频数据推流

1.  调用接口[setExternalAudioSource](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)启用外部音频输入推流。

    **说明：** 目前仅支持输入音频PCM数据，数据编码为Signed 16-bit。

2.  应用侧通过接口[configLocalAudioPublish](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)配置音频推流，然后调用[publish](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)接口开始推音频流。

    **说明：** SDK允许先推流在开启外部音频输入，即步骤1和步骤2时序对换，但这种情况下，默认开始推流时，先推送出的是麦克风采集音频，直到启用外部输入。

3.  应用侧持续调用[pushExternalAudioFrameRawData](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)接口，向SDK投递音频PCM数据，参数audioSamples带入音频数据地址，参数sampleLength指明音频长度，参数timestamp为当前时间。

    **说明：**

    -   投递音频裸数据的频率由应用方控制，每次投递数据量不要超过240ms的音频数据量，建议每次投递20ms的音频数据，保持循环投递直到结束。当输入数据频率过快，SDK缓存已满暂时无法消费数据时，接口会返回错误码ERR\_AUDIO\_BUFFER\_FULL，此时应用侧需要等待一个数据时间长度后，再次重试投递此数据，直到成功，否则将丢失输入音频数据。
    -   与视频输入一致，同样建议应用侧单独开启线程，投递音频裸数据，直到输入停止。
    -   由于外部输入音频数据的同时，可能同时还有麦克风在采集推流，应用可设置是否需要将外部输入音频与麦克风采集音频混音后一起推出，或单独只推送外部输入音频，通过调用接口[setMixedWithMic](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)可开启或关闭与麦克风采集音频的混音，同时可通过接口[setExternalAudioPublishVolume](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)和[getExternalAudioPublishVolume](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)设置和获取输入音频的混音音量，音量可调整范围为\[0 - 100\]，默认50。
    -   当应用同时推送麦克风采集音频与外部输入音频，接口[muteLocalMic](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)的默认行为是停止所有音频的推送（包括麦克风与外部输入），如果应用只需要停止麦克风音频（保持外部输入音频推送），可通过设置第二个参数 mode，选择AliRtcMuteOnlyMicAudioMode模式即可。
4.  数据源输入结束或应用中止外部音频输入，调用接口[setExternalAudioSource](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)关闭外部视音频输入。


代码示例：

```
AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
.....

//1. 启用外部音频输入播放
unsigned int sampleRate = 44100; //44.1k
unsigned int channelsPerFrame = 1; //单声道
pEngine->setExteranlAudioRender(true, sampleRate, channelsPerFrame); //启用音频输入播放
bRenderExternalAudio = true;

//2.独立线程推送外部音频数据
unsigned int audioDataInterval = 20; //20 ms
size_t bytePerSample = 16 / 8; // Signed 16-bit
size_t dataSize = sampleRate * channelsPerFrame * bytePerSample / (1000 / audioDataInterval);
unsigned int* data = (unsigned int*)malloc(dataSize);

do
{
    /*
    从外部数据源拷贝推送音频数据到data
    */

    std::chrono::milliseconds now = std::chrono::duration_cast<std::chrono::milliseconds>(std::chrono::system_clock::now().time_since_epoch());
    int ret = mpEngine->pushExternalAudioRenderRawData(data, dataSize, sampleRate, channelsPerFrame, now.count());
    if (ret < 0)
    {
        //发生错误，中断播放
        break;
    }

    //返回结果不为0，需要进行错误判断，检查是否缓冲区满
    //返回结果如果为0，投递成功，继续读取并投递数据，无需间隔
    while (ret == ERR_AUDIO_BUFFER_FULL && bRenderExternalAudio)
    {
        Sleep(audioDataInterval); //缓冲区满，间隔一个数据长度后再次重试，直到成功
        if (!bRenderExternalAudio) break;

        ret = mpEngine->pushExternalAudioRenderRawData(data, read_size, sampleRate, channelsPerFrame, now.count());

        if (ret < 0)
        {
            //发生错误，中断推送
            break;
        }
    }
} while (bRenderExternalAudio);

.....

//4.停止外部音频输入播放
mpEngine->setExteranlAudioRender(false, 0, 0);
bRenderExternalAudio = false;
```

## 外部音频输入播放

1.  调用接口[setExteranlAudioRender](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)启用外部音频输入播放，通过参数enable设置开启，通过参数sampleRate和参数channelsPerFrame指定要输入音频数据的采样率和声道数。

    **说明：** 目前仅支持输入音频PCM数据，数据编码为Signed 16-bit，输入播放音频的声道数与采样率，可以在推流过程中动态变更，下一步骤2中，投递接口[pushExternalAudioRenderRawData](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)中可指定当次音频数据的采样率和声道数。

2.  应用侧持续调用[pushExternalAudioRenderRawData](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)接口，向SDK投递音频PCM数据播放，参数audioSamples带入音频数据地址，参数sampleLength指明音频长度，参数sampleRate和参数channelsPerFrame指定要输入音频数据的采样率和声道数，参数timestamp为当前时间戳。

    **说明：** 与外部输入音频数据推送相同，播放音频也需要由应用侧保持频率投递，建议应用侧独立开启线程，进行数据投递，保证数据输入及时性。

3.  数据源输入结束或应用中止音频播放时，调用接口[setExteranlAudioRender](/cn.zh-CN/SDK参考/Windows SDK/AliRtcEngine接口.md)关闭外部音频播放。


代码示例：

```
AliRtcEngine *pEngine = AliRtcEngine::sharedInstance(this, "");
.....

//1. 启用外部音频输入播放
unsigned int sampleRate = 44100; //44.1k
unsigned int channelsPerFrame = 1; //单声道
pEngine->setExteranlAudioRender(true, sampleRate, channelsPerFrame); //启用音频输入播放
bRenderExternalAudio = true;

//2.独立线程推送外部音频数据
unsigned int audioDataInterval = 20; //20 ms
size_t bytePerSample = 16 / 8; // Signed 16-bit
size_t dataSize = sampleRate * channelsPerFrame * bytePerSample / (1000 / audioDataInterval);
unsigned int* data = (unsigned int*)malloc(dataSize);

do
{
    /*
    从外部数据源拷贝推送音频数据到data
    */

    std::chrono::milliseconds now = std::chrono::duration_cast<std::chrono::milliseconds>(std::chrono::system_clock::now().time_since_epoch());
    int ret = mpEngine->pushExternalAudioRenderRawData(data, dataSize, sampleRate, channelsPerFrame, now.count());
    if (ret < 0)
    {
        //发生错误，中断播放
        break;
    }

    //返回结果不为0，需要进行错误判断，检查是否缓冲区满
    //返回结果如果为0，投递成功，继续读取并投递数据，无需间隔
    while (ret == ERR_AUDIO_BUFFER_FULL && bRenderExternalAudio)
    {
        Sleep(audioDataInterval); //缓冲区满，间隔一个数据长度后再次重试，直到成功
        if (!bRenderExternalAudio) break;

        ret = mpEngine->pushExternalAudioRenderRawData(data, read_size, sampleRate, channelsPerFrame, now.count());

        if (ret < 0)
        {
            //发生错误，中断推送
            break;
        }
    }
} while (bRenderExternalAudio);

.....

//4.停止外部音频输入播放
mpEngine->setExteranlAudioRender(false, 0, 0);
bRenderExternalAudio = false;
```

