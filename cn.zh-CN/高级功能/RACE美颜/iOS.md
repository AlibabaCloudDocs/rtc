# iOS

通过阅读本文，您可以了解RACE美颜的集成方式及RTC对接RACE美颜的方法。

## 集成RACE SDK

支持pods与本地集成两种方式。

-   pods集成

    ```
    pod 'AliyunRace', '1.0.0.12196201'
    ```

-   本地集成

    获取AliyunRace.framework、Face3D.framwork、opencv2.framework文件并添加到工程中。


## RTC SDK对接RACE接口说明

以下为RTC SDK对接RACE时需要使用的接口说明，RACE美颜SDK中的其他接口不在本文说明。

|API|描述|
|---|--|
|[aliyun\_beautify\_create](#li_1j2_dy6_hcb)|创建美颜美型实例。|
|[aliyun\_beautify\_setFaceDebug](#li_6jl_gw9_ekw)|美颜美型调试开关。|
|[aliyun\_setLogLevel](#li_9p0_8p1_fp1)|设置输出日志等级。|
|[aliyun\_beautify\_setSkinBuffing](#li_9ic_x4u_ass)|设置磨皮等级。|
|[aliyun\_beautify\_setSharpen](#li_x3y_nei_riy)|设置锐化等级。|
|[aliyun\_beautify\_setSkinWhitening](#li_dj7_iff_w8u)|设置美白等级。|
|[aliyun\_beautify\_setFaceSwitch](#li_j26_iey_3py)|美型开关。|
|[aliyun\_beautify\_setFaceShape](#li_p1z_o1e_5wf)|设置美型等级。|
|[aliyun\_beautify\_processTextureToTexture](#li_jet_h73_mqv)|美颜美型纹理输入渲染。|
|[aliyun\_beautify\_destroy](#li_faw_el8_82p)|销毁美颜美型实例。|

-   aliyun\_beautify\_create：创建美颜美型实例。

    ```
    int aliyun_beautify_create(race_t *handle);
    ```

    |参数|类型|描述|
    |--|--|--|
    |context|Context|上下文。|

    返回说明

    0表示创建成功，小于0表示创建失败。

-   aliyun\_beautify\_setFaceDebug：美颜美型调试开关。

    ```
    int aliyun_beautify_setFaceDebug(race_t handle, bool enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |enable|bool|调试开启标志。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   aliyun\_setLogLevel：设置输出日志等级。

    ```
    void aliyun_setLogLevel(int level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |level|int|日志等级。|

-   aliyun\_beautify\_setSkinBuffing：设置磨皮等级。

    ```
    int aliyun_beautify_setSkinBuffing(race_t handle, float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |level|float|磨皮等级，范围：0~1。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   aliyun\_beautify\_setSharpen：设置锐化等级。

    ```
    int aliyun_beautify_setSharpen(race_t handle, float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |level|float|锐化等级，范围：0~1。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   aliyun\_beautify\_setSkinWhitening：设置美白等级。

    ```
    int aliyun_beautify_setSkinWhitening(race_t handle, float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |level|float|美白等级，范围：0~1。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   aliyun\_beautify\_setFaceSwitch：美型开关。

    ```
    void aliyun_beautify_setFaceSwitch(race_t handle, bool switchOn);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |switchOn|bool|是否开启人脸检测及美型处理，取值：    -   true：开启。
    -   false：关闭。 |

-   aliyun\_beautify\_setFaceShape：设置美型等级。

    ```
    int aliyun_beautify_setFaceShape(race_t handle, ALRFaceShape type, float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |type|ALRFaceShape|美型类型。|
    |level|float|美型等级，可以超出[ALRFaceShape](#p_tkw_w2r_i13)中定义的参数范围。|

    返回说明

    0表示设置成功，小于0表示设置失败。

    ALRFaceShape 定义和建议范围如下：

    ```
    typedef enum ALRFaceShape
    {
        ALR_FACE_TYPE_CUT_CHEEK       = 0,//颧骨，取值：0~1
        ALR_FACE_TYPE_CUT_FACE        = 1,//削脸，取值：0~1
        ALR_FACE_TYPE_THIN_FACE       = 2,//瘦脸，取值：0~1
        ALR_FACE_TYPE_LONG_FACE       = 3,//脸长，取值：0~1
        ALR_FACE_TYPE_LOWER_JAW       = 4,//下巴缩短，取值：-1~1
        ALR_FACE_TYPE_HIGHER_JAW      = 5,//下巴拉长，取值：-1~1
        ALR_FACE_TYPE_THIN_JAW        = 6,//瘦下巴，取值：-1~1
        ALR_FACE_TYPE_THIN_MANDIBLE   = 7,//瘦下颌，取值：0~1
        ALR_FACE_TYPE_BIG_EYE         = 8, //大眼，取值：0~1
        ALR_FACE_TYPE_EYE_ANGLE1      = 9,//眼角1，取值：0~1
        ALR_FACE_TYPE_CANTHUS         = 10,//眼距，取值：-1~1
        ALR_FACE_TYPE_CANTHUS1        = 11,//拉宽眼距，取值：-1~1
        ALR_FACE_TYPE_EYE_ANGLE2      = 12,//眼角2，取值：-1~1
        ALR_FACE_TYPE_EYE_TDANGLE     = 13,//眼睛高度，取值：-1~1
        ALR_FACE_TYPE_THIN_NOSE       = 14,//瘦鼻，取值：0~1
        ALR_FACE_TYPE_NOSE_WING       = 15,//鼻翼，取值：0~1
        ALR_FACE_TYPE_NASAL_HEIGHT    = 16,//鼻长，取值：-1~1
        ALR_FACE_TYPE_NOSE_TIP_HEIGHT = 17,//鼻头长，取值：-1~1
        ALR_FACE_TYPE_MOUTH_WIDTH     = 18,//唇宽，取值：-1~1
        ALR_FACE_TYPE_MOUTH_SIZE      = 19,//嘴唇大小，取值：-1~1
        ALR_FACE_TYPE_MOUTH_HIGH      = 20,//唇高，取值：-1~1
        ALR_FACE_TYPE_PHILTRUM        = 21, //人中
        ALR_FACE_TYPE_MAX             = 22
    } ALRFaceShape;
    ```

-   aliyun\_beautify\_processTextureToTexture：美颜美型纹理输入渲染。

    ```
    int aliyun_beautify_processTextureToTexture(race_t handle,
                                                uint32_t textureIn,
                                                uint32_t width,
                                                uint32_t height,
                                                aliyun_rotation_t rotation,
                                                uint8_t flags);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|
    |textureIn|uint32\_t|输入图像纹理。|
    |width|uint32\_t|输入图像纹理宽度。|
    |height|uint32\_t|输入图像纹理高度。|
    |rotation|aliyun\_rotation\_t|输入图像纹理旋转角度（顺时针），RTC 对接时该参数必须设置为ALR\_ROTATE\_180\_CW。|
    |flags|uint8\_t|RTC对接时该参数必须设置为0。|

    返回说明

    返回textureId表示渲染成功，小于0表示渲染失败。

-   aliyun\_beautify\_destroy：销毁美颜美型实例。

    ```
    void aliyun_beautify_destroy(race_t handle);
    ```

    |参数|类型|描述|
    |--|--|--|
    |handle|race\_t|美颜美型句柄。|


## RTC对接RACE美颜

1.  设置RTC Engine美颜通道。

    RTC中使用外置美颜功能时，必须打开Engine的美颜通道。美颜通道的打开是通过在AliRtcEngine sharedInstance的第二个参数extra中添加`user_specified_video_preprocess`扩展字段，并设置为TRUE。

    ```
    #pragma mark extras配置
    - (NSString *)serializeExtrasJson {
        NSMutableDictionary *extrasDic = [[NSMutableDictionary alloc] init];
        [extrasDic setValue:@"TRUE" forKey:@"user_specified_video_preprocess"];
    
        if (extrasDic.count == 0) {
            return @"";
        }
        NSError *parseError = nil;
        NSData *jsonData = [NSJSONSerialization dataWithJSONObject:extrasDic options:NSJSONWritingPrettyPrinted error:&parseError];
        return [[NSString alloc] initWithData:jsonData encoding:NSUTF8StringEncoding];
    }
    
     _engine = [AliRtcEngine sharedInstance:self extras:extras];
    ```

2.  订阅RTC本地预览Texture回调。

    在调用接口startPreview（本地预览开启）之后，调用subscribeVideoTexture订阅opengl纹理数据。uid填写空字符串（""），videoSource填写为AliRtcVideosourceCameraLargeType，videoTextureType填写为AliRtcVideoTextureTypePre。

    ```
    // 开启本地预览
    [self.engine startPreview];
    [self.engine subscribeVideoTexture:@"" videoSource:AliRtcVideosourceCameraLargeType videoTextureType:AliRtcVideoTextureTypePre];    /* 美颜订阅openGL纹理数据 */
    ```

3.  RTC SDK Texture回调对接RACE美颜。

    订阅本地预览Texture成功后， RTC SDK会触发以下三个回调：

    -   onVideoTextureCreated：Texture创建回调。在该回调中创建和初始化RACE美颜句柄。

        ```
        - (void)onVideoTextureCreated:(NSString *)uid videoTextureType:(AliRtcVideoTextureType)videoTextureType context:(void *)context
        {
            if(aliRaceBuautyHandle){
                aliyun_beautify_destroy(aliRaceBuautyHandle);
                aliRaceBuautyHandle = nullptr;
            }
        
            aliyun_beautify_create(&aliRaceBuautyHandle);
            aliyun_beautify_setFaceSwitch(aliRaceBuautyHandle, true);
            aliyun_setLogLevel(ALR_LOG_LEVEL_ERROR);
        
            //如需初始化美颜参数请编写代码
            SkinBuffing = 1;
            Sharpen = 1;
            SkinWhitening = 0.5;
            aliyun_beautify_setSkinBuffing(aliRaceBuautyHandle, SkinBuffing);
            aliyun_beautify_setSharpen(aliRaceBuautyHandle, Sharpen);
            aliyun_beautify_setSkinWhitening(aliRaceBuautyHandle, SkinWhitening);
        }
        ```

    -   onVideoTexture：Texture渲染回调。在该回调中，调用RACE接口[aliyun\_beautify\_processTextureToTexture](#li_jet_h73_mqv)进行每一帧的美颜处理。

        **说明：** 请务必判断返回值texId是否有效，当texId小于0时，该回调必须要返回参数中原始的inputTexture。磨皮、锐化、美白等级的控制，请您在该回调中美颜处理前调用相关的接口。

        ```
        - (int)onVideoTexture:(NSString *)uid videoTextureType:(AliRtcVideoTextureType)videoTextureType textureId:(int)textureId width:(int)width height:(int)height rotate:(int)rotate extraData:(long)extraData{
        
            if (beautifySwitchOn == NO) {
                return textureId;
            }
        
            aliyun_beautify_setSkinBuffing(aliRaceBuautyHandle, SkinBuffing);
            aliyun_beautify_setSharpen(aliRaceBuautyHandle, Sharpen);
            aliyun_beautify_setSkinWhitening(aliRaceBuautyHandle, SkinWhitening);
            int texId = aliyun_beautify_processTextureToTexture(aliRaceBuautyHandle,textureId,width,height,ALR_ROTATE_180_CW,0);
        
            if(texId<0) {
               texId = textureId;
            }
            return texId;
        }
        ```

    -   onVideoTextureDestory：Texture销毁回调。在该回调中执行RACE美颜SDK销毁相关的工作。

        ```
        - (void)onVideoTextureDestory:(NSString *)uid videoTextureType:(AliRtcVideoTextureType)videoTextureType{
        
            if(aliRaceBuautyHandle){
                aliyun_beautify_destroy(aliRaceBuautyHandle);
                aliRaceBuautyHandle = nullptr;
            }
        }
        ```

4.  RACE美颜控制。

    基础美颜控制：磨皮、锐化、美白。基础美颜控制必须在onVideoTexture回调中的[aliyun\_beautify\_processTextureToTexture](#li_jet_h73_mqv)之前进行设置。

    人脸检测和美型控制：如果需要打开人脸美型高级功能，通过接口[aliyun\_beautify\_setFaceSwitch](#li_j26_iey_3py)打开开关，有关美型类别的等级设置可以通过接口[aliyun\_beautify\_setFaceShape](#li_p1z_o1e_5wf)进行设置。

    **说明：** 当您不使用人脸美型功能时，请不要打开此功能，否则会有性能损耗。

5.  取消订阅RTC本地预览Texture回调。

    在关闭本地预览前取消订阅本地预览texture回调。

    ```
    [self.engine unSubscribeVideoTexture:@"" videoSource:AliRtcVideosourceCameraLargeType videoTextureType:AliRtcVideoTextureTypePre];
    [self.engine stopPreview];
    ```


