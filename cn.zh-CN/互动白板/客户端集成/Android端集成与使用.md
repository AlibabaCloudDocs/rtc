# Android端集成与使用

通过阅读本文，您可以了解到Android端互动白板SDK的集成及使用方法。

## 使用说明

Android端SDK接口的功能是通过函数`void invokeAPI(String method, String params, @Nullable InvokeAPIResultListener listener)`调用Web端对应功能的接口实现的，根据Web端接口的参数个数不同调用规则如下所示：

-   当Web端接口只有一个参数时，此处以调用Web端绘制椭圆的接口`setToolType("circle")`为例：

    ```
    whiteBoard.invokeAPI("setToolType", "circle");
    ```

-   当Web端接口有多个参数时，需要将参数转换成JSON格式，此处以调用Web端按index设置画布某页的背景色接口`setBackgroundColorByIndex(1, "#FFF")`为例：

    ```
    whiteBoard.invokeAPI("setBackgroundColorByIndex", "{\"index\":1, \"color\":\"#FFF\"}");
    ```


更多Web端SDK接口，详情请参见[Web端API](/cn.zh-CN/互动白板/客户端集成/Web端集成与使用.md)。

## 环境要求

|类别|要求|
|--|--|
|API版本|API 19：Android 4.4或以上版本。|
|开发环境|Android Studio 2.0或以上版本。|

## 操作步骤

1.  集成互动白板SDK。

    1.  下载并解压互动白板SDK，下载地址，请参见[开发支持](/cn.zh-CN/互动白板/简介.md)。

    2.  复制SDK文件AliyunWhiteBoardSdk.aar到App模块下的libs文件夹中。

2.  在AndroidManifest.xml中配置App的权限。

    ```
    <uses-permission android:name="android.permission.INTERNET"/>
    ```

3.  使用示例说明。

    -   创建白板实例

        ```
        //构建docInfo
        String configData;
        String docData;
        bool canMultipleEdit = false; //是否支持多人协同编辑
        if (canMultipleEdit) {
            configData = "{}";
          docData = "{\"accessToken\":\"bspdlhBnWnexpFFHfrbrutBwQaqP****\",\"collabHost\":\"collab-cn-shanghai.dingtalk.com\",\"permission\":2,\"userInfo\":{\"avatarUrl\":\"http://www.avatarset/Christina.jpg\",\"nick\":\"Christina\",\"nickPinyin\":\"Pinyin_Christina\",\"userId\":\"1234123\"},\"docKey\":\"oJGq7rgmRwGR****\"}";
                /* 客户服务器通过调用白板服务器读取白板文档的数据，客户端通过客户服务器提供的接口获取白板文档的数据docData，其JSON格式如下所示：
                {
                    "accessToken": "bEVijFCQILnwlbfaesbeLxoZOFmg****",
                    "collabHost": "pre-collab-cn-shanghai.dingtalk.com",
                    "permission": 2,
                    "userInfo": {
                    "avatarUrl": "http://www.avatarset/Harold.jpg",
                    "nick": "Harold",
                    "nickPinyin": "Pinyin_Harold",
                    "userId": "1234123"
                    },
                    "docKey": "KM7qeYmW6J6k****"
                }
                */
        } else {
            //单机版配置
            configData = "{\"module\":{\"document\":false}}";
            docData = "{}";
        }
        DocInfo docInfo = new DocInfo(configData, docData);
        
        //注册回调事件
        BoardEventListener boardEventListener = new BoardEventListener() {
          @Override
          public void onEventNotify(String eventName, String eventData) {
            Log.i("AliyunWhiteBoard", "eventName：" + eventName + "Data：" + eventData);
            if (eventName == kEventBoardCreated) {
              //白板创建成功事件，自此之后，app可以通过调用AliyunWhiteBoard.invokeAPI来实现白板操作
            } else {
              //其他事件，日志，异常等
            }
          }
        };
        
        AliyunWhiteBoard whiteBoard = null;
        
        //选择WebView容器
        /*
        默认使用内建的原生WebView，也可以使用三方（推荐UC内核），可参考DefaultWebView
        实现一个三方内核的IWhiteboardWebView的接口适配即可。
        */
        boolean useBuiltInWebView = true;
        if (useBuiltInWebView) {
          //使用内建原生WebView，低版本设备上可能会有小部分兼容性问题
          whiteBoard = new AliyunWhiteBoard(this, docInfo, boardEventListener);
        } else {
          //使用三方WebView，如UC内核，可以兼容低版本设备
          //你可以参考DefaultWebView来实现一个IWhiteboardWebView接口，进行适配
          IWhiteboardWebView webView = new DefaultWebView(this);
          whiteBoard = new AliyunWhiteBoard(webView, docInfo, boardEventListener);
        }
        
        //创建（异步），等待onEventNotify的kEventBoardCreated即表示创建成功
        whiteBoard.start();
        
        // 将白板 View 添加到布局中
        FrameLayout boardContainer = findViewById(R.id.board_container);
        boardContainer.addView(whiteBoard.getBoardRenderView());
        ```

    -   绘画示例

        ```
        // 设置为圆形
        whiteBoard.invokeAPI("setToolType", "circle");
        // 设置为矩形
        whiteBoard.invokeAPI("setToolType", "rect");
        // 清空白板
        whiteBoard.invokeAPI("clearBoard", "");
        ```

    -   生命周期回调示例

        ```
        whiteBoard.onPause();
        ```

        ```
        whiteBoard.onResume();
        ```

        ```
        whiteBoard.onDestroy();
        ```


