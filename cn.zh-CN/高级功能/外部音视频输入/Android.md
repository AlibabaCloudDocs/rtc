# Android

阿里云RTC为您提供了输入外部音视频流的功能。通过阅读本文，您可以了解输入外部音视频流的方法。

## 输入外部视频流

**说明：** SDK允许先推流然后开启外部视频输入，但这种情况下，默认开始推流时，先推送出的是本地原始采集源（摄像头或屏幕捕获）的视频数据，直到启用外部输入。

1.  调用[registerVideoRawDataInterface](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)注册外部视频接口回调。

    ```
    //获取AliRtcEngine实例
    AliRtcEngine mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
    AliRtcEngine.VideoRawDataInterface videoRawDataInterface = mAliRtcEngine.registerVideoRawDataInterface(
                        AliRtcEngine.AliRawDataStreamType.AliRTCSdk_Streame_Type_Capture, AliRtcEngine.AliRtcRenderMode.AliRtcRenderModeAuto);
    ```

2.  输入视频数据。

    接口说明如下所示。

    ```
    /**
             * 发送视频帧
             * @param frame AliRawDataFrame数据帧实体类
             * @param timeStamp 时间戳
             * @return
             */
            public abstract int deliverFrame(AliRawDataFrame frame, long timeStamp);
    ```

    参数说明，AliRawDataFrame必填项如下所示。

    |参数|说明|
    |--|--|
    |MediaStatesVideoFormat|数据类型，目前默认AndroidYUV数据返回NV21|
    |width|视频流宽|
    |height|视频流高|
    |rotation|视频流角度|
    |video\_frame\_length|数据buffer长度|
    |lineSize|yuv数据数组，具体使用请参见下文示例|
    |frame|buffer数据|

    示例方法如下所示。

    ```
    private void decodeYUVRawData(AliRtcEngine.VideoRawDataInterface videoRawDataInterface) {
            String yuvPath = "<!-请输入yuv文件地址->";
            if (TextUtils.isEmpty(yuvPath)) {
                ToastUtils.LongToast("请先选择YUV文件！！！");
                return;
            }
            File yuvDataFile = new File(yuvPath);
            if (!yuvDataFile.exists()) {
                ToastUtils.LongToast(yuvPath + " 文件不存在！！！");
                return;
            }
            //此处仅为示例代码做法，请使用正确的流角度
            int rotation = 90;
            Log.d(TAG, "decodeYUVRawData: "+rotation+"__"+getVideoFormat());
            ToastUtils.LongToast("inputing yuv data");
            //此处仅为示例代码做法，请使用正确的流宽高
            int width = 480;
            int height = 640;
            //start push yuv
            new Thread() {
                @Override
                public void run() {
                    File yuvDataFile = new File(yuvPath);
                    RandomAccessFile raf = null;
                    try {
                        raf = new RandomAccessFile(yuvDataFile, "r");
                    } catch (FileNotFoundException e) {
                        e.printStackTrace();
                        return;
                    }
                    try {
                        byte[] buffer = new byte[width * height * 3 / 2];
                        while (videoRawDataInterface != null) {
                            int len = raf.read(buffer);
                            if (len == -1) {
                                raf.seek(0);
                            }
                            AliRtcEngine.AliRawDataFrame rawDataFrame
                                    = new AliRtcEngine.AliRawDataFrame();
                            rawDataFrame.format = MediaStatesVideoFormat.NV21;// 支持NV21和I420
                            rawDataFrame.frame = buffer;
                            rawDataFrame.width = width;
                            rawDataFrame.height = height;
                            rawDataFrame.lineSize[0] = width;
                            rawDataFrame.lineSize[1] = width / 2;
                            rawDataFrame.lineSize[2] = height / 2;
                            rawDataFrame.lineSize[3] = 0;
                            rawDataFrame.rotation = rotation;
                            rawDataFrame.video_frame_length = buffer.length;
                            if (videoRawDataInterface != null) {
                                    videoRawDataInterface.deliverFrame(rawDataFrame, System.nanoTime() / 1000);
                            }
                            //主动sleep发送一次
                            Thread.sleep(25);
                        }
                    } catch (IOException | InterruptedException ex) {
                        ex.printStackTrace();
                    } finally {
                        try {
                            raf.close();
                        } catch (IOException e) {
                            e.printStackTrace();
                        }
                    }
                }
            }.start();
        }
    ```

3.  调用[unRegisterVideoRawDataInterface](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)取消注册外部视频接口回调。

    ```
    mAliRtcEngine.unRegisterVideoRawDataInterface(
                        type);
    ```


## 输入外部音频流

1.  调用[setExternalAudioSource](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)启用外部音频输入，并调用[setMixedWithMic](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)设置外部音频输入是否与麦克风混合。

    ```
    //获取mAliRtcEngine，
    AliRtcEngine  mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext());
    //设置开启外部音频输入源
    mAliRtcEngine.setExternalAudioSource(true,44100,1);
    //完全替代麦克风采集
    mAliRtcEngine.setMixedWithMic(false);
    ```

2.  调用[pushExternalAudioFrameRawData](/cn.zh-CN/SDK参考/Android SDK/AliRtcEngine接口.md)输入音频数据。

    **说明：** 如果返回值为17236225，表示当前buffer队列饱和，建议您等待20ms，再继续输送数据。

    ```
    private void decodePCMRawData(){
            String pcmPath = "/sdcard/123.pcm";
            if (TextUtils.isEmpty(pcmPath)) {
                ToastUtils.LongToast("请先选择PCM文件！！！");
                return;
            }
            File pcmDataFile = new File(pcmPath);
            if (!pcmDataFile.exists()) {
                ToastUtils.LongToast(pcmPath + " 文件不存在！！！");
                return;
            }
            ToastUtils.LongToast("inputing pcm data");
    
            new Thread() {
                @Override
                public void run() {
                    File pcmDataFile = new File(pcmPath);
                    RandomAccessFile raf = null;
                    try {
                        raf = new RandomAccessFile(pcmDataFile, "r");
                    } catch (FileNotFoundException e) {
                        e.printStackTrace();
                        return;
                    }
                    try {
                        byte[] buffer = new byte[(44100/100)*4*1];
                        while (true) {
                            int len = raf.read(buffer);
                            if (len == -1) {
                                raf.seek(0);
                            }
                            mAliRtcEngine.pushExternalAudioFrameRawData(buffer,buffer.length,0);
                            Thread.sleep(20);
                        }
                    } catch (IOException | InterruptedException ex) {
                        ex.printStackTrace();
                    } finally {
                        try {
                            raf.close();
                        } catch (IOException e) {
                            e.printStackTrace();
                        }
                    }
                }
            }.start();
        }
    ```


