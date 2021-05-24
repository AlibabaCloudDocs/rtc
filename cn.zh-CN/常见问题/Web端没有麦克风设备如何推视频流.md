# Web端没有麦克风设备如何推视频流

通过阅读本文，您可以了解到当Web端没有麦克风时设备推视频流的方法。

1.  设置纯订阅模式跳过isSupport设备检测。

    ```
    aliWebrtc.isSupport({isReceiveOnly: true}).then((re)=>{
        // 支持纯订阅模式
    }).catch(err => {
        // 不支持纯订阅模式
    })
    ```

2.  获取audiotrack，设置外部输入`setExternalMediaTrack`替换音频流。

    ```
    //获取mediaStream
    let mediaStream = video.captureStream(); // video为播放视频的media标签
    //获取音频列表
    let audiotracks = mediaStream && mediaStream.getAudioTracks()
    //获取其中某一个audiotrack
    let audiotrack = (audiotracks && audiotracks.length) ? audiotracks[0]
    //置外部输入替换音频流
    aliWebrtc.setExternalMediaTrack(audiotrack, 0);
    ```

    **说明：**

    -   设置外部输入前需要先停止正在进行的推流。
    -   每次停止推流后都需要重新设置外部输入。
3.  正常推流（此时可以不推音频流，SDK内部识别出已经推了外部输入音频，因此会跳过设备检测）。


