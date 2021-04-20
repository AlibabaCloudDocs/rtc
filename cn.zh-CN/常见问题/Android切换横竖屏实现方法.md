---
keyword: 切换横竖屏
---

# Android切换横竖屏实现方法

通过阅读本文，您可以了解Android端实现横竖屏切换的方法。

## 横竖屏模式切换

正常情况下竖屏模式推流分辨率宽<高，例如：480\*640；横屏模式推流分辨率宽\>高，例如：640\*480。

调用setDeviceOrientationMode方法进行切换横竖屏：

```
//接口方法
public abstract void setDeviceOrientationMode(AliRtcEngine.AliRtcOrientationMode mode);
```

|名称|类型|描述|
|--|--|--|
|mode|[AliRtcOrientationMode](/cn.zh-CN/SDK参考/Android SDK/数据类型.md)|设备方向。取值： -   AliRtcOrientationModePortrait（默认值）：固定竖屏模式。
-   AliRtcOrientationModeLandscapeLeft：固定左横屏模式。
-   AliRtcOrientationModeLandscapeRight：固定右横屏模式。
-   AliRtcOrientationModeAuto：自适应模式。 |

**说明：**

-   当应用切换横竖屏时，调用此接口进行设备方向切换，摄像头采集会随机进行切换。
-   竖屏模式时不需要调用此接口。
-   1.17之前版本仅支持固定竖屏模横式，即只要当前未打开摄像头采集（未开启预览并且未开始视频推流），设置可生效。打开摄像头后再调用该接口不会生效，不支持动态横竖屏切换。

如果您的设备不支持自适应模式，而您想要设置自适应模式，您需要监听旋转的方向，然后根据角度设置当前的横竖屏。具体操作如下：

1.  设置自适应模式。

    ```
    //设置横屏竖屏自适应模式。
     mAliRtcEngine.setDeviceOrientationMode(AliRtcOrientationModeAuto);
     setRequestedOrientation(SCREEN_ORIENTATION_UNSPECIFIED);
    ```

2.  设置setRequestedOrientation监听旋转角度。

    ```
    /**
      * 监听旋转角度
      */
    private OrientationEventListener mOrientationEventListener;
        @Override
        protected void onResume() {
            if (null==mOrientationEventListener) {
                mOrientationEventListener = new OrientationEventListener(this) {
                    @Override
                    public void onOrientationChanged(int orientation) {
                        if (orientation == OrientationEventListener.ORIENTATION_UNKNOWN) {
                            return;  //手机平放时，检测不到有效的角度。
                        }
                        //备注：如果您的应用有固定横竖屏模式和自适应模式切换。请添加判断语句，只有自适应模式才根据角度设置横竖屏方向。
    
                        //只检测是否有四个角度的改变，设置自适应模式后，只需要修改setRequestedOrientation即可。
                        if (orientation > 350 || orientation < 10) { //0度，竖直。
                            setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_PORTRAIT);
                        } else if (orientation > 80 && orientation < 100) { //90度，右横屏。
                            setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_REVERSE_LANDSCAPE);
                        } else if (orientation > 170 && orientation < 190) { //180度，倒立。
                            setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_PORTRAIT);
                        } else if (orientation > 260 && orientation < 280) { //270度，左横屏。
                            setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE);
                        } else {
                            return;
                        }
                    }
                };
                mOrientationEventListener.enable();
            }
        }
    
        @Override
        protected void onPause() {
            super.onPause();
            //停止监听。
            if (null != mOrientationEventListener) {
                mOrientationEventListener.disable();
                mOrientationEventListener = null;
            }
        }
    ```


