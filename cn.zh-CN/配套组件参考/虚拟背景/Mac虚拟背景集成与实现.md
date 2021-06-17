# Mac虚拟背景集成与实现

阿里云RTC提供背景替换和虚化功能，您可以根据实际场景使用该功能完善RTC使用体验。通过阅读本文，您可以了解到虚拟背景的集成与实现方法。

-   环境中已安装Xcode 9.0或以上版本，更多信息，请参见[Xcode](https://apps.apple.com/cn/app/xcode/id497799835?mt=12)。
-   您需要持有Apple开发证书或个人账号。
-   如果使用Mac mini等不包含自带摄像头和麦克风的设备，需要插入外置摄像头和麦克风。

## 环境要求

Mac端具体环境要求，更多信息，请参见[支持的平台](/cn.zh-CN/配套组件参考/虚拟背景/简介.md)。

## 使用限制

背景替换和虚化功能不能同时开启，使用时只能开启其一。

## 集成开发环境

1.  创建Xcode项目项目。

2.  集成阿里云RTC SDK，具体操作，请参见[集成客户端SDK](/cn.zh-CN/快速入门/集成客户端SDK/Mac.md)。

    **说明：** 需要集成RTC SDK 2.4及以上版本，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

3.  集成虚拟背景组件。

    1.  下载并解压虚拟背景组件，下载地址，请参见[组件下载](/cn.zh-CN/配套组件参考/组件下载.md)。

    2.  复制bokeh.framework文件至工程中。

    3.  在**General**页签中，在**Frameworks, Libraries, and Embedded Content**区域中添加bokeh.framework，并将对应的**Embed**属性设置成**Embed & Sign**。

4.  按Commond+B，如果界面提示**Build Success**，表示虚拟背景组件集成成功。


## 功能实现——背景替换

您可以通过调用[enableBackgroundExchange](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)实现背景替换功能，如下所示：

```
//开启背景替换
[self.engine enableBackgroundExchange:YES imagePath:path scalMode:mode];
```

```
//关闭背景替换
[self.engine enableBackgroundExchange:NO imagePath:path scalMode:mode];
```

## 功能实现——背景虚化

您可以通过调用[enableBackgroundBlur](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)实现背景虚化功能，如下所示：

```
//开启背景虚化
[self.engine enableBackgroundBlur:YES blurDegree:degree];
```

```
//关闭背景虚化
[self.engine enableBackgroundBlur:NO blurDegree:degree];
```

