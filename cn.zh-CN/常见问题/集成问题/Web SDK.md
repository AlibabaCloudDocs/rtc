---
keyword: [Web SDK, 常见问题]
---

# Web SDK

## 摄像头和麦克风无法使用

![未使用https](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6341158951/p63712.jpeg)

-   AppServer和网页需要使用https协议。
-   检测是否禁用或者占用摄像头和麦克风设备。

## Web端和其它端无法互通

需要在其他端调用setH5CompatibleMode，设置兼容模式。

## Android设备不能进行Web通信

检测Android设备是否支持H264协议。

**说明：** Android设备进行Web页面通信，需要安卓设备支持H264协议。

## Web SDK无法内嵌App内

Web SDK不支持内嵌App内。

## Web SDK是否支持小程序

web SDK 暂不支持微信小程序、支付宝小程序。

## 无法显示本地摄像头

-   AppServer和网页需要使用https协议。
-   查看设备是否被禁用。
-   检查硬件是否可用。

## SDK如果只使用音频，是否可以没有摄像头

如果只使用音频，可以没有摄像头。

