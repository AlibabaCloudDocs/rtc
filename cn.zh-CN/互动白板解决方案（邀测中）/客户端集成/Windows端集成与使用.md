# Windows端集成与使用

通过阅读本文，您可以了解到Windows端互动白板SDK的集成及使用方法。

## 环境要求

|类别|要求|
|--|--|
|操作系统|Winsows 7或以上版本。|
|开发环境|Visual Studio版本不限，建议Visual Studio 2017。|

## 使用说明

Windows端SDK接口的功能是通过函数`bool InvokeAPI(const char *method_name, const char *parameter, ApiResponseCB api_callback)`调用Web端对应功能的接口实现的，根据Web端接口的参数个数不同调用规则如下所示：

-   当Web端接口只有一个参数时，此处以调用Web端绘制椭圆的接口`setToolType("circle")`为例：

    ```
    board_controller->InvokeAPI("setToolType", "circle", nullptr);
    ```

-   当Web端接口有多个参数时，需要将参数转换成json格式，此处以调用Web端按index设置画布某页的背景色接口`setBackgroundColorByIndex(1, "#FFF")`为例：

    ```
    board_controller->InvokeAPI("setToolType", "{\"index\":1, \"color\":\"#FFF\"}", nullptr);
    ```


更多Web端SDK接口，详情请参见[Web端API](/cn.zh-CN/互动白板解决方案（邀测中）/客户端集成/Web端集成与使用.md)。

## 操作步骤

1.  集成互动白板SDK。

    1.  下载并解压互动白板SDK，下载地址，请参见[开发支持](/cn.zh-CN/互动白板解决方案（邀测中）/简介.md)。

        解压后文件夹结构如下所示：

        |目录|说明|
        |--|--|
        |WhiteboardSdkWin\\sdk\\include|SDK头文件。|
        |WhiteboardSdkWin\\sdk\\lib|SDK依赖库。|
        |WhiteboardSdkWin\\sdk\\symbol|SDK二进制符号文件。|
        |WhiteboardSdkWin\\demo\\bin|Demo程序。|
        |WhiteboardSdkWin\\demo\\src|Demo源代码（VS2017 MFC工程）。|

    2.  导入SDK文件到项目中。

        复制WhiteboardSdkWin\\sdk\\include和WhiteboardSdkWin\\sdk\\lib到VS工程目录中。

2.  在需要使用SDK的文件中引入头文件并添加好依赖库。

    ```
    #include "AliWhiteboardSDK.h"
    
    #pragma comment(lib, "AliWhiteboardSDK.lib")
    ```

    头文件AliWhiteboard.h内容如下所示：

    ```
    #ifndef ALI_WHITEBOARD_SDK_H__
    #define ALI_WHITEBOARD_SDK_H__
    
    #include "windows.h"
    #include <functional>
    
    #ifdef BUILD_ALIWB_DLL
    /* Building library. */
    #define ALIWB_EXTERN __declspec(dllexport)
    #else
    #define ALIWB_EXTERN __declspec(dllimport)
    #endif
    
    namespace AliWhiteboard {
    
        //Global Init/Shutdown
        void ALIWB_EXTERN InitSdk(HINSTANCE hInstance);
    
        void ALIWB_EXTERN ShutdownSdk();
    
        //Get the sdk version, the return buffer should be freed by calling FreeBuffer()
        ALIWB_EXTERN const char *GetSDKVersion();
    
        void ALIWB_EXTERN FreeBuffer(void *buffer);
    
        typedef enum { kDebug = 0, kWarning = 1, kError = 2 } LogLevel;
        void ALIWB_EXTERN SetLogCallback(std::function<void(LogLevel level, const char *log_str)> log_callback);
    
        struct WhiteBoardConfig {
            HWND parent_wnd = nullptr;
            std::string config_data;
            std::string doc_data;
        };
    
        //white board controller
        class ALIWB_EXTERN AliWhiteboardController {
        public:
            static AliWhiteboardController *CreateWhiteboardController(const WhiteBoardConfig& config);
    
            static void DestroyWhiteboardController(AliWhiteboardController *whiteboardController);
    
            virtual ~AliWhiteboardController() = default;
    
        public:
    
            typedef std::function<void(const char *api_response)> ApiResponseCB;
            virtual bool InvokeAPI(const char *method_name, const char *parameter, ApiResponseCB api_callback) = 0;
    
            // Events
            #define kEventBoardCreated   "E_BoardCreated"
            #define kEventBoardDestroyed "E_BoardDestroyed"
            typedef std::function<void(const char *event_name, const char *event_data)> EventCB;
            virtual void RegisterEvent(EventCB event_callback) = 0;
    
            // UI position
            virtual bool SetBoardViewPos(int x, int y, int width, int height) = 0;
    
            // Debug tools
            virtual void ShowDevTools() = 0;
        };
    };// namespace AliWhiteboard
    
    #endif// ALI_WHITEBOARD_SDK_H__
    ```

3.  使用示例说明。

    -   全局初始化与销毁

        ```
        //WinMain函数入口进行
        //1. 初始化
        AliWhiteboard::InitSdk(nullptr);
        //2. 设置日志回调，可以将sdk日志输出到项目自己的日志系统
        AliWhiteboard::SetLogCallback([](AliWhiteboard::LogLevel level, const std::string &log_str) {
          ::OutputDebugStringA(log_str.c_str());
        });
        
        //使用白板
        
        //WinMain退出前进行
        //3. SDK资源释放
        AliWhiteboard::ShutdownSdk();
        ```

    -   白板实例创建与销毁

        ```
        //构建config，填充config_data与doc_data
        AliWhiteboard::WhiteBoardConfig config;
        config.parent_wnd = hParentWnd;
        bool can_multiple_edit = false; //是否支持多人协同编辑
        if (can_multiple_edit) {
            config.config_data = "{}";
          config.doc_data = "{\"accessToken\":\"bspdlhBnWnexpFFHfrbrutBwQaqPFffa\",\"collabHost\":\"collab-cn-shanghai.dingtalk.com\",\"permission\":2,\"userInfo\":{\"avatarUrl\":\"http://www.avatarset/Christina.jpg\",\"nick\":\"Christina\",\"nickPinyin\":\"Pinyin_Christina\",\"userId\":\"1234123\"},\"docKey\":\"oJGq7rgmRwGRnAKe\"}";
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
            config.config_data = "{\"module\":{\"document\":false}}";
            config.doc_data = "{}";
        }
        
        //创建白板
        AliWhiteboard::AliWhiteboardController* board_controller =
        AliWhiteboard::AliWhiteboardController::CreateWhiteboardController(config);
        
        //注册事件回调
        board_controller->RegisterEvent([](const std::string &event_name, const std::string &event_data) {
          //这里是非UI线程，如需要操作UI，请在此处切换至UI线程
          if (event_name == kEventBoardCreated) {
                //白板创建成功事件，来自于CreateWhiteboardController
            //注意：只有当此事件来之后，才可以调用后面提到的invokeAPI
          } else if (event_name == kEventBoardDestroyed) {
            //白板销毁事件，来自于DestroyWhiteboardController，请在收到此事件后再关闭父窗口
          } else {
            //其他事件，日志，异常等
          }
        });
        
        //使用白板
        //参考#白板画笔、绘图接口调用
        
        //销毁
        //销毁成功后（上面event_name == kEventBoardDestroyed），才能关闭父窗口
        AliWhiteboard::AliWhiteboardController::DestroyWhiteboardController(board_controller);
        board_controller = nullptr;
        ```

    -   白板窗口位置和大小的设置

        ```
        //在父窗口的WM_SIZE事件处理函数内，设置白板窗口位置、大小与父窗口适配
        RECT parentRect;
        ::GetClientRect(hParentWnd, &parentRect);
        int cx = parentRect.right - parentRect.left;
        int cy = parentRect.bottom - parentRect.top;
        board_controller->SetBoardViewPos(parentRect.left, parentRect.top, cx, cy);
        ```

    -   绘画示例

        ```
        //绘制椭圆
        board_controller->InvokeAPI("setToolType", "circle", nullptr);
        //绘制矩形
        board_controller->InvokeAPI("setToolType", "rect", nullptr);
        //清空
        board_controller->InvokeAPI("clearBoard", "", nullptr);
        ```


