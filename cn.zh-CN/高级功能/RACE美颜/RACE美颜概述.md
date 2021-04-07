# RACE美颜概述

通过阅读本文，您可以了解RACE美颜功能的基本信息。

## 简介

渲染计算平台RACE（Render And Compute Everything Engine）美颜包含图像及视频渲染能力，如滤镜、特效、贴纸、美颜美型、人脸检测等算法能力，可以覆盖多种拍摄、剪辑场景，满足客户丰富的产品需求。

## 快速集成

-   Android端，支持maven与本地aar离线集成两种方式：

    -   maven依赖集成方式：maven \{ url "https://maven.aliyun.com/nexus/content/repositories/releases" \} implementation 'com.aliyun.race:AliyunRace:1.1.1'。
    -   本地集成方式：获取AliyunRace.aar文件并添加到工程中。
    具体操作，请参见[Android端接入](/cn.zh-CN/高级功能/RACE美颜/Android.md)。

-   iOS端，支持pod与本地framework离线集成两种方式：

    -   pod依赖集成方式：pod 'AliyunRace', '1.1.1'。
    -   本地集成方式：将AliyunRace.framework、Face3D.framwork、opencv2.framework添加到工程中。
    具体操作，请参见[iOS端接入](/cn.zh-CN/高级功能/RACE美颜/iOS.md)。


## 美颜美型功能

-   功能介绍

    高级美颜包含美白、磨皮、锐化等功能；美型默认包含优雅、精致、网红、可爱、婴儿五种脸型。该功能提供包括眼睛、鼻子、嘴形等22种预置形状，便于客户根据产品需求扩展丰富的功能。

-   数据结构及接口介绍
    -   美型形状类型。对于每一种形状，您还可以将参数值设置超出下列定义的范围，进行综合调试效果。

        ```
        /**
         * 美型形状类型
         */
        typedef enum ALRFaceShape
        {
            ALR_FACE_TYPE_CUT_CHEEK       = 0, //颧骨      [0,1]
            ALR_FACE_TYPE_CUT_FACE        = 1, //削脸      [0,1]
            ALR_FACE_TYPE_THIN_FACE       = 2, //瘦脸      [0,1]
            ALR_FACE_TYPE_LONG_FACE       = 3, //脸长      [0,1]
            ALR_FACE_TYPE_LOWER_JAW       = 4, //下巴缩短  [-1,1]
            ALR_FACE_TYPE_HIGHER_JAW      = 5, //下巴拉长  [-1,1]
            ALR_FACE_TYPE_THIN_JAW        = 6, //瘦下巴    [-1,1]
            ALR_FACE_TYPE_THIN_MANDIBLE   = 7, //瘦下颌    [0,1]
            ALR_FACE_TYPE_BIG_EYE         = 8, //大眼     [0,1]
            ALR_FACE_TYPE_EYE_ANGLE1      = 9, //眼角1     [0,1]
            ALR_FACE_TYPE_CANTHUS         = 10,//眼距     [-1,1]
            ALR_FACE_TYPE_CANTHUS1        = 11,//拉宽眼距 [-1,1]
            ALR_FACE_TYPE_EYE_ANGLE2      = 12,//眼角2    [-1,1]
            ALR_FACE_TYPE_EYE_TDANGLE     = 13,//眼睛高度 [-1,1]
            ALR_FACE_TYPE_THIN_NOSE       = 14,//瘦鼻     [0,1]
            ALR_FACE_TYPE_NOSE_WING       = 15,//鼻翼     [0,1]
            ALR_FACE_TYPE_NASAL_HEIGHT    = 16,//鼻长     [-1,1]
            ALR_FACE_TYPE_NOSE_TIP_HEIGHT = 17,//鼻头长   [-1,1]
            ALR_FACE_TYPE_MOUTH_WIDTH     = 18,//唇宽     [-1,1]
            ALR_FACE_TYPE_MOUTH_SIZE      = 19,//嘴唇大小 [-1,1]
            ALR_FACE_TYPE_MOUTH_HIGH      = 20,//唇高     [-1,1]
            ALR_FACE_TYPE_PHILTRUM        = 21, //人中
            ALR_FACE_TYPE_MAX             = 22
        } ALRFaceShape;
        ```

    -   创建高级美颜实例。

        ```
        /**
         * 创建美颜美型实例
         * @param handle 美颜美型句柄指针
         * @param resDir 资源文件目录绝对路径
         * @param rid 数据上报标识符
         * @param lid 日志上报标识符
         * @return 成功返回 ALR_OK，否则返回 < 0
         */
        int aliyun_beautify_create(race_t *handle, const char *resDir, int64_t rid = -1, int64_t lid = -1);
        ```

    -   销毁高级美颜实例。

        ```
        /**
         * 销毁美颜美型实例
         * @param handle 美颜美型句柄
         */
        void aliyun_beautify_destroy(race_t handle);
        ```

    -   高级美颜调试开关。

        ```
        /**
         * 美颜美型调试开关
         * @param handle 美颜美型句柄
         * @param enable 调试开启标志
         * @return 成功返回 ALR_OK，否则返回 < 0
         */
        int aliyun_beautify_setFaceDebug(race_t handle, bool enable);
        ```

    -   美型开关。

        ```
        /**
         * 美型开关
         * @param handle 美颜美型句柄
         * @param switchOn 是否开启人脸检测及美型处理
         */
        void aliyun_beautify_setFaceSwitch(race_t handle, bool switchOn);
        ```

    -   设置美型参数。

        ```
        /**
         * 设置美型参数
         * @param handle 美颜美型句柄
         * @param level 美型等级参数，可以超出 ALRFaceShape 中定义的参数范围
         * @return 成功返回 ALR_OK，否则返回 < 0
         */
        int aliyun_beautify_setFaceShape(race_t handle, ALRFaceShape type, float level);
        ```

    -   高级美颜渲染。

        ```
        /**
         *  高级美颜，输入是类型 CMSampleBufferRef 的图像数据，返回与输入同样大小的纹理 id
         *  @param handle 创建成功的句柄
         *  @param sampleBuffer 图像数据 CMSampleBufferRef
         *  @return 成功则返回渲染纹理 id，失败返回 0
         */
        int aliyun_beautify_processSampleBuffer(race_t handle, void *sampleBuffer);
        /**
         * 单输入美颜美型渲染
         * @param handle 美颜美型句柄
         * @param buffer CPU图像内存地址
         * @param bufferSize CPU图像内存字节数
         * @param format 图像像素格式
         * @param width 图像宽度
         * @param height 图像高度
         * @param bytesPerRow CPU图像内存一行的字节数
         * @param rotation 图像旋转角度（顺进针方向）
         * @param range 颜色色域范围
         * @param standard 色彩标准
         * @param flags 详见 ALR_FLAG_XXX 定义，如 OES 纹理、镜像、输出图像旋转等
         * @return 成功则返回输出纹理句柄，否则返回 < 0
         */
        int aliyun_beautify_processBufferToTexture(race_t handle,
                                                   uint8_t *buffer,
                                                   uint32_t bufferSize,
                                                   aliyun_image_format_t format,
                                                   uint32_t width,
                                                   uint32_t height,
                                                   uint32_t bytesPerRow,
                                                   aliyun_rotation_t rotation,
                                                   aliyun_color_range_t range,
                                                   aliyun_color_standard_t standard,
                                                   uint8_t flags);
        /**
         * 美颜美型纹理输入渲染
         * @param handle 美颜美型句柄
         * @param textureIn 输入图像纹理
         * @param width 输入图像纹理宽度
         * @param height 输入图像纹理高度
         * @param rotation 输入图像纹理旋转角度（顺时针）
         * @param flags 详见 ALR_FLAG_XXX 定义，如 OES 纹理、镜像、输出图像旋转等
         * @return 成功则返回输出纹理句柄，否则返回 < 0
         */
        int aliyun_beautify_processTextureToTexture(race_t handle,
                                                    uint32_t textureIn,
                                                    uint32_t width,
                                                    uint32_t height,
                                                    aliyun_rotation_t rotation,
                                                    uint8_t flags);
        /**
         * 双输入美颜美型渲染
         * @param handle 美颜美型句柄
         * @param textureIn GPU纹理 id
         * @param buffer CPU图像内存地址
         * @param bufferSize CPU图像内存字节数
         * @param format 图像像素格式
         * @param width 图像宽度
         * @param height 图像高度
         * @param bytesPerRow CPU图像内存一行的字节数
         * @param rotation 图像旋转角度（顺进针方向）
         * @param flags 详见 ALR_FLAG_XXX 定义，如 OES 纹理、镜像、输出图像旋转等
         * @return 成功则返回输出纹理句柄，否则返回 < 0
         */
        int aliyun_beautify_processDualInputToTexture(race_t handle,
                                                      uint32_t textureIn,
                                                      uint8_t *buffer,
                                                      uint32_t bufferSize,
                                                      aliyun_image_format_t format,
                                                      uint32_t width,
                                                      uint32_t height,
                                                      uint32_t bytesPerRow,
                                                      aliyun_rotation_t rotation,
                                                      uint8_t flags);
        ```

-   接口集成示例

    ```
    #include "aliyun_beautify.h"
    
    race_t beautify = nullptr;
    
    // 创建高级美颜实例
    // iOS: RACE内部自动从Framework读取，可传空字串。
    // Android: 外部需将asserts/race_res目录拷贝到sdcard或者可访问的路径，并将此路径作为参数传入如/sdcard
    aliyun_beautify_create(&beautify, "");
    
    // 设置美颜参数
    aliyun_beautify_setSkinBuffing(beautify, skinBuffingValue); //磨皮
    aliyun_beautify_setSkinWhitening(beautify, skinWhiteningValue); //美白
    aliyun_beautify_setSharpen(beautify, sharpenValue); //锐化
    
    // 设置美型参数
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_BIG_EYE, bigEyeValue);//大眼
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_LONG_FACE, longFaceValue);//脸长
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_CUT_FACE, cutFaceValue);//削脸
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_THIN_FACE, thinFaceValue);//瘦脸
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_LOWER_JAW, lowerJawValue);//下巴
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_MOUTH_WIDTH, mouthWidthValue);//唇宽
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_THIN_NOSE, thinNoseValue);//瘦鼻
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_THIN_MANDIBLE, thinMandibleValue);//下颌
    aliyun_beautify_setFaceShape(beautify, ALR_FACE_TYPE_CUT_CHEEK, cutCheekValue);//颧骨
    
    // iOS: 美颜美型效果处理，返回渲染后的结果纹理id。
    textureOut = aliyun_beautify_processSampleBuffer(beautify, sampleBuffer);
    
    // Android & iOS: 单纹理输入
    textureOut = aliyun_beautify_processTextureToTexture(beautify,
                                                         textureIn,
                                                         width, height,
                                                         rotation, flags);
    
    // Android & iOS: CPU内存+GPU纹理双输入
    textureOut = aliyun_beautify_processDualInputToTexture(beautify,
                                                           textureIn,
                                                           buffer, bufferSize, 
                                                           format, width, height,
                                                           bytePerRow,
                                                           rotation, flags);
    
    // 销毁美颜美型实例
    aliyun_beautify_destroy(beautify);
    ```


## 人脸检测

-   功能介绍

    在静态照片、图像或动态视频流中，使用人脸检测技术可以快速准确地辨别出单张或多张人脸，并检测出人脸所在的位置。

-   数据结构及接口介绍
    -   数据结构。

        ```
        // 宏定义
        #define ALR_FACE_DETECT_MODE_VIDEO           0x10000000  // video
        #define ALR_FACE_DETECT_MODE_IMAGE           0x20000000  // image
        /// 网络模型
        #define ALR_FACE_DETECT_NETWORK_HBN          0x00000001  // HBN
        #define ALR_FACE_DETECT_NETWORK_FASTERRCNN   0x00000002  // Faster RCNN
        
        // 人脸区域
        typedef struct aliyun_rect_t
        {
            int left;    //left of face rectangle
            int top;     //top of face rectangle
            int right;   //right of face rectangle
            int bottom;  //bottom of face rectangle
        } aliyun_rect_t;
        
        // 点的数据结构
        typedef struct aliyun_point_t
        {
            float x;
            float y;
        } aliyun_point_t;
        
        // 一张人脸的数据结构
        typedef struct aliyun_face_t
        {
            aliyun_rect_t rect;                   // 人脸区域
            float score;                          // 置信度
            aliyun_point_t landmarks_array[106];  // 106关键点
            float landmarks_visible_array[106];  // 106关键点遮挡情况
            float yaw;                           // 水平转角，真实度量的左负右正
            float pitch;                         // 俯仰角，真实度量的上负下正
            float roll;                          // 旋转角，真实度量的左负右正
            float eye_distance;                  // 两眼间距
            int faceID;
        } aliyun_face_t;
        
        // 多张人脸的数据结构
        typedef struct aliyun_face_info_t
        {
            aliyun_face_t *p_faces;                 //face info
            int face_count;                      //face detection num
        } aliyun_face_info_t;
        
        // 人脸检测参数类型 
        typedef enum
        {
            ALR_FACE_PARAM_DETECT_INTERVAL        = 1,  // 人脸检测的帧率（默认值30，即每隔30帧检测一次）
            ALR_FACE_PARAM_SMOOTH_THRESHOLD       = 2,  // 人脸关键点平滑系数（默认值0.25）
            ALR_FACE_PARAM_POSE_SMOOTH_THRESHOLD  = 4,  // 姿态平衡系数(0,1]，越大平滑程度越大
            ALR_FACE_PARAM_DETECT_THRESHOLD       = 5,  // 人脸检测阈值(0,1)，阈值越大，误检越少，但漏检测会增加, default 0.95 for faster rcnn; default 0.3 for SSD
            ALR_FACE_PARAM_ALIGNMENT_INTERVAL     = 11, // 人脸检测对齐间隔，默认1，一般不要超过5
            ALR_FACE_PARAM_MAX_FACE_SUPPORT       = 12, // 最多支持检出的人脸个数，最大设为32, 主要针对faster rcnn
            ALR_FACE_PARAM_DETECT_IMG_SIZE        = 13, // 人脸检测输入的图像大小，default： 240 for faster rcnn, recommend set 320 for tiny face detection
        } aliyun_face_param_type_t;
        ```

    -   创建人脸检测实例。

        Android端C语言接口：

        ```
        /**
         * 创建人脸检测句柄
         * @param handle
         * @param det_paraPath 人脸检测模型的路径
         * @param pts_paraPath 关键点检测模型的路径
         * @param config
         * @return == 0 OK; < 0 error
         */
        RACE_EXTERN int aliyun_face_create(race_t* handle,
                                           JNIEnv* env,
                                           const char* det_paraPath,
                                           const char* pts_paraPath,
                                           unsigned int config);
        ```

        iOS端C语言接口：

        ```
        /**
         * 创建人脸检测句柄
         * iOS端推荐使用接口
         * @param handle with initialed
         * @param config 检测图片：ALR_FACE_DETECT_MODE_IMAGE，检测视频：ALR_FACE_DETECT_MODE_VIDEO
         * @return == 0 OK;  < 0 error
         */
        RACE_EXTERN int aliyun_face_default_create(race_t* handle, unsigned int config);
        
        /**
         * 创建人脸检测句柄
         * @param handle with initialed
         * @param det_paraPath 人脸检测模型的绝对路径
         * @param pts_paraPath 关键点检测模型的绝对路径
         * @param config 检测图片：ALR_FACE_DETECT_MODE_IMAGE，检测视频：ALR_FACE_DETECT_MODE_VIDEO，人脸检测模型选择模型1，则增加ALR_FACE_DETECT_NETWORK_HBN，选择模型3，则增加ALR_FACE_DETECT_NETWORK_FASTERRCNN
         * @return == 0 OK; < 0 error
         */
        RACE_EXTERN int aliyun_face_create(race_t* handle,
                               const char* det_paraPath,
                               const char* pts_paraPath,
                               unsigned int config);
        ```

    -   设置人脸检测参数。

        ```
        /**
         * 设置人脸检测参数
         * @param handle with initialed
         * @param type face_param_type
         * @param value new threshold
         * @return = 0 OK; < 0 error
         */
        RACE_EXTERN int aliyun_face_setParam(race_t handle, aliyun_face_param_type_t type, float value);
        ```

    -   调用人脸检测接口。

        ```
        /**
         * 人脸检测
         * @param handle with initialed
         * @param buffer input image
         * @param format support type BGR、RGBA、RGB、Y(GRAY)，推荐使用RGBA
         * @param width  width
         * @param height height
         * @param bytesPerRow 用于检测的图像的跨度(以像素为单位)，即每行的字节数
         * @param rotation rotate image to frontalization for face detection
         * @param config MOBILE_FACE_DETECT, or MOBILE_FACE_DETECT|MOBILE_EYE_BLINK et.al 默认值0
         * @param outRotation result process rotate specific angle first, angle =  0/90/180/270
         * @param outFlipAxis  flip x/y 0(no flip)/1(flip X axis)/2(flip Y axis)
         * @param faceInfo store face detetion result
         * @return = 0 OK; < 0 error
         */
        RACE_EXTERN int aliyun_face_detect(race_t handle,
                                           uint8_t *buffer,
                                           aliyun_image_format_t format,
                                           uint32_t width,
                                           uint32_t height,
                                           uint32_t bytesPerRow,
                                           aliyun_rotation_t rotation,
                                           uint32_t config,
                                           aliyun_rotation_t outRotation,
                                           uint32_t outFlipAxis,
                                           aliyun_face_info_t* faceInfo);
        ```

    -   销毁人脸检测实例。

        ```
        /**
         * 销毁人脸检测句柄
         * @param handle  with initialed
         */
        RACE_EXTERN void aliyun_face_destroy(race_t handle);
        ```

-   接口集成示例

    ```
    race_t handle = nullptr;
    // for Android
    aliyun_face_create(handle,
                       "/sdcard/race_res/models/0_3/fd_00002_3",
                       "/sdcard/race_res/models/0_3/fd_00002_12",
                       ALR_FACE_DETECT_NETWORK_FASTERRCNN | ALR_FACE_DETECT_MODE_VIDEO);
    // for iOS
    aliyun_face_default_create(handle, ALR_FACE_DETECT_MODE_VIDEO);
    // 设置检测间隔，推荐设置为5
    aliyun_face_setParam(handle, ALR_FACE_PARAM_DETECT_INTERVAL, 5);
    
    aliyun_face_info_t info;
    aliyun_face_detect(handle,
                       buffer,
                       ALR_IMAGE_FORMAT_NV21,
                       1280,
                       720,
                       1280,
                       ALR_ROTATE_90_CW,
                       0,
                       ALR_ROTATE_90_CW,
                       0,
                       &info);
    
    aliyun_face_destroy(handle);
    ```


