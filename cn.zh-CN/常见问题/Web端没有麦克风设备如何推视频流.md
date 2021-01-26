# Web端没有麦克风设备如何推视频流

通过阅读本文，您可以了解到当Web端没有麦克风时，设备推视频流的方法。

1.  设置纯订阅模式跳过isSupport设备检测。

    ```
    aliWebrtc.isSupport({isReceiveOnly: true}).then((re)=>{
        // 支持纯订阅模式
    }).catch(err => {
        // 不支持纯订阅模式
    })
    ```

2.  获取audiotrack，设置外部输入`setExternalMediaTrack`替换音频流。

    可通过audio、video或canvas播放音频或视频，使用`captureStream`方法获取mediaStream，然后调用`mediaStream.getAudioTracks()`获取音频列表，再获取其中某一个audiotrack。最后设置外部输入`setExternalMediaTrack`替换音频流。

    ```
    let mediaStream = video.captureStream(); // video为播放视频的media标签
    let audiotracks = mediaStream && mediaStream.getAudioTracks()
    let audiotrack = (audiotracks && audiotracks.length) ? audiotracks[0]
    aliWebrtc.setExternalMediaTrack(audiotrack, 0);
    ```

    **说明：**

    -   设置外部输入前需要先停止正在进行的推流。
    -   每次停止推流后都需要重新设置外部输入。
3.  正常推流（此时可以不推音频流，SDK内部识别出已经推了外部输入音频，因此会跳过设备检测）。


