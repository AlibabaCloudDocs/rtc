# Web

本文为您介绍Web端音频输出功能调用接口的具体步骤。

## 输出音频媒体

1.  开启音频数据接收回调。

    ```
    aliWebrtc.enableAudioVolumeIndicator = true;
    ```

    **说明：** 该接口可以在实例化后任何时间开启。

2.  使用音频能量值回调。

    ```
    aliWebrtc.on("onAudioLevel").then(data => {
        console.log(data)
    })
    ```

    **说明：** 需要设置[enableAudioVolumeIndicator](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)后回调，每两秒返回一次（返回两秒内音频能量最大值）。

    返回结果说明：

    -   当您推了音频流，返回数组中userId为字符串0的一项，是自己的音频信息。
    -   当您订阅了其他用户的音频流，该数组中会包含订阅用户的音频信息。
    -   具体数组各项的信息如下所示：

        |返回值|类型|描述|
        |---|--|--|
        |userId|String|订阅用户userId，用户自己的userId为0。|
        |displayName|String|用户名。|
        |level|Number|音频能量值，取值范围0~100。|
        |buffer|Array|音频PCM两秒内的数据。|

3.  关闭音频数据接收回调。

    当您需要停止接收音频数据，可以设置关闭音频数据接收。

    ```
    aliWebrtc.enableAudioVolumeIndicator = false;
    ```


