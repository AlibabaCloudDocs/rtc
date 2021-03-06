---
keyword: [rtc, web, 设备检测]
---

# Web

RTC SDK为您提供了设备检测和管理的功能，您可以在加入频道之前检查硬件设备是否能正常工作。通过阅读本文，您可以了解设备检测和管理的方法。

## 功能简介

RTC SDK通过调用内部方法实现设备检测和管理。例如，您可以查询设备信息、检测摄像头是否正常工作、检测音频设备是否正常录音及播放、设置摄像头方向或者切换音频设备（麦克风和扬声器）等。

## 实现方法

以下为常用的设备检测和管理方法，更多信息，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)。

getDevices：获取设备信息，返回摄像头和音频输入设备。如果外接设备重新插拔后获取不到设备信息，请尝试重新启动电脑。

```
aliWebrtc.getDevices().then((re)=>{
}).catch((error)=>{ 
  console.log(error.message)
});
```

