# iOS播放音效文件

RTC SDK为您提供了伴奏文件和音效文件设置接口。通过阅读本文，您可以了解伴奏文件和音效文件的设置方法。

## 伴奏文件

-   startAudioAccompanyWithFile（仅iOS可用）：开始播放伴奏。

    ```
    - (int)startAudioAccompanyWithFile:(NSString *)filePath onlyLocalPlay:(BOOL)onlyLocalPlay replaceMic:(BOOL)replaceMic loopCycles:(NSInteger)loopCycles;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |filePath|NSString \*|文件路径。|
    |onlyLocalPlay|BOOL|是否只本地播放。取值：YES\|NO。|
    |replaceMic|BOOL|是否替换MIC（麦克风）。取值：YES\|NO。|
    |loopCycles|NSInteger|循环次数。可以设置为-1或者正整数。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 支持本地资源和网络资源播放。

-   pauseAudioAccompany（仅iOS可用）：暂停播放伴奏。

    ```
    - (int)pauseAudioAccompany;
    ```

    返回说明

    0表示成功，其他返回错误码。

-   resumeAudioAccompany（仅iOS可用）：恢复播放伴奏。

    ```
    - (int)resumeAudioAccompany;
    ```

    返回说明

    0表示成功，其他返回错误码。

-   stopAudioAccompany（仅iOS可用）：停止伴奏。

    ```
    - (int)stopAudioAccompany;
    ```

    返回说明

    0表示成功，其他返回错误码。

-   setAudioAccompanyVolume：设置伴奏音量。

    ```
    - (int)setAudioAccompanyVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量。取值范围：0~100。默认取值50。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 设置音量需要在调用startAudioAccompanyWithFile后才能生效。

-   setAudioAccompanyPublishVolume（仅iOS可用）：设置伴奏之后推流出去的音量。

    ```
    - (int)setAudioAccompanyPublishVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量。取值范围：0~100。默认取值50。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 设置音量需要在调用startAudioAccompanyWithFile后才能生效。

-   getAudioAccompanyPublishVolume（仅iOS可用）：获取伴奏推流音量。

    ```
    - (int)getAudioAccompanyPublishVolume;
    ```

    返回说明

    0表示成功，其他返回错误码。

-   setAudioAccompanyPlayoutVolume（仅iOS可用）：设置伴奏本地音量。

    ```
    - (int)setAudioAccompanyPlayoutVolume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|NSInteger|混音音量。取值范围：0~100。默认取值50。|

    返回说明

    0表示成功，其他返回错误码。

    **说明：** 设置音量需要在调用startAudioAccompanyWithFile后才能生效。

-   getAudioAccompanyPlayoutVolume（仅iOS可用）：获取伴奏本地音量。

    ```
    - (int)getAudioAccompanyPlayoutVolume;
    ```

    返回说明

    0表示成功，其他返回错误码。


## 音效文件

-   preloadAudioEffectWithSoundId（仅iOS可用）：预加载音效。

    ```
    - (int)preloadAudioEffectWithSoundId:(NSInteger)soundId filePath:(NSString *)filePath;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |filePath|NSString \*|音效文件路径。|

    返回说明

    0表示成功，其他返回错误码。

-   unloadAudioEffectWithSoundId（仅iOS可用）：清除预加载音效。

    ```
    - (int)unloadAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示成功，其他返回错误码。

-   playAudioEffectWithSoundId（仅iOS可用）：开始播放音效。

    ```
    - (int)playAudioEffectWithSoundId:(NSInteger)soundId filePath:(NSString *)filePath cycles:(NSInteger)cycles publish:(BOOL)publish;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |filePath|NSString \*|音效文件路径。|
    |cycles|NSInteger|循环次数。可以设置-1或者正整数。|
    |publish|BOOL|是否发布。取值：YES\|NO。|

    返回说明

    0表示成功，其他返回错误码。

-   pauseAudioEffectWithSoundId（仅iOS可用）：暂停播放音效。

    ```
    - (int)pauseAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示成功，其他返回错误码。

-   resumeAudioEffectWithSoundId（仅iOS可用）：恢复播放音效。

    ```
    - (int)resumeAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示成功，其他返回错误码。

-   stopAudioEffectWithSoundId（仅iOS可用）：停止播放音效。

    ```
    - (int)stopAudioEffectWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示成功，其他返回错误码。

-   setAudioEffectPublishVolumeWithSoundId（仅iOS可用）：设置音效推流音量。

    ```
    - (int)setAudioEffectPublishVolumeWithSoundId:(NSInteger)soundId volume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |volume|NSInteger|混音音量。取值范围：0~100。默认取值50。|

    返回说明

    0表示成功，其他返回错误码。

-   getAudioEffectPublishVolumeWithSoundId（仅iOS可用）：获取音效推流音量。

    ```
    - (int)getAudioEffectPublishVolumeWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    返回0~100为成功，否则返回错误码。

-   setAudioEffectPlayoutVolumeWithSoundId（仅iOS可用）：设置音效本地音量。

    ```
    - (int)setAudioEffectPlayoutVolumeWithSoundId:(NSInteger)soundId volume:(NSInteger)volume;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|
    |volume|NSInteger|混音音量。取值范围：0~100。默认取值50。|

    返回说明

    0表示成功，其他返回错误码。

-   getAudioEffectPlayoutVolumeWithSoundId（仅iOS可用）：获取音效本地音量。

    ```
    - (int)getAudioEffectPlayoutVolumeWithSoundId:(NSInteger)soundId;
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|NSInteger|用户给该音效文件分配的ID。|

    返回说明

    0表示成功，其他返回错误码。


