# Android播放音效文件

RTC SDK为您提供了伴奏文件和音效文件设置接口。通过阅读本文，您可以了解伴奏文件和音效文件的设置方法。

## 伴奏文件

-   startAudioAccompany：开始播放伴奏。

    ```
    public abstract int startAudioAccompany(String fileName, boolean onlyLocalPlay, boolean replaceMic, int loopCycles);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |fileName|String|伴奏文件路径，支持本地文件和网络url。|
    |onlyLocalPlay|boolean|是否仅本地播放，true表示仅仅本地播放，false表示本地播放且推流到远端。|
    |replaceMic|boolean|是否替换mic的音频流，true表示伴奏音频流替换本地mic音频流，false表示伴奏音频流和mic音频流同时推。|
    |loopCycles|int|循环播放次数，-1表示一直循环。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   pauseAudioAccompany：暂停播放伴奏。

    ```
    public abstract int pauseAudioAccompany();
    ```

    返回说明

    0表示操作成功，非0表示操作失败。

-   resumeAudioAccompany：恢复播放伴奏。

    ```
    public abstract int resumeAudioAccompany();
    ```

    返回说明

    0表示操作成功，非0表示操作失败。

-   stopAudioAccompany：结束播放伴奏。

    ```
    public abstract int stopAudioAccompany();
    ```

    返回说明

    0表示操作成功，非0表示操作失败。

-   setAudioAccompanyVolume：设置伴奏推流和本地音量。

    ```
    public abstract int setAudioAccompanyVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |volume|int|伴奏本地播放音量。默认取值50。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   setAudioAccompanyPublishVolume：设置伴奏推流音量。

    ```
    public abstract int setAudioAccompanyPublishVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |volume|int|伴奏推流音量。默认取值50。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   getAudioAccompanyPublishVolume：获取伴奏推流音量。

    ```
    public abstract int getAudioAccompanyPublishVolume();
    ```

    返回说明

    返回伴奏推流音量取值范围：0~100，返回-1表示获取失败。

-   setAudioAccompanyPlayoutVolume：设置伴奏本地音量。

    ```
    public abstract int setAudioAccompanyPlayoutVolume(int volume);
    ```

    参数说明

    |名称|类型|描述|
    |volume|int|伴奏本地播放音量。默认取值50。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   getAudioAccompanyPlayoutVolume：获取伴奏本地音量。

    ```
    public abstract int getAudioAccompanyPlayoutVolume();
    ```

    返回说明

    返回伴奏推流音量取值范围：0~100，返回-1表示获取失败。


## 音效文件

-   preloadAudioEffect：预加载音效。

    ```
    public abstract int preloadAudioEffect(int soundId, String filePath);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID（此ID由调用者生成）。|
    |filePath|String|音效文件路径。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   unloadAudioEffect：清除预加载音效。

    ```
    public abstract int unloadAudioEffect(int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID（此ID应与预加载时传入的ID相同）。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   playAudioEffect：开始播放音效。

    ```
    public abstract int playAudioEffect(int soundId, String filePath, int cycles, boolean publish);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|
    |filePath|String|音效文件路径，支持本地文件和网络url。|
    |cycles|int|循环播放次数。-1表示一直循环。|
    |publish|boolean|是否将音效音频流推到远端。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   pauseAudioEffect：暂停播放音效。

    ```
    public abstract int pauseAudioEffect(int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   resumeAudioEffect：恢复播放音效。

    ```
    public abstract int resumeAudioEffect(int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   stopAudioEffect：停止播放音效。

    ```
    public abstract int stopAudioEffect(int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    0表示操作成功，非0表示操作失败。

-   setAudioEffectPublishVolume：设置音效推流音量。

    ```
    public abstract int setAudioEffectPublishVolume(int soundId, int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|
    |volume|int|音效推流音量。取值范围：0～100。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   getAudioEffectPublishVolume：获取音效推流音量。

    返回0~100音效推流音量，返回-1表示获取失败。

    ```
    public abstract int getAudioEffectPublishVolume(int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    返回音效推流音量取值范围：0~100，返回-1表示获取失败。

-   setAudioEffectPlayoutVolume：设置音效本地音量。

    ```
    public abstract int setAudioEffectPlayoutVolume(int soundId, int volume);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|
    |volume|int|音效本地播放音量。取值范围：0～100。默认取值50。|

    返回说明

    0表示操作成功， 非0表示操作失败。

-   getAudioEffectPlayoutVolume：获取音效本地音量。

    ```
    public abstract int getAudioEffectPlayoutVolume(int soundId);
    ```

    参数说明

    |名称|类型|描述|
    |--|--|--|
    |soundId|int|音效ID。|

    返回说明

    返回音效本地播放音量取值范围：0~100，-1表示获取失败。


