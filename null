# 如何实现多模块共享AVAudioSession

iOS端RTC SDK和其他音频模块对AVAudioSession都有控制权，您需要根据实际情况分配AVAudioSession的控制权限。通过阅读本文，您可以了解怎样设置SDK对AVAudioSession的控制权限。

## 背景信息

默认情况下，RTC SDK和App对AVAudioSession都有控制权，为了保证RTC SDK通话功能的正常使用，RTC SDK会提高对AVAudioSession使用的优先级。然而在某些场景下，例如当需要暂停RTC SDK并且使用其他音频组件（音乐播放器、其他第三方音频组件等），此时需要限制RTC SDK对AVAudioSession的控制权限。

## 解决方案

RTC SDK为您提供以下接口方法设置SDK对AVAudioSession的控制权限，如果您调用了该方法限制了RTC SDK的控制权限，则需要App自行维护以保证SDK功能正常，App也可以随时使用此方法把管理权限交还给RTC SDK。

```
- (int)setAudioSessionOperationRestriction:(AliRtcAudioSessionOperationRestriction)restriction;
```

|名称|类型|描述|
|--|--|--|
|restriction|[AliRtcAudioSessionOperationRestriction](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|控制权限。|

