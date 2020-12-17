# iOS

阿里云RTC SDK为您提供基础美颜功能和第三方美颜接入功能的接口和回调，您可以通过本文了解相关流程。

## 基础美颜

-   功能简介

    目前阿里云RTC支持基础美颜的版本为1.17.9以上版本。

    在直播、视频通话、视频会议等场景中，美颜效果能更好的提升用户体验，阿里云RTC基础美颜提供了美白和磨皮两种功能。

-   实现方法

    阿里云RTC SDK通过setBeautyEffect方法设置是否启用基础美颜。

    ```
    /** 
    * 设置美颜 
    * @param enable 美颜开关 
    * @param config 美颜参数控制 
    */
    - (int)setBeautyEffect:(BOOL)enable config:(AliRtcBeautyConfig)config;
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|true表示开启，false表示关闭，默认为关闭。|
    |config|[AliRtcBeautyConfig](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|基础美颜参数。|


## 第三方美颜

-   功能简介

    目前阿里云RTC支持美颜接入的版本为1.14.0以上版本。

    通常美颜SDK接受如下两种类型的数据回调处理。

    -   YUV裸数据用于做人脸识别。
    -   openGL纹理数据用于最终做美颜效果的处理。
-   接入流程

    为了避免完成集成SDK后，自己能看到美颜效果，对方却看不到美颜效果。在接入前，我们需要在SDK的实例extra字段中添加开关，设置user\_specified\_video\_preprocess为TRUE。

    1.  SDK的instance构造函数里面，扩展字段添加\[extrasDic setValue:@"TRUE" forKey:@"user\_specified\_video\_preprocess"\]，并且将extraDic经过序列化之后传入到AliRtcEngine sharedInstance的第二个字段extra中。
    2.  在调用本地预览开启接口startPreview之后，调用subscribeVideoTexture订阅openGL纹理数据。

        **说明：** 通常是对本地用户进行美颜，uid填写为英文半角双引号（""）字符串即可。

    3.  需要对接YUV数据人脸识别功能时候：在调用本地预览开启接口startPreview之后，再调用subscribeVideoPreprocessData订阅采集前处理YUV数据（通常是对采集图像做人脸识别）。
    4.  需要对接YUV数据人脸识别功能时候：在onVideoDetectCallback回调中做第三方算法的人脸识别操作，返回的long为人脸识别之后的该图像的人脸结构体指针。
    5.  在onVideoTextureCreated中做第三方算法的初始化工作，其中context为openGL的上下文。
    6.  在onVideoTexture做第三方算法的每一帧美颜处理工作，如果不需要美颜或者第三方算法处理不成功，请将输入的textureId返回给该函数。如果美颜处理成功，则返回第三方算法处理过的textureId。
    7.  在onVideoTextureDestory做第三方算法的销毁工作。

## 第三方美颜接口调用

-   RTC SDK YUV裸数据人脸识别接入接口，人脸识别接入时，需要订阅采集之后的前处理buffer数据，所以在startPreview之后需要调用subscribeVideoPreprocessData接口获取采集前处理数据并处理。

    ```
    ///@brief 订阅采集视频前处理裸数据
    ///@param videoSource 订阅本地采集的哪一路流，移动端场景填写AliRtcVideosourceCameraLargeType
    - (void)subscribeVideoPreprocessData:(AliRtcVideoSource)videoSource;
    ```

    onVideoDetectCallback回调方法如下：

    **说明：** 订阅成功后，通过delegate回调本地采集数据。

    ```
    ///@brief RTC采集视频数据前处理回调
    ///@param type 视频流类型
    ///@param videoFrame 视频数据帧
    ///@return 人脸识别结构体指针（第三方定义结构体），SDK只做传递 （该返回值传递人脸数据）
    - (long)onVideoDetectCallback:(AliRtcVideoSource)type videoFrame:(AliRtcVideoDataSample *)videoFrame;
    ```

    AliRtcVideoDataSample对象定义如下：

    ```
    @interface AliRtcVideoDataSample : NSObject
    @property (nonatomic, assign) AliRtcImageFormat format; //iOS输出的YUV数据格式为NV12
    @property (nonatomic, assign) AliRtcVideoDataType dataType;
    @property (nonatomic, assign) long dataPtr;
    @property (nonatomic, assign) long dataYPtr;
    @property (nonatomic, assign) long dataUPtr;
    @property (nonatomic, assign) long dataVPtr;
    @property (nonatomic, assign) int strideY;
    @property (nonatomic, assign) int strideU;
    @property (nonatomic, assign) int strideV;
    @property (nonatomic, assign) int height;
    @property (nonatomic, assign) int width;
    @property (nonatomic, assign) int rotation;
    @property (nonatomic, assign) int stride;
    @property (nonatomic, assign) long long timeStamp;
    @end
    ```

-   RTC SDK openGL 纹理接口美颜接入时，需要订阅视频的纹理数据，所以在startPreview之后需要调用接口获取openGL的纹理数据和openGL的线程环境。需要调用的接口如下所示：

    -   subscribeVideoTexture接口。

```
///@brief 订阅openGL的纹理数据
///@param[in] uid 订阅的用户，通常本地需要美颜，填写""或者本地uid都可以
///@param[in] videoSource 订阅本地pub的哪一路流，移动端场景填写AliRtcVideosourceCameraLargeType
///@param[in] videoTextureType 美颜的场景选择AliRtcVideoTextureTypePre
- (void)subscribeVideoTexture:(NSString *)uid videoSource:(AliRtcVideoSource)videoSource videoTextureType:(AliRtcVideoTextureType)videoTextureType;
```

    -   onVideoTextureCreated回调（相芯SDK不处理此回调）。

```
///@brief 表示本地视频流纹理创建
///@param[in] uid 订阅的用户，subscribeVideoTexture所填写的uid
///@param[in] videoTextureType，subscribeVideoTexture所填写的videoTextureType
///@param[in] context openGL的上下文EAGLContext指针
- (void)onVideoTextureCreated:(NSString *)uid videoTextureType:(AliRtcVideoTextureType)videoTextureType context:(void *)context
```

    -   onVideoTexture回调。

```
///@brief 表示每一帧视频流处理
///@param[in] uid 订阅的用户，subscribeVideoTexture所填写的uid
///@param[in] videoTextureType，subscribeVideoTexture所填写的videoTextureType
///@param[in] textureId 视频流纹理的输入texture id
///@param[in] width 视频流纹理的宽度
///@param[in] height 视频流纹理的高度
///@param[in] extraData 检测的人脸数据， 带人脸识别时：为onVideoDetectCallback返回的人脸结构数据指针；不带人脸识别时：为0
///@param[out] 处理之后的texture id，如果不需要美颜，请把textureId输入的texture id传回
- (int)onVideoTexture:(NSString *)uid videoTextureType:(AliRtcVideoTextureType)videoTextureType textureId:(int)textureId width:(int)width height:(int)height extraData:(long)extraData
```

    -   onVideoTextureDestory回调（相芯SDK不处理此回调）。

```
///@brief 表示本地视频流纹理销毁
///@param[in] uid 订阅的用户，subscribeVideoTexture所填写的uid
///@param[in] videoTextureType，subscribeVideoTexture所填写的videoTextureType
- (void)onVideoTextureDestory:(NSString *)uid videoTextureType:(AliRtcVideoTextureType)videoTextureType
```

-   外置美颜SDK相关接口调用。

    外置美颜SDK根据各自的设计，有对应的SDK自己的提供的接口，需要App对接时候正确使用，主要有如下：

    -   初始化、销毁。
    -   资源加载和释放（通常是人脸识别使用的资源文件）。
    -   美颜控制接口（美颜等级、强度的调节接口，美颜开关接口）。
    -   对接RTC SDK回调的接口。

