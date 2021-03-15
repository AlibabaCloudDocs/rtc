# Web端集成与使用

通过阅读本文，您可以了解到Web端互动白板SDK的集成及使用方法。

## 环境要求

|浏览器类别|平台|版本要求|
|-----|--|----|
|QQ浏览器（基于Chromium内核）|Windows|Chromium 70或以上版本。|
|360安全浏览器（基于Chromium内核）|Windows|Chromium 70或以上版本。|
|Chrome|Windows、Mac|Chrome 70或以上版本。|
|Safari|Mac|Safari 13或以上版本。|
|New Microsoft Edge（基于Chromium内核）|Windows|Chromium 88或以上版本。|
|搜狗高速浏览器|Windows|11或以上版本。|

## 操作步骤

1.  集成互动白板SDK，此处以Web SDK 0.0.2版本为例介绍。

    ```
    <!DOCTYPE html>
    <html lang="en">
    
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" />
      <meta http-equiv="X-UA-Compatible" content="ie=edge" />
      <title>demo</title>
      <!-- Web SDK版本：0.0.2 -->
      <link rel="stylesheet" href="https://g.alicdn.com/alidocs/wb-sdk/0.0.2/umd/index.css">
    </head>
    
    <body data-spm="13945202">
      <div id="root"></div>
      <script crossorigin src="https://g.alicdn.com/code/lib/babel-polyfill/7.10.4/polyfill.js"></script>
      <script crossorigin
        src="http://g.alicdn.com/alidocs/static/??react/16.13.1/react.production.min.js,react-dom/16.13.1/react-dom.production.min.js"></script>
      <!-- Web SDK版本：0.0.2 -->
      <script crossorigin src="https://g.alicdn.com/alidocs/wb-sdk/0.0.2/umd/index.js"></script>
    </body>
    
    </html>
    ```

    **说明：**

    -   在集成Web SDK之前，需要先引入react，并确保react-dom为16.13.0或以上版本。
    -   如果需要兼容低版本的浏览器，需要引入polyfill。
2.  创建并初始化白板控制器。

    ```
    const AliyunBoard = new AliyunBoard(options: IAliyunBoardOption)
    ```

    IAliyunBoardOption结构如下所示：

    |Key|类型|描述|
    |---|--|--|
    |docKey|string|白板文档的docKey，必传。|
    |module|    ```
{
 document: boolean;
 collaboration: boolean;
}
    ```

|一般不需要传module参数，不传则document和collaboration默认都为true。    -   document：是否初始化白板文档，默认为true。
    -   collaboration：是否初始化协同引擎，默认为true。 |
    |getPreviewUrl|\(url: string, type: AttachmentType\) =\> Promise<string\>|附件URL转预览URL函数，一般为异步函数，主要用于附件的权限控制，如果不传则默认展示插入附件时的URL。type为附件类型（pdf、video、audio）。|
    |maxSceneCount|number|最大可插入的页数，默认为10。|
    |getDocumentData|\(\) =\> Promise<IDocumentData\> \| IDocumentData    ```
其中interface IDocumentData {
  accessToken: string; // 初始化协同引擎所需的token
  collabHost: string; // 协同引擎域名
  permission: number; // 文档权限 (1: 只读，2：编辑)
  userInfo?: {
    avatarUrl?: string; // 用户头像缩略图地址
    userId: string; // 用户ID
    nick?: string; // 昵称
    nickPinyin?: string // 昵称拼音
  };
}
    ```

|当module.document 为true时，该参数为必传项，可以为异步函数。|
    |schema|    ```
{
  size?: {
     width?: number; // 画布宽
     height?: number; // 画布高
     dpi?: number; // dpi
  },
  scale?: number;  // 缩放，默认为1
  slides?: [] ISlide
}
    ```

    ```
其中interface ISlide {
   id?: string;
   background?: string; // 画布背景色
}
    ```

|该参数传入后会覆盖默认的schema对象。|
    |attachmentHost|string|pdf.html页面的host地址。pdf附件需要在iframe中加载出来，需要和白板域名在同一个域下，否则会报access cross-origin frame的错误。|

3.  使用示例说明。

    ```
    import React, { useEffect } from "react";
    import ReactDOM from "react-dom";
    import debounce from "lodash/debounce";
    
    const { Canvas, AliyunBoard } = window.aliyunBoardSDK;
    
    const getDocumentData = () => {
      return new Promise(resolve => {
        /**
         * 客户服务器通过调用白板服务器读取白板文档的数据，客户端通过客户服务器提供的接口获取
         * 白板文档的数据docData，其JSON格式如下所示：
         */
        resolve({
          accessToken: "HnWuPIvSRcXitPhQhadHjtinBHKJwBTA",
          collabHost: "daily-collab.xxxx.test",
          permission: 2,
          userInfo: {
            avatarUrl: "http://www.avatarset/Virginia.jpg",
            userId: "23123",
            nick: "Anne",
            nickPinyin: "Pinyin_Anne",
          },
        });
      });
    };
    
    const aliyunBoard = new AliyunBoard({
        docKey：'xxxx',
      getDocumentData,
        getPreviewUrl: async (url: string, type: string) => {
        // 异步加签
            if (type === 'pdf') {
                const previewUrl = await someAsyncSign(url);
          return previewUrl;
            } else {
                return url
            }
      },
    });
    
    const handleResize = debounce(() => {
      const { stage } = aliyunBoard;
      stage.scale = window.innerWidth / stage.width;
    }, 300);
    
    export const BoardDemo = () => {
      useEffect(() => {
        window.addEventListener("resize", handleResize);
        return () => {
          window.removeEventListener("resize", handleResize);
        };
      }, []);
    
      return (
        <div>
          <Canvas model={aliyunBoard} style={{ height: 500, overflow: "auto" }} />
        </div>
      );
    };
    
    ReactDOM.render(<BoardDemo />, document.getElementById("root"));
    ```


## API

-   内容操作接口

    |API|使用示例|描述|
    |---|----|--|
    |preScene|aliyunBoard.preScene\(\)|向前翻页。|
    |nextScene|aliyunBoard.nextScene\(\)|向后翻页。|
    |gotoScene|aliyunBoard.gotoScene\(pageNum: number\)|跳转至指定页面。|
    |addScene|aliyunBoard.addScene\(\)|增加页面。|
    |removeSceneById|aliyunBoard.removeSceneById\(id: string\)|按ID删除页面。|
    |removeSceneByIndex|aliyunBoard.removeSceneByIndex\(index: number\)|按index删除页面。|
    |setScale|aliyunBoard.setScale\(scale: number\)|缩放画板。|
    |getScale|aliyunBoard.getScale\(\)|获取当前画板缩放值。|
    |undo|aliyunBoard.undo\(\)|撤销上一步操作。|
    |redo|aliyunBoard.redo\(\)|重做上一步操作。|
    |setToolType|aliyunBoard.setToolType\("pointer"\)|指针，支持选中图元，并拖动到指定位置。其中AliyunBoardToolType = "pointer"\|"pen"\|"circle"\|"rect"\|"laser"\|"text"\|"eraser"\|"straight"，其他绘画类接口请参见[绘画接口](#li_zc9_lc1_tyq)。|
    |setBackgroundColorByIndex|aliyunBoard.setBackgroundColorByIndex\(index: number, color: string\)|按index设置画布某页的背景色。|
    |setBackgroundColorById|aliyunBoard.setBackgroundColorById\(id: string, color: string\)|按ID设置画布某页的背景色。|
    |getCurrentScene|aliyunBoard.getCurrentScene\(\)|返回白板画布页Scene对象。|
    |setReadOnly|aliyunBoard.setReadOnly\(readOnly: boolean\)|设置或取消当前画板只读属性。|
    |getReadOnly|aliyunBoard.getReadOnly\(\)|获取画板的只读属性。|

-   绘画接口

    |API|使用示例|描述|
    |---|----|--|
    |setToolType|aliyunBoard.setToolType\("pen"\)|涂鸦（画笔），可设置画笔粗细、颜色。|
    |aliyunBoard.setToolType\("eraser"\)|橡皮擦，支持按图元擦除。|
    |aliyunBoard.setToolType\("text"\)|文本，可设置文本字体样式（加粗、斜体）、字号、颜色。|
    |aliyunBoard.setToolType\("straight"\)|直线绘制，绘制直线样式涂鸦，可设置粗细、颜色。|
    |aliyunBoard.setToolType\("rect"\)|矩形绘制，绘制矩形样式涂鸦，可设置粗细、颜色。|
    |aliyunBoard.setToolType\("circle"\)|椭圆绘制，绘制椭圆样式涂鸦，可设置粗细、颜色。|
    |setCurrentBrush|aliyunBoard.setCurrentBrush\(brush: IBrushItem\)|设置当前工具属性，可设置线条颜色、粗细，文字字号、字体。    ```
其中IBrushItem = {
  strokeWidth?: number; // 线条大小
  stroke?: string; // 线条颜色
  fontFamily?: string; // 字体
  fontSize?: number; // 字号
}
    ``` |
    |clearBoard|aliyunBoard.clearBoard\(\)|清空当前页白板。|

-   其他接口

    |API|使用示例|描述|
    |---|----|--|
    |addImage|aliyunBoard.addImage\(shape: IShapeModel\)|添加图片。如果x, y 不传，则默认插入画布页中间位置，如果图片预览时涉及权限，则需配合[getPreviewUrl](#entry_q81_hgl_zk3)一起使用。    ```
其中IShapeModel = {
 width: number, // 图片展示的宽
 height: number, // 图片展示的高
 x?: number, // 图片相对于画布的X轴位置
 y?: number, // 图片相对于画布的Y轴位置
 href: string // 图片地址或加签需要的ID
}
    ``` |
    |addAttachment|aliyunBoard.addAttachment\(attachment: IAttachment\)|添加附件。目前可添加的附件类型有pdf、mp4、mp3，如果附件预览时涉及权限，则需配合[getPreviewUrl](#entry_q81_hgl_zk3)一起使用。    ```
其中IAttachment = {
 id?: string, // 附件的ID，不传则自动生成随机ID
 type: pdf | mp4| mp3, // 附件类型
 title: string, // 附件标题
 src: string // 附件地址或加签需要的ID
}
    ``` |
    |saveToFile|aliyunBoard.saveToFile\(title: string, type?: string\)|将白板保存为本地文件。    -   title：保存的文件名。
    -   type：保存类型，默认为pdf。

**说明：** 目前仅支持pdf。 |
    |getPreviewData|aliyunBoard.getPreviewData\(index?:number\)|获取序号为index的白板页image对象，如果不传，则返回所有页的image对象列表。返回值：Image\[\] \| Image。|


