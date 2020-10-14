---
keyword: iOS横屏
---

# iOS切换横竖屏实现方法

当您成功集成SDK，并想实现移动端切换横竖屏进行实时音视频通信。您可以阅读本文，了解实现本地切换横竖屏的代码方法，帮助您更好的体验阿里云音视频通信服务。

## 横竖屏模式切换

正常情况下竖屏模式推流分辨率宽<高，例如：480\*640；横屏模式推流分辨率宽\>高，例如：640\*480。

如果您想切换横竖屏，请调用setDeviceOrientationMode方法进行切换横竖屏。该方法调用成功返回0，失败返回其他。

**说明：** 仅允许在推流和预览之前进行设置。

```
//接口方法
- (int)setDeviceOrientationMode:(AliRtcOrientationMode)mode;
//示例方法
[[UIDevice currentDevice] setValue:@(UIDeviceOrientationLandscapeLeft) forKey:@"orientation"];
[self.engine setDeviceOrientationMode:(AliRtcOrientationModeLandscapeLeft)];
```

|参数|类型|描述|
|--|--|--|
|mode|[AliRtcOrientationMode](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|设备方向。取值： -   AliRtcOrientationModePortrait（默认值）：固定竖屏模式。
-   AliRtcOrientationModeLandscapeLeft：固定左横屏模式。
-   AliRtcOrientationModeLandscapeRight：固定右横屏模式。
-   AliRtcOrientationModeAuto：自适应横竖屏模式。 |

**说明：**

-   当应用切换横竖屏时，调用此接口进行设备方向切换，摄像头采集会随机进行切换。
-   1.17之前版本仅支持固定竖屏模式，不支持动态横竖屏切换，即只要当前未打开摄像头采集（未开启预览并且未开始推视频流），设置可生效；打开摄像头后再设置不生效。

## 竖屏模式切换推流分辨率宽高

竖屏模式推流分辨率宽\>高，例如：640\*480（摄像头保持竖屏采集）。

您可以调用setVideoSwapWidthAndHeight方法切换分辨率。

**说明：** 请您在调用setVideoProfile和joinChannel之前进行切换。

```
- (void)setVideoSwapWidthAndHeight:(BOOL)swapWidthAndHeight forTrack:(AliRtcVideoTrack)track;
```

|参数|类型|描述|
|--|--|--|
|swapWidthAndHeight|BOOL|是否交换宽和高，取值：YES\|NO（默认值）|
|track|[AliRtcVideoTrack](/cn.zh-CN/SDK参考/iOS和Mac SDK/数据类型.md)|视频Track类型|

**说明：** 您可以在以下情况调用该接口进行切换宽和高：

-   竖屏模式下竖屏推流，推流分辨率需要宽\>高。
-   横屏模式下横屏推流，推流分辨率需要宽<高。

