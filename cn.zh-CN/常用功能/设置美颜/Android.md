# Android

阿里云RTC SDK为您提供基础美颜功能和第三方美颜接入功能的接口和回调，您可以通过本文了解相关流程。

## 基础美颜

-   功能简介

    目前阿里云RTC支持基础美颜的版本为1.17.9以上版本。

    在直播、视频通话、视频会议等场景中，美颜效果能更好的提升用户体验，阿里云RTC基础美颜提供了美白和磨皮两种功能。

-   实现方法

    阿里云RTC SDK通过setBeautyEffect方法设置是否启用基础美颜。

    ```
    public abstract int setBeautyEffect(boolean enable, AliRtcEngine.AliRtcBeautyConfig config);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|true表示开启，false表示关闭，默认为关闭。|
    |config|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|基础美颜参数。|


## 第三方美颜

-   功能简介

    目前阿里云RTC支持美颜接入的版本为1.14.0以上版本。

    通常美颜SDK接受如下两种类型的数据回调处理：

    -   YUV裸数据用于做人脸识别。
    -   openGL纹理数据用于最终做美颜效果的处理。
-   接入流程

    为了避免完成集成SDK后，自己能看到美颜效果，对方却看不到美颜效果。在接入前，我们需要在SDK的实例extra字段中添加开关，设置user\_specified\_video\_preprocess为TRUE。

    1.  SDK的instance构造函数里面，扩展字段添加jsonObject.addProperty\("user\_specified\_video\_preprocess", "TRUE"\)，并且将jsonObject转化成string后传入到AliRtcEngine.getInstance的第二个字段extra里面。
    2.  在调用本地预览开启接口startPreview之后，调用RegisterTexturePreObserver订阅openGL纹理数据。

        **说明：** 通常是对本地用户进行美颜，callid填写为双引号（""）字符串即可。

    3.  需要对接YUV数据人脸识别功能时候：在调用本地预览开启接口startPreview之后，再调用RegisterPreprocessVideoObserver订阅采集前处理YUV数据（通常是对采集图像做人脸识别）。
    4.  需要对接YUV数据人脸识别功能时候：在AliDetectObserver的onData回调中做第三方算法的人脸识别操作，返回的long为人脸识别之后的该图像的人脸结构体指针。
    5.  在传入observer函数回调onTextureCreate中第三方算法的初始化工作，其中context为openGL的上下文。
    6.  在传入observer函数回调onTexture做第三方算法的每一帧美颜处理工作，如果不需要美颜或者第三方算法处理不成功，请将输入的textureId返回给该函数。如果美颜处理成功，则返回第三方算法处理过的textureId。
    7.  在传入observer函数回调onTextureDestroy做第三方算法的销毁工作。

## 第三方美颜接口调用

-   RTC SDK YUV裸数据人脸识别接入接口，人脸识别接入时，需要订阅采集之后的前处理buffer数据，所以在startPreview之后需要调用RegisterPreprocessVideoObserver接口获取采集前处理数据并处理。

    ```
    ///@brief register preprocess observer 
    ///@param observer 回调接口
    void RegisterPreprocessVideoObserver(AliDetectObserver observer);
    ```

    订阅成功后，将会回调AliDetectObserver的onData参数。

    ```
    ///@brief 采集前处理回调接口
    ///@param dataFrameY Y分量指针
    ///@param dataFrameU U分量指针
    ///@param dataFrameV V分量指针，NV12和NV21该指针为null
    ///@param format， 图像数据格式，Android输出的YUV数据格式为NV21
    ///@param width， 图像宽度
    ///@param height， 图像高度
    ///@param strideY， 图像Y分量stride
    ///@param strideU， 图像U分量stride
    ///@param strideV， 图像V分量stride
    ///@param rotate， 图像旋转角度
    ///@param extraData，附加字段（非定制化可忽略）
    ///@return 人脸识别结构体指针（第三方定义结构体），SDK只做传递 （该返回值传递人脸数据）
    long onData(long dataFrameY, long dataFrameU, long dataFrameV, AliRTCImageFormat format, int width, int height, int strideY, int strideU, int strideV, int rotate, long extraData);
    ```

-   RTC SDK openGL纹理接口在美颜接入时，需要订阅视频的纹理数据，所以在startPreview之后需要调用接口获取openGL的纹理数据和openGL的线程环境。 需要调用的接口如下所示：

-   RegisterTexturePreObserver接口。

```
///@brief 订阅openGL的纹理数据
///@param[in] uid 订阅的用户，通常本地需要美颜，填写""或者本地uid都可以
///@param[in] observer 回调接口
void RegisterTexturePreObserver(String callId, AliTextureObserver observer);
```

-   onTextureCreate回调（相芯SDK不处理此回调）。

```
///@brief 表示本地视频流纹理创建
///@param[in] callId 订阅的用户，RegisterTexturePreObserver所填写的callId
///@param[in] context openGL的上下文EGLContext指针
void onTextureCreate(String callId, long context);
```

-   onTexture回调。

```
///@brief 表示每一帧视频流处理
///@param[in] callId 订阅的用户，RegisterTexturePreObserver所填写的callId
///@param[in] textureId 视频流纹理输入的ID
///@param[in] width 视频流纹理的宽度
///@param[in] height 视频流纹理的高度
///@param[in] stride 视频流纹理的stride
///@param[in] rotate 视频流纹理的rotate角度
///@param[in] extraData 检测的人脸数据，带人脸识别时：为AliDetectObserver的OnData返回的人脸结构数据指针；不带人脸识别时：为0
///@param[out] 处理之后的texture id，如果不需要美颜，请把textureId输入的texture id传回
int onTexture(String callId, int textureId, int width, int height, int stride, int rotate, long extraData);
```

-   onTextureDestroy回调（相芯SDK不处理此回调）。

```
///@brief 表示本地视频流纹理销毁
///@param[in] callId 订阅的用户，RegisterTexturePreObserver所填写的callId
void onTextureDestroy(String callId);
```


