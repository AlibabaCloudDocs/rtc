# Android

通过阅读本文，您可以了解RACE美颜的集成方式及RTC对接RACE美颜的方法。

## 集成RACE SDK

支持maven与aar离线集成两种方式。

-   maven集成
    1.  在项目的project目录的gradle添加以下maven仓库。

        ```
        allprojects {
            repositories {
                google()
                jcenter()
                maven { url "https://maven.aliyun.com/nexus/content/repositories/releases" }
            }
        }
        ```

    2.  在App的gradle下添加RACE依赖。

        ```
        implementation "com.aliyun.race:AliyunRace:1.1.0"
        ```

-   本地集成

    获取AliyunRace.aar文件并添加到工程的libs目录中。


## RTC SDK对接RACE接口说明

以下为RTC SDK对接RACE时需要使用的接口说明，RACE美颜SDK中的其他接口不在本文说明。

|API|描述|
|---|--|
|[AliyunBeautifyNative](#li_v53_ojx_9zf)|创建美颜美型实例。|
|[initialize](#li_1f4_lev_4l9)|初始化美型实例。|
|[setFaceDebug](#li_oz5_ats_910)|美颜美型调试开关。|
|[setLogLevel](#li_azl_7df_7yo)|设置输出日志等级。|
|[setSkinBuffing](#li_ldp_2an_vvq)|设置磨皮参数。|
|[setSharpen](#li_yv2_mfg_byr)|设置锐化参数。|
|[setSkinWhitening](#li_l52_xjs_i7w)|设置美白参数。|
|[setFaceSwitch](#li_8rj_wbf_ogi)|美型开关。|
|[setFaceShape](#li_6r3_whl_gac)|设置美型参数。|
|[processTexture](#li_45i_9bx_2jc)|美颜美型纹理输入渲染。|
|[destroy](#li_afo_8kf_lit)|销毁美颜美型实例。|

-   AliyunBeautifyNative：创建美颜美型实例。

    ```
    AliyunBeautifyNative(Context context);
    ```

    |参数|类型|描述|
    |--|--|--|
    |context|Context|上下文。|

-   initialize：初始化美型实例。

    ```
    int initialize();
    ```

    返回说明

    0表示初始化成功，小于0表示初始化失败。

-   setFaceDebug：美颜美型调试开关。

    ```
    void setFaceDebug(boolean enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|美颜美型Debug开关。|

-   setLogLevel：设置输出日志等级。

    ```
    void setLogLevel(int level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |level|int|日志等级。|

-   setSkinBuffing：设置磨皮等级。

    ```
    int setSkinBuffing(float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |level|float|磨皮等级，取值：0~1。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   setSharpen：设置锐化等级。

    ```
    int setSharpen(float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |level|float|锐化等级，取值：0~1。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   setSkinWhitening：设置美白等级。

    ```
    int setSkinWhitening(float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |level|float|美白等级，取值：0~1。|

    返回说明

    0表示设置成功，小于0表示设置失败。

-   setFaceSwitch：美型开关。

    ```
    void setFaceSwitch(boolean enable);
    ```

    |参数|类型|描述|
    |--|--|--|
    |enable|boolean|是否开启人脸检测及美型处理，取值：    -   true：开启。
    -   false：关闭。 |

-   setFaceShape：设置美型等级。

    ```
    int setFaceShape(int type, float level);
    ```

    |参数|类型|描述|
    |--|--|--|
    |type|int|美型类型。详情请参见[type定义](#p_hkx_fti_dui)。|
    |level|float|美型等级。|

    返回说明

    0表示设置成功，小于0表示设置失败。

    type定义和建议范围如下：

    ```
    public static final int ALR_FACE_SHAPE_TYPE_CUT_CHEEK      = 0; //颧骨，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_CUT_FACE       = 1; //削脸，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_THIN_FACE      = 2; //瘦脸，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_LONG_FACE      = 3; //脸长，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_LOWER_JAW      = 4; //下巴缩短，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_HIGHER_JAW     = 5; //下巴拉长，取值：-1~1
    public static final int ALR_FACE_TYPE_THIN_JAW             = 6; //瘦下巴，取值：-1~1
    public static final int ALR_FACE_TYPE_THIN_MANDIBLE        = 7; //瘦下颌，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_BIG_EYE        = 8; //大眼，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_EYE_ANGLE1     = 9; //眼角1，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_CANTHUS        = 10;//眼距，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_CANTHUS1       = 11;//拉宽眼距，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_EYE_ANGLE2     = 12;//眼角2，取值：-1~1
    public static final int ALR_FACE_TYPE_EYE_TDANGLE          = 13;//眼睛高度，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_THIN_NOSE      = 14;//瘦鼻，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_NOSEWING       = 15;//鼻翼，取值：0~1
    public static final int ALR_FACE_SHAPE_TYPE_NASAL_HEIGHT   = 16;//鼻长，取值：-1~1
    public static final int ALR_FACE_TYPE_NOSE_TIP_HEIGHT      = 17;//鼻头长，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_MOUTH_WIDTH    = 18;//唇宽，取值：-1~1
    public static final int ALR_FACE_TYPE_MOUTH_SIZE           = 18;//嘴唇大小，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_MOUTH_HIGH     = 20;//唇高，取值：-1~1
    public static final int ALR_FACE_SHAPE_TYPE_PHILTRUM       = 21;//人中
    ```

-   processTexture：美颜美型纹理输入渲染。

    ```
    int processTexture(int texture, int width, int height, int rotation, int flag);
    ```

    |参数|类型|描述|
    |--|--|--|
    |texture|int|输入图像纹理。|
    |width|int|输入图像纹理宽度。|
    |height|int|输入图像纹理高度。|
    |rotation|int|输入图像纹理旋转角度（顺时针）。|
    |flags|int|RTC对接时该参数必须设置为0。|

    返回说明

    返回textureId表示渲染成功，小于0表示渲染失败。

-   destroy：销毁美颜美型实例。

    ```
    void destroy();
    ```


## RTC对接RACE美颜

1.  设置RTC Engine美颜通道。

    RTC中使用外置美颜功能时，必须打开Engine的美颜通道。美颜通道的打开是通过扩展字段添加`jsonObject.addProperty("user_specified_video_preprocess", "TRUE");`，jsonObject转化成string后传入到AliRtcEngine.getInstance的第二个字段extra里面。详细使用方式如下所示：

    ```
    JSONObject jsonObject = new JSONObject();
    //初始化支持美颜的SDK
    jsonObject.put("user_specified_video_preprocess", "TRUE");
    //实例化必须在主线程进行
    mAliRtcEngine = AliRtcEngine.getInstance(getApplicationContext(), jsonObject.toString());
    ```

2.  订阅RTC本地预览Texture回调。

    在调用本地预览开启接口`startPreview`之后，调用`RegisterTexturePreObserver`订阅openGL纹理数据。userId填写空字符串（""）。

    **说明：** observer为实例化接口类AliTextureObserver。

    ```
    //订阅美颜texture回调
    mAliRtcEngine.RegisterTexturePreObserver("", raceBeautyImp);
    ```

3.  RTC SDK Texture回调对接RACE美颜。

    订阅本地预览Texture成功后， RTC SDK会触发以下三个回调：

    -   onTextureCreate：Texture创建回调。在该回调中创建和初始化RACE美颜。

        ```
        @Override
        public void onTextureCreate(String callId, long context) {
            if (mBeautifyNative == null) {
                mBeautifyNative = new AliyunBeautifyNative(mContext);
            }
            //初始化
            mBeautifyNative.initialize();
            //美颜开关
            mBeautifyNative.setFaceSwitch(true);
        }
        ```

    -   onTexture：Texture渲染回调。在该回调中调用RACE接口[processTexture](#li_45i_9bx_2jc)进行每一帧的美颜处理。

        **说明：** 请务必判断返回值texId是否有效，当texId小于0时，该回调必须要返回参数中原始的inputTexture。磨皮、锐化、美白等级的控制，请您在该回调中美颜处理接口processTexture之前调用相关的接口。

        ```
        @Override
        public int onTexture(String callId, int inputTexture, int textureWidth, int textureHeight, int stride, int rotate, long extra) {
            int texId = inputTexture;
            if (!isOn) {
                return inputTexture;
            }
            mBeautifyNative.setSkinBuffing(mSkinBuffing);
            mBeautifyNative.setSkinWhitening(mSkinWhitening);
            mBeautifyNative.setSharpen(mSharpen);
            if (mBeautifyNative != null) {
                texId = mBeautifyNative.processTexture(inputTexture, textureWidth, textureHeight, rotate, 0);
                if (texId < 0) {
                    texId = inputTexture;
                }
            }
            return texId;
        }
        ```

    -   onTextureDestroy：Texture销毁回调。在该回调中执行RACE美颜SDK销毁相关的工作。

        ```
        @Override
        public void onTextureDestroy(String callId) {
            if (mBeautifyNative != null) {
                mBeautifyNative.destroy();
            }
        }
        ```

4.  RACE美颜控制。

    基础美颜控制：磨皮、锐化、美白。基础美颜控制必须在onTexture回调中的[processTexture](#li_45i_9bx_2jc)之前进行设置。

    人脸检测和美型控制：如果需要打开人脸美型高级功能，通过接口[setFaceSwitch](#li_8rj_wbf_ogi)打开开关，有关美型类别的等级设置可以通过接口[setFaceShape](#li_6r3_whl_gac)进行设置。

    **说明：** 当您不再使用人脸美型功能时，请您关闭此功能，否则会有性能损耗。

5.  取消订阅RTC本地预览Texture回调。

    在关闭本地预览前取消订阅本地预览texture回调。

    ```
    mAliRtcEngine.UnRegisterTexturePreObserver("");
    ```


