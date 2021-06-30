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

1.  集成互动白板SDK，此处以Web SDK 0.0.8版本为例介绍。

    -   JS示例：

        ```
        <!DOCTYPE html>
        <html lang="en">
        
        <head>
          <meta charset="UTF-8" />
          <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" />
          <meta http-equiv="X-UA-Compatible" content="ie=edge" />
          <title>demo</title>
          <!-- Web SDK版本：0.0.8 -->
          <link rel="stylesheet" href="https://g.alicdn.com/alidocs/wb-sdk/0.0.8/universal/index.css">
        </head>
        
        <body>
          <div id="root"></div>
          <script crossorigin src="https://g.alicdn.com/code/lib/babel-polyfill/7.10.4/polyfill.js"></script>
          <!-- Web SDK版本：0.0.8 -->
          <script crossorigin src="https://g.alicdn.com/alidocs/wb-sdk/0.0.8/universal/index.js"></script>
        </body>
        
        </html>
        ```

        **说明：**

        -   项目需引用universal目录下的index.js。
        -   如果需要兼容低版本的浏览器，需要引入polyfill。
    -   React示例：

        ```
        <!DOCTYPE html>
        <html lang="en">
        <head>
          <meta charset="UTF-8" />
          <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" />
          <meta http-equiv="X-UA-Compatible" content="ie=edge" />
          <title>demo</title>
          <!-- Web SDK版本：0.0.8 -->
          <link rel="stylesheet" href="https://g.alicdn.com/alidocs/wb-sdk/0.0.8/umd/index.css">
        </head>
        
        <body>
          <div id="root"></div>
          <script crossorigin src="https://g.alicdn.com/code/lib/babel-polyfill/7.10.4/polyfill.js"></script>
          <script crossorigin
            src="//g.alicdn.com/alidocs/static/??react/16.13.1/react.production.min.js,react-dom/16.13.1/react-dom.production.min.js"></script>
          <!-- Web SDK版本：0.0.8 -->
          <script crossorigin src="https://g.alicdn.com/alidocs/wb-sdk/0.0.8/umd/index.js"></script>
        </body>
        
        </html>
        ```

        **说明：**

        -   在集成Web SDK之前，需要先引入react，并确保react-dom为16.13.1或以上版本。
        -   如果需要兼容低版本的浏览器，需要引入polyfill。
2.  创建并初始化白板控制器，使用示例，请参见[步骤 3](#step_fay_m3u_r26)。

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
  wsDomain: string; // 高性能长连接服务地址
}
    ```

|当module.document 为true时，该参数为必传项，可以为异步函数。|
    |schema|    ```
{
  size?: {
     width?: number; // 画布宽，单位：厘米
     height?: number; // 画布高，单位：厘米
     dpi?: number; // dpi（dot per inch）
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

|白板初始化时使用的schema对象，传入后会覆盖默认的schema对象。示例代码如下所示：    -   覆盖默认的背景色

        ```
{
 slides:[{ background: 'red'}]
}
        ```

    -   覆盖默认的画布大小（默认值为size: \{width: 21, height: 29.7, dpi: 144\}）

        ```
{
 size: {width: 15, height: 22, dpi: 144}
}
        ```

**说明：**

    -   计算方式：如果需要宽度是1500px，则width=1500/144\*2.54=26.46（1 inch = 2.54 cm）。
    -   协同版本的schema各个端需保持一致，即schema里不能有变量。如果需要做各个端适配，可以调用setScale来进行缩放，详情请参见[内容操作接口](#li_aqo_li1_bdh)。 |
    |brush|Partial<Record<IBrushName, IBrushItem\>\>    ```
其中type IBrushName = "pen" | "text" | "shape"
interface IBrushItem {
  strokeWidth?: number; // 线条大小
  stroke?: string; // 线条颜色
  fontFamily?: string; // 字体
  fontSize?: number; // 字号
  strokeDasharray?: string; // 线形
  startArrow?: boolean; // 起始箭头
  endArrow?: boolean; // 末尾剪头
}
    ```

|配置默认画笔属性。示例代码如下所示：    -   配置默认画笔为绿色，线条粗细为 8；默认形状为黄色，线条粗细为2

        ```
{
    pen: { stroke: "green", strokeWidth: 8 },
    shape: { stroke: "yellow", strokeWidth: 2},
}
        ```

    -   配置画笔为虚线，带末端箭头

        ```
{
    pen: { stroke: "green", strokeWidth: 8, strokeDasharray: "4" },
    straight: { stroke: "yellow", strokeWidth: 2, endArrow: true },
}
        ``` |
    |minScale|number|配置缩放的最小值。|
    |maxScale|number|配置缩放的最大值。|
    |defaultToolType|AliyunBoardToolType|配置默认工具项。|
    |fitMode|number|画布初始时的自适应模式，取值：    -   0：无自适应。
    -   1（默认）：宽度自适应。
    -   2：高度自适应 |
    |syncCursor|boolean|是否同步鼠标，取值：    -   true：同步。
    -   false（默认）：不同步。 |
    |eraserSize|number|默认橡皮可擦范围大小，可擦区域为正方形，默认值为20像素。|
    |attachmentHost|string|pdf.html页面的host地址。pdf附件需要在iframe中加载出来，需要和白板域名在同一个域下，否则会报access cross-origin frame的错误。|
    |syncMode|number|协同模式，取值：    -   0：正常模式。
    -   1：课堂模式。
**说明：** 开启课堂模式后会将老师的视口范围同步到学生端，需要设置老师端的forceSync配置项为true。 |
    |forceSync|boolean|指定开启课堂模式后的老师端协同状态（需要和syncMode的课堂模式同时使用），取值：    -   true：协同模式，如果syncMode为课堂模式，需要设置此参数为true。
    -   false（默认）：非协同模式。 |
    |drawableGestureMode|string|指定在大屏上多点触控的模式，取值：    -   igoreSecond（默认）：只响应第一个触控点。
    -   multiple：支持多点触控。 |
    |pinchable|boolean|是否开启移动端上双指手势缩放画布，取值：    -   true（默认）：开启。
    -   false：关闭。 |
    |enableGesture|boolean|是否开启支持大屏手势。该选项一般只在大屏硬件上开启，开启后支持在大屏上用手势对形状进行移动、旋转、缩放的组合操作。取值：    -   true：开启。
    -   false（默认）：关闭。 |
    |replay|boolean|是否开启进入回放模式。开启后白板会进入操作回放模式，需要配合服务端的录制接口同时使用。取值：    -   true：开启。
    -   false（默认）：关闭。 |
    |cornerFixRatio|boolean|选中形状区域的四个角时是否开启等比例缩放。取值：    -   true：开启。
    -   false（默认）：关闭。 |

3.  使用示例说明。

    **说明：** 为保障资源安全，当客户端通过长连接访问互动白板服务时，只有访问域名存在于合法域名列表中，才可以正常访问白板服务。若Web端出现跨域问题（常见于使用localhost或IP:端口号访问页面），请绑定域名或使用本地域名，并进行白板应用合法域名的配置，具体操作，请参见[设置互动白板应用合法域名](/cn.zh-CN/互动白板/创建及配置应用.md)。

    -   JS示例：

        ```
        const { initBoard, AliyunBoard } = window.aliyunBoardSDK;
        
        const getDocumentData = () => {
          return new Promise(resolve => {
            /**
             * 客户服务端通过调用白板服务的打开白板接口获取白板文档的连接信息，客户端通过客户服务端提供的接口获取
             * 白板文档的连接信息，其JSON格式如下所示：
             */
            resolve({
              accessToken: '*******',
              collabHost: '*******',
              permission: 2,
              userInfo: {
                avatarUrl: "http://www.avatarset/Gladys.jpg",
                nick: "Gladys",
                nickPinyin: "Pinyin_Gladys",
                userId: "1234123",
              },
            });
          });
        };
        
        const aliyunBoard = new AliyunBoard({
          getDocumentData,
          docKey: "*******",
          getPreviewUrl: (url, type) => {
            return new Promise(resolve => {
              console.log("file type:", type);
              resolve(url);
            });
          },
        });
        
        const config = { model: aliyunBoard };
        initBoard(config, document.getElementById("root"));
        ```

    -   React示例：

        ```
        import React from "react";
        import ReactDOM from "react-dom";
        
        const { Canvas, AliyunBoard } = window.aliyunBoardSDK;
        
        const getDocumentData = () => {
          return new Promise(resolve => {
            /**
             * 客户服务端通过调用白板服务的打开白板接口获取白板文档的连接信息，客户端通过客户服务端提供的接口获取
             * 白板文档的连接信息，其JSON格式如下所示：
             */
            resolve({
              accessToken: '********',
              collabHost: '********',
              permission: 2,
              userInfo: {
                avatarUrl: "http://www.avatarset/Gladys.jpg",
                nick: "Gladys",
                nickPinyin: "Pinyin_Gladys",
                userId: "1234123",
              },
            });
          });
        };
        
        const aliyunBoard = new AliyunBoard({
          getDocumentData,
          docKey: "*******"
        });
        
        export const BoardDemo = () => {
          return (
            <div>
              <Canvas model={aliyunBoard} style={{height: 900, width: '100%'}}/>
            </div>
          );
        };
        
        ReactDOM.render(<BoardDemo/>, document.getElementById("root"));
        ```


## API

-   内容操作接口

    |API|使用示例|描述|
    |---|----|--|
    |preScene|aliyunBoard.preScene\(\)|向前翻页。|
    |nextScene|aliyunBoard.nextScene\(\)|向后翻页。|
    |getScenesCount|aliyunBoard.getScenesCount\(\)|获取当前的总页数，返回类型为number。|
    |gotoScene|aliyunBoard.gotoScene\(pageNum: number\)|跳转至指定页面。|
    |getCurrentSceneIndex|aliyunBoard.getCurrentSceneIndex\(\)|获取当前页index。|
    |addScene|aliyunBoard.addScene\(\)|增加页面。|
    |removeSceneById|aliyunBoard.removeSceneById\(id: string\)|按ID删除页面。|
    |removeSceneByIndex|aliyunBoard.removeSceneByIndex\(index: number\)|按index删除页面。|
    |setScale|aliyunBoard.setScale\(scale: number\)|缩放画板。|
    |getScale|aliyunBoard.getScale\(\)|获取当前画板缩放值。|
    |undo|aliyunBoard.undo\(\)|撤销上一步操作。|
    |redo|aliyunBoard.redo\(\)|重做上一步操作。|
    |setToolType|aliyunBoard.setToolType\("pointer"\)|指针，支持选中图元，并拖动到指定位置。其中AliyunBoardToolType = "pointer"\|"pen"\|"circle"\|"rect"\|"laser"\|"text"\|"eraser"\|"straight"\|"triangle"\|"bitEraser"\|"roundRect"\|"rightTriangle"，其他绘画类接口请参见[绘画接口](#li_zc9_lc1_tyq)。|
    |setBackgroundColorByIndex|aliyunBoard.setBackgroundColorByIndex\(index: number, color: string\)|按index设置画布某页的背景色。|
    |setBackgroundColorById|aliyunBoard.setBackgroundColorById\(id: string, color: string\)|按ID设置画布某页的背景色。|
    |getCurrentScene|aliyunBoard.getCurrentScene\(\)|返回白板画布页Scene对象。|
    |getScenes|aliyunBoard.getScenes\(\)|返回白板画布Scene对象列表。|
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
    |aliyunBoard.setToolType\("triangle"\)|三角形绘制，绘制三角形样式涂鸦，可设置粗细、颜色。|
    |aliyunBoard.setToolType\("bitEraser"\)|像素橡皮擦。|
    |aliyunBoard.setToolType\("roundRect"\)|圆角矩形绘制，绘制圆角矩形样式涂鸦，可设置粗细、颜色。|
    |aliyunBoard.setToolType\("rightTriangle"\)|直角三角形绘制，绘制直角三角形样式涂鸦，可设置粗细、颜色。|
    |setCurrentBrush|aliyunBoard.setCurrentBrush\(brush: IBrushItem\)|设置当前工具属性，可设置线条颜色、粗细，文字字号、字体。    ```
其中IBrushItem = {
  strokeWidth?: number; // 线条大小
  stroke?: string; // 线条颜色
  fontFamily?: string; // 字体
  fontSize?: number; // 字号
}
    ``` |
    |getCurrentToolType|aliyunBoard.getCurrentToolType\(\)|获取当前工具类型。其中AliyunBoardToolType = "pointer"\|"pen"\|"circle"\|"rect"\|"laser"\|"text"\|"eraser"\|"straight"\|"triangle"\|"bitEraser"\|"roundRect"\|"rightTriangle"。|
    |clearBoard|aliyunBoard.clearBoard\(\)|清空当前页白板。|
    |unSelectAll|aliyunBoard.unSelectAll\(\)|取消形状选中。|
    |setEraserSize|aliyunBoard.setEraserSize\(size: number\)|设置橡皮工具可擦除范围。|
    |updateSelectedTextStyle|aliyunBoard.updateSelectedTextStyle\(textStyle: \{\[key: string\]: any\}\) |设置选中文字的字号、斜体、加粗或下划线，详情如下所示：    -   设置斜体：aliyunBoard.updateSelectedTextStyle\(\{'fontStyle': 'italic'\}\)
    -   设置字号：aliyunBoard.updateSelectedTextStyle\(\{'fontSize': 64\}\)
    -   设置加粗：aliyunBoard.updateSelectedTextStyle\(\{'fontWeight': 'bord'\}\)
    -   设置下划线：aliyunBoard.updateSelectedTextStyle\(\{'textDecoration': 'underline'\}\) |

-   其他接口

    |API|使用示例|描述|
    |---|----|--|
    |addImage|aliyunBoard.addImage\(shape:IShapeModel\)|添加图片。如果x, y 不传，则默认插入画布页中间位置，如果图片预览时涉及权限，则需配合[getPreviewUrl](#entry_q81_hgl_zk3)一起使用。    ```
其中IShapeModel = {
 width: number, // 图片展示的宽
 height: number, // 图片展示的高
 x?: number, // 图片相对于画布的X轴位置
 y?: number, // 图片相对于画布的Y轴位置
 href: string // 图片地址或加签需要的ID
}
    ``` |
    |addBackgroundImage|aliyunBoard.addBackgroundImage\(url: string\)|添加背景图片（背景图不可删除和编辑）。|
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
    |getPreviewData|aliyunBoard.getPreviewData\(index?:number\)|获取序号为index的白板页image对象，如果不传，则返回所有页的image对象列表。返回值：Image\[\] \| Image。**说明：** 仅支持Web端，暂不支持Native端调用。 |
    |setPinchable|aliyunBoard.setPinchable\(true:boolean\)|设置是否开启移动端手势缩放。|
    |getPinchable|aliyunBoard.getPinchable\(true:boolean\)|返回是否开启了移动端手势缩放。|

-   事件监听接口

    |API|使用示例|描述|
    |---|----|--|
    |on|aliyunBoard.on\(eventType, \(...args: any\[\]\) =\> \{ console.log\(args\)\}\)|在aliyunBoard对象上注册事件监听。事件类型请参见[eventType取值](#p_bji_1nn_b77)。|

    事件类型eventType取值如下所示：

    |事件类型|描述|
    |----|--|
    |ALIYUNBOARD\_READY|白板初始化完成事件。|
    |ALIYUNBOARD\_ERROR\_EVENT|白板内部报错事件。|
    |ALIYUNBOARD\_COLLABERROR\_EVENT|协同引擎运行时报错事件。|
    |ALIYUNBOARD\_PINCH\_START|双指缩放开始事件。|
    |ALIYUNBOARD\_PINCH|双指缩放事件。|
    |ALIYUNBOARD\_PINCH\_END|双指缩放结束事件。|
    |ALIYUNBOARD\_EXECUTE|协同消息执行完成后的回调事件。回调参数为：    ```
{
uid: string | number;
nick: string;
commandType: string;
type: string;
sceneId?: string;
shapeId?: string;
x?: number;
y?: number;
width?: number;
height?: number;
ready?: boolean;
action: 'redo' | 'undo';
}
    ``` |
    |ALIYUNBOARD\_PAGINATION\_CHANGE|白板页改变后的回调事件（供应用方修改页码相关的UI），回调参数为：    ```
{
type: 'add' | 'remove' | 'index'; // type表示操作类型，add为添加页面，remove为删除页面，index为改变当前页
index: number; // index表示相应操作的页面索引值
}
    ```

**说明：** 该事件只在接收到远端页码变更后回调，本地修改页码时不会调用。 |


