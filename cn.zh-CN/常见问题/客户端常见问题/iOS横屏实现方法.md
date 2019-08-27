# iOS横屏实现方法 {#concept_111356_zh .concept}

本文档为您介绍了实现iOS横屏的两种方法。

SDK 暂不支持横竖屏切换，可通用下面两种方式实现本地横竖屏效果，但实际推出去的流不会有变化。

-   当app支持横屏时。

    您在旋转设备至横屏时，需要对视频通话界面做支持横竖屏切换布局。对于本地绘制视频和远端用户绘制视频的AliVideoCanvas实例对应的AliRenderView实例，只需对AliRenderView实例的frame做相应改变即可实现横屏效果，不需要对AliVideoCanvas实例做额外设置。

-   当app不支持横屏时。

    如果您要在视频通话界面实现强制横屏效果，AliRenderView实例的superview可通过改变transform来做横屏转换，但需要对AliRenderView实例做反向变换，不需要对相应的AliVideoCanvas实例做额外设置。如果只改变superview的transform会出现界面绘制的镜头角度和实际视频角度有偏差。


示例代码

``` {#codeblock_miy_d57_4dx .language-objc}
superview.transform = CGAffineTransformMakeRotation(M_PI_2);//对renderView的父视图做正向旋转变换
superview.frame = superViewNewFrame;//设置父视图的横屏布局
renderView.transform = CGAffineTransformMakeRotation(-M_PI_2);//canvas的randerView做反向旋转
renderView.frame = renderViewNewFrame;//设置横屏位置布局      
```

