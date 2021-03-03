# iOS和Mac端集成与使用

通过阅读本文，您可以了解到iOS和Mac端互动白板SDK的集成及使用方法。

项目已配置有效的开发者证书。

## 使用说明

iOS和Mac端SDK接口的功能是通过函数`- (void)invokeAPI:(NSString *)methodName parameter:(NSString *)parameter completionHandler:(void (^ _Nullable)(_Nullable id result, NSError * _Nullable error))completionHandler;`调用Web端对应功能的接口实现的，根据Web端接口的参数个数不同调用规则如下所示：

-   当Web端接口只有一个参数时，此处以调用Web端绘制椭圆的接口`setToolType("circle")`为例：

    ```
    [boardView invokeAPI:@"setToolType" parameter:@"circle" completionHandler:nil];
    ```

-   当Web端接口有多个参数时，需要将参数转换成json格式，此处以调用Web端按index设置画布某页的背景色接口`setBackgroundColorByIndex(1, "#FFF")`为例：

    ```
    invokeAPI:@"setToolType" parameter:@"{\"index\":1, \"color\":\"#FFF\"}" completionHandler:nil];
    ```


更多Web端SDK接口，详情请参见[Web端API](/cn.zh-CN/互动白板解决方案（邀测中）/客户端集成/Web端集成与使用.md)。

## 环境要求

|类别|要求|
|--|--|
|操作系统|Mac OS X 10.10或以上版本。|
|开发环境|Xcode 9.0或以上版本。|

## 操作步骤

1.  集成互动白板SDK。

    1.  下载并解压互动白板SDK，下载地址，请参见[开发支持](/cn.zh-CN/互动白板解决方案（邀测中）/简介.md)。

    2.  打开Xcode工程，选择待运行的Target。

    3.  单击**Build Phases**页签，在**Link Binary with Libraries**区域单击**+**添加AliWhiteboard.framework（iOS依赖库）或AliWhiteboardMac.framework（Mac依赖库）。

2.  在需要使用SDK API的文件中引入头文件。

    -   iOS端：

        ```
        #import <AliWhiteboard/AliWhiteboard.h>
        ```

    -   Mac端：

        ```
        #import <AliWhiteboard/AliWhiteboardMac.h> //AliWhiteboardMac.h 内部会import AliWhiteboard.h
        ```

    头文件AliWhiteboard.h内容如下所示：

    ```
    #import <Foundation/Foundation.h>
    #import <WebKit/WebKit.h>
    NS_ASSUME_NONNULL_BEGIN
    
    /// 回调protocol
    @protocol AliWhiteboardDelegate <NSObject>
    #define kEventBoardCreated   @"E_BoardCreated"
    #define kEventBoardDestroyed @"E_BoardDestroyed"
    @required
    - (void)eventNotify:(NSString *)eventName eventData:(NSString *)eventData;
    @end
    
    @interface WhiteboardConfig : NSObject
    @property (nonatomic, strong) NSString* configData;
    @property (nonatomic, strong) NSString* docData;
    @end
    
    /// 白板功能类
    @interface AliWhiteboard : WKWebView
    
    - (instancetype)initWithConfig:(WhiteboardConfig *)boardConfig
                     eventDelegate:(id<AliWhiteboardDelegate>) eventDelegate
                             frame:(CGRect)frame;
    
    /// @param methodName 需要被执行方法名
    /// @param parameter 方法对应的参数
    /// @param completionHandler 方法结果
    - (void)invokeAPI:(NSString *)methodName parameter:(NSString *)parameter completionHandler:(void (^_Nullable)(NSString * response))completionHandler;
    
    /// SDK版本
    + (NSString *)sdkVersion;
    @end
    
    NS_ASSUME_NONNULL_END
    ```

3.  使用示例说明。

    -   创建白板实例

        ```
        WhiteboardConfig *boardConfig = [[WhiteboardConfig alloc] init];
        bool canMultipleEdit = NO; //是否支持多人协同编辑
        if (canMultipleEdit) {
          boardConfig.configData = @"{}";
          boardConfig.docData = @"{\"accessToken\":\"bspdlhBnWnexpFFHfrbrutBwQaqPFffa\",\"collabHost\":\"collab-cn-shanghai.dingtalk.com\",\"permission\":2,\"userInfo\":{\"avatarUrl\":\"http://www.avatarset/Christina.jpg\",\"nick\":\"Christina\",\"nickPinyin\":\"Pinyin_Christina\",\"userId\":\"1234123\"},\"docKey\":\"oJGq7rgmRwGRnAKe\"}";
                /* 客户服务器通过调用白板服务器读取白板文档的数据，客户端通过客户服务器提供的接口获取白板文档的数据docData，其JSON格式如下所示：
                {
                    "accessToken": "bEVijFCQILnwlbfaesbeLxoZOFmgCQtx",
                    "collabHost": "pre-collab-cn-shanghai.dingtalk.com",
                    "permission": 2,
                    "userInfo": {
                    "avatarUrl": "http://www.avatarset/Harold.jpg",
                    "nick": "Harold",
                    "nickPinyin": "Pinyin_Harold",
                    "userId": "1234123"
                    },
                    "docKey": "KM7qeYmW6J6kqpj8"
                }
                */
        } else {
          //单机版配置
          boardConfig.configData = @"{\"module\":{\"document\":false}}";
          boardConfig.docData = @"{}";
        }
        
        // 大小位置
        CGRect frame = CGRectMake(0, 0,
                                      self.view.frame.size.width,
                                      self.view.frame.size.height);
        AliWhiteboard * boardController = [[AliWhiteboard alloc]
                                             initWithConfig:boardConfig
                                              eventDelegate:self       //回调事件
                                                      frame:frame];
        [self.view addSubview:boardView];
        ```

    -   绘画示例

        ```
        // 绘制椭圆
        [boardView invokeAPI:@"setToolType" parameter:@"circle" completionHandler:nil];
        // 绘制矩形
        [boardView invokeAPI:@"setToolType" parameter:@"rect" completionHandler:nil];
        // 清空
        [boardView invokeAPI:@"clearBoard" parameter:@"" completionHandler:nil];
        ```

    -   回调示例

        ```
        // MARK: - AliWhiteboardDelegate
        - (void)eventNotify:(nonnull NSString *)eventName eventData:(nonnull NSString *)eventData {
            NSLog(@"eventName: %@, eventData: %@", eventName, eventData);
            if ([eventName isEqualToString:kEventBoardCreated]) {
                //白版创建成功事件，自此之后，app可以通过调用invokeAPI来实现白版操作
            } else {
                //Other events that you may care
            }
        }
        ```


