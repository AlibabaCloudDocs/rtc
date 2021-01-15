# extras参数配置说明

本文为您介绍extras参数配置的说明、使用场景和实现方式。

## 功能说明

extras字符配置的功能列表如下表所示。

|参数|功能描述|取值|适用平台|
|--|----|--|----|
|user\_specified\_aec|音频3A：回声消除|TRUE：开启，FALSE：关闭|Android、iOS、Mac、Windows|
|user\_specified\_ans|音频3A：自动降噪|TRUE：开启，FALSE：关闭|Android、iOS、Mac、Windows|
|user\_specified\_agc|音频3A：自动增益|TRUE：开启，FALSE：关闭|Android、iOS、Mac、Windows|
|user\_specified\_engine\_mode|音质模式|TRUE：开启，FALSE：关闭|Android、iOS、Mac、Windows|
|user\_specified\_scene\_mode|场景模式|TRUE：开启，FALSE：关闭|Android、iOS、Mac、Windows|
|user\_specified\_video\_preprocess|使用三方美颜处理视频|TRUE：开启，FALSE：关闭|Android、iOS|
|user\_specified\_groupid|1对1模式|TRUE：开启，FALSE：关闭|Android、iOS、Mac、Windows|

## 音频3A

使用场景

-   当移动端（Android和iOS）硬件效果不满足要求时，可以将这三个开关均设置为TRUE，表示启用阿里云RTC提供的软件音频处理算法。能达到效果与音乐模式或媒体模式一样。
-   当PC端或移动端有外接声卡设备，而且声卡设备自带音频信号处理功能时，为保真音质，建议手动将相关功能设置为FLASE。
-   如果不设置任何3A参数，即表示不激活3A开关的功能，系统会按照当前选择的模式（默认模式，音乐模式等）运行。

实现方式

```
JsonObject jsonObject = new JsonObject();

jsonObject.put("user_specified_aec","TRUE");
jsonObject.put("user_specified_ans","TRUE");
jsonObject.put("user_specified_agc","TRUE");

AliRtcEngine engine= AliRtcEngine.getInstance(context, jsonObject.toString());
```

## 音质模式与场景模式

功能说明

-   在一些比较专业的场景里，用户对声音的效果需求很高。阿里云RTC提供多种组合方案。
-   开发者根据对音质、场景等的不同需求，自由定制不同的音频属性，获得最佳实时互动效果。

模式说明

-   音质模式

    |音质模式值列举|模式名称|声道数|采样率|编码码率|
    |-------|----|---|---|----|
    |ENGINE\_LOW\_QUALITY\_MODE|低音质模式|1|8 kHz|12 Kbps|
    |ENGINE\_BASIC\_QUALITY\_MODE|标准音质模式|1|16 kHz|24 Kbps|
    |ENGINE\_HIGH\_QUALITY\_MODE|高音质模式|1|48 kHz|48 Kbps|

-   场景模式

    |场景模式值列举|场景名称|特性|
    |-------|----|--|
    |SCENE\_DEFAULT\_MODE|默认场景|一般的音视频通信场景推荐使用。|
    |SCENE\_EDUCATION\_MODE|教育场景|优先保证音频连续性与稳定性。|
    |SCENE\_MEDIA\_MODE|媒体场景|保真人声与音乐音质，连麦直播间推荐使用。|
    |SCENE\_MUSIC\_MODE|音乐场景|高保真音乐音质，乐器教学等对音乐音质有要求的场景推荐使用。|


场景搭配示例

|场景|音质模式|场景模式|特性|
|--|----|----|--|
|普通语音聊天室|ENGINE\_BASIC\_QUALITY\_MODE|SCENE\_DEFAULT\_MODE|音质较好，优先保证通话质量，传输流畅。适用于对音质没有极致追求的场景。|
|语音教学小班课|ENGINE\_HIGH\_QUALITY\_MODE|SCENE\_DEFAULT\_MODE|音质高清，优先保证通话质量，传输流畅。适用于对语音音质有极致追求的场景。|
|乐器教学小班课|ENGINE\_HIGH\_QUALITY\_MODE|SCENE\_MUSIC\_MODE|音质高清，优先音乐质量，传输流畅。适用于对音乐音质有极致追求的场景。|
|直播连麦（语聊）|ENGINE\_HIGH\_QUALITY\_MODE|SCENE\_MEDIA\_MODE|传输流畅、音质高清，保证语音质量的同时，兼顾音乐音质。适用于既有语音又有音乐的聊天场景。|
|直播连麦（唱歌）|ENGINE\_HIGH\_QUALITY\_MODE|SCENE\_MUSIC\_MODE|传输流畅、音质高清，优先音乐质量，配合提供的各种音效。适用于唱歌乐器弹奏为主的场景。|
|小型穿戴设备（如电话手表）|ENGINE\_LOW\_QUALITY\_MODE|SCENE\_DEFAULT\_MODE|传输流畅、音质较好，优先保证语音可听可懂，功耗低。|

实现方式

```
JsonObject jsonObject = new JsonObject();
//开启音乐场景下高音质模式
jsonObject.put("user_specified_engine_mode","ENGINE_HIGH_QUALITY_MODE");
jsonObject.put("user_specified_scene_mode","SCENE_MUSIC_MODE");

AliRtcEngine engine= AliRtcEngine.getInstance(context, jsonObject.toString());
```

## 使用三方美颜处理视频

功能说明

-   在接⼊前，我们需要在SDK的实例extra字段中添加开关：user\_specified\_video\_preprocess：TRUE。
-   通常客户集成以后反馈⾃⼰能看到美颜，对⽅看不到，就是因为这个没有设置。

实现方式

```
JsonObject jsonObject = new JsonObject();
jsonObject.put("user_specified_video_preprocess","TRUE");

AliRtcEngine engine= AliRtcEngine.getInstance(context, jsonObject.toString());
```

## 1对1模式

1对1模式自动推流，只推相机大流，不推次要相机流。

场景描述

随着近些年音视频的应用越来越广泛，衍生了多样的在线教育、实时通信等场景。在教育场景下1对1指导更是广泛使用。下面是一些典型的1对1场景。 比如1对1线上课外辅导、1对1线上语言教学、1对1线上音乐陪练和1对1线上面试等。

实现方式

```
JsonObject jsonObject = new JsonObject();
jsonObject.put("user_specified_groupid","1v1");

AliRtcEngine engine= AliRtcEngine.getInstance(context, jsonObject.toString());
```

