# Windows虚拟背景集成与实现

阿里云RTC提供背景替换和虚化功能，您可以根据实际场景使用该功能完善RTC使用体验。通过阅读本文，您可以了解到虚拟背景的集成与实现方法。

环境中已安装Visual Studio 2010或以上版本。

## 环境要求

Windows端具体环境要求，更多信息，请参见[支持的平台](/cn.zh-CN/配套组件参考/虚拟背景/简介.md)。

## 使用限制

背景替换和虚化功能不能同时开启，使用时只能开启其一。

## 集成开发环境

1.  创建Visual Studio项目。

2.  集成阿里云RTC SDK，具体操作，请参见[集成客户端SDK](/cn.zh-CN/快速入门/集成客户端SDK/Windows.md)。

    **说明：** 需要集成RTC SDK 2.4及以上版本，详情请参见[SDK下载](/cn.zh-CN/SDK参考/SDK下载.md)。

3.  集成虚拟背景组件。

    1.  下载并解压虚拟背景组件，下载地址，请参见[组件下载](/cn.zh-CN/配套组件参考/组件下载.md)。

    2.  复制库文件至程序的执行路径下。

        -   如果系统为32位，请将x86目录下的pthreadVC2.dll和bokeh.dll文件复制到程序的执行路径下。
        -   如果系统为64位，请将x64目录下的pthreadVC2.dll、bokeh.dll、tensorflowlite\_c.dll和vcruntime140\_1.dll文件复制到程序的执行路径下。
4.  编译。如果编译成功，表示虚拟背景组件集成成功。


## 功能实现——背景替换

您可以通过调用[EnableBackgroundExchange](/cn.zh-CN/SDK参考/Windows SDK/AliEngine接口.md)实现背景替换功能，如下所示：

```
  BackgroundExchangeDlg dlg;
  dlg.enableBgExchangeCallback = [this, &dlg]
  {
    CString imagePath = dlg.mBgImagePath;
    if (PathFileExists(imagePath))
    {
      std::string  filePath = CT2A(imagePath);
      AliEngineBokehScaleModel scaleMode = (dlg.mBgExchangeMode != 0 ? AliEngineBokehScaleModelFill :  AliEngineBokehScaleModelCrop);
      mpEngine->EnableBackgroundExchange(true,filePath.c_str(), scaleMode);
    }
  };

  dlg.disableBgExchangeCallback = [this, &dlg]
  {
    AliEngineBokehScaleModel scaleMode = (dlg.mBgExchangeMode != 0 ? AliEngineBokehScaleModelFill : AliEngineBokehScaleModelCrop);
    mpEngine->EnableBackgroundExchange(false, "", scaleMode);
  };

  dlg.DoModal();
```

## 功能实现——背景虚化

您可以通过调用[EnableBackgroundBlur](/cn.zh-CN/SDK参考/Windows SDK/AliEngine接口.md)实现背景虚化功能，如下所示：

```
  BackgroundBlurDlg dlg;
  dlg.mBlurValue = m_nBackgroundBlurDegree;
  dlg.enableBackgroundBlurCallback = [this, &dlg]
  {
    m_nBackgroundBlurDegree = dlg.mBlurValue;
    mpEngine->EnableBackgroundBlur(true, m_nBackgroundBlurDegree);
  };

  dlg.disableBackgroundBlurCallback = [this]
  {
    mpEngine->EnableBackgroundBlur(false, 0);
  };

  dlg.DoModal();
```

