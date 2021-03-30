# Mac

通过阅读本文，您可以了解到屏幕分享的使用方法。

## 推流端

1.  启动屏幕分享。

    ```
    // 配置屏幕分享推流
    [self.engine configLocalScreenPublish:YES];
    // 启动推流
    [self.engine publish:^(int err) {
    }];
    .....
    ```

2.  停止屏幕分享。

    ```
    // 配置屏幕分享停止
    [self.engine configLocalScreenPublish:NO];
    // 启动停推
    [self.engine publish:^(int err) {
    }];
    ```


## 订阅端

订阅端用户可通过自动或手动方式订阅推流端屏幕分享视频流，并设置对应View显示，详情请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/iOS和Mac SDK/AliRtcEngine接口.md)。

