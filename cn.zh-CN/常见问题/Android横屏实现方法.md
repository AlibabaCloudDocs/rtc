# Android横屏实现方法 {#concept_111357_zh .concept}

当您成功集成SDK，并想实现移动端横屏进行实时音视频通信。您可以通过本文档，了解实现本地横屏的代码方法，帮助您更好的体验阿里云音视频通信服务。

SDK暂不支持横竖屏切换，可通用下面两种方式实现本地横竖屏效果，但实际推出去的流不会有变化。

-   直接对当前Activity进行配置，需要您先配置AndroidManifest。

    ``` {#codeblock_it2_klm_bw5 .language-xml}
    <activity
    android:name="<Your Activity>"
    android:configChanges="orientation|keyboardHidden|screenSize"
    android:screenOrientation="sensor">     
    ```

    然后在Activity中重载onConfigurationChanged，监听当前横竖屏变化，并处理相关View成横屏或竖屏适配。

    ``` {#codeblock_p3i_84i_wze .language-java}
    @Override
    public void onConfigurationChanged(Configuration newConfig) {
    super.onConfigurationChanged(newConfig);
    if (newConfig.orientation == Configuration.ORIENTATION_PORTRAIT) {
    setPortraitView();
    } else if (newConfig.orientation == Configuration.ORIENTATION_LANDSCAPE) {
     setLandscapeView();
    }
    }       
    ```

    **说明：** 这个方法将会在屏幕旋转变化时调用，可以在这里做出我们在屏幕变化时想要的操作，并且不会重启activity。但它只能一次旋转90度，如果旋转180度，onConfigurationChanged函数不会被调用。

-   添加横竖屏监听事件OrientationEventListener，监听各个旋转角度的处理。

    ``` {#codeblock_o2f_ej5_7zk .language-java}
    mEventListener = new OrientationEventListener(MainActivity.this) {
    @Override
    public void onOrientationChanged(int orientation) {
    if (orientation == OrientationEventListener.ORIENTATION_UNKNOWN) {
    // 手机平放时，检测不到有效的角度
    return;
    }
    // 只检测是否有四个角度的改变
    if (orientation > 350 || orientation < 10) {
    // 0度：手机默认竖屏状态（home键在正下方）
    setPortraitView();
    } else if (orientation > 80 && orientation < 100) {
    // 90度：手机顺时针旋转90度横屏（home建在左侧）
    setLandscapeView();
    } else if (orientation > 170 && orientation < 190) {
    // 180度：手机顺时针旋转180度竖屏（home键在上方）
    setPortraitView();
    } else if (orientation > 260 && orientation < 280) {
    // 270度：手机顺时针旋转270度横屏，（home键在右侧）
    setLandscapeView();
    }
    }
    };
    mEventListener.enable(); //打开监听
    mEventListener.disable(); //关闭监听    
    ```

    **说明：** 监听事件不需要配置AndroidManifest，能够更详细的监听旋转的角度。


如果上述适配对于部分机型无效，可以用Android平台层API，对View进行相应角度旋转即可。

