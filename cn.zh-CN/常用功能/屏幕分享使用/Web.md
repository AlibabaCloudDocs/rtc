# Web

阿里云RTC SDK为您提供屏幕分享使用的接口方法，通过本文档您可以了解实现的具体调用流程。

您需要调用isSupport接口根据返回参数supportScreenShare来检测是否支持屏幕分享。

## 环境要求

Web SDK屏幕共享功能的环境要求请参见[环境要求](/cn.zh-CN/快速入门/集成客户端SDK/Web.md)。

## 推流端

1.  设置参数。

    ```
    /**
     * 设置视频/屏幕流参数
     * @param {Number} width 宽度
     * @param {Number} height 高度
     * @param {Number} frameRate 帧率
     * @param {Number} type 类型 1：摄像头流 2：共享流
     */
    aliWebrtc.setVideoProfile({
        width,
        height,
        frameRate
    },type);
    ```

2.  启动屏幕分享。

    ```
    // 配置屏幕共享推流
    aliWebrtc.configLocalScreenPublish = true;
    
    // 启动推流
    aliWebrtc.publish().then(()=>{
        //推流成功
    }).catch((err) => {
      //推流失败
    })
    ```

3.  共享屏幕声音。

    **说明：** 共享屏幕声音支持Windows端Chrome 75及以上版本或Edge 80及以上版本，Mac端仅支持分享标签页声音。

    1.  勾选**分享音频**。

        ![001](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3802612161/p237285.png)

    2.  推音频流。

        分享的音频会和麦克风混流，需要同时推音频流，此时订阅端只需订阅音频流就可以听到对方麦克风和屏幕分享音频。

4.  停止屏幕分享。

    ```
    // 配置屏幕共享停止
    aliWebrtc.configLocalScreenPublish = false;
    
    // 启动停推
    aliWebrtc.publish().then(()=>{
        //推流成功
    }).catch((err) => {
      //推流失败
    })
    ```

5.  错误码提示。

    ```
    aliWebrtc.on("onError",(error)=>{
      //10010 屏幕共享未知错误
      //10011 屏幕共享在选择页面取消选择 屏幕共享被禁止
      //10012 屏幕共享在网页底部悬浮窗单击停止共享  屏幕共享已取消
        console.log(error.errorCode);
    })
    ```


## 订阅端

订阅端用户可通过手动方式订阅推流端屏幕共享流，并设置对应video显示，详情请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)。

