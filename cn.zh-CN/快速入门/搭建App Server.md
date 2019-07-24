# 搭建App Server {#task_1096283 .task}

应用服务器（App Server）是指由用户自行研发的程序层。通过对接阿里云RTC云端服务实现用户应用的业务逻辑，如用户管理、鉴权校验等。本文以开发工具IDEA使用Java语言为例，为您介绍搭建App Server的具体操作步骤。

在进行操作前，您需要：

-   获取应用ID，具体操作请参见[创建应用](cn.zh-CN/快速入门/创建应用.md#)。
-   获取AccessKeyId和AccessKeySecret，具体操作请参见[获取AccessKey](../../../../cn.zh-CN/API参考/获取AccessKey.md#)。

**警告：** 主账号Accesskey泄露会威胁您所有资源的安全。建议使用子账号（RAM用户）Accesskey进行操作，可有效降低Accesskey泄露的风险。

1.  根据您的需求下载对应版本的App Server源码，阿里云音视频通信为您提供以下版本。 
    -   [Golang](https://github.com/aliyunvideo/AliRtcAppServer/tree/master/golang#appserver)
    -   [Java](https://github.com/aliyunvideo/AliRtcAppServer/tree/master/java#appserver)
    -   [Python](https://github.com/aliyunvideo/AliRtcAppServer/tree/master/python#appserver)
    -   [C\#](https://github.com/aliyunvideo/AliRtcAppServer/tree/master/csharp#appserver)
    -   [Nodejs](https://github.com/aliyunvideo/AliRtcAppServer/tree/master/nodejs#appserver)
    -   [PHP](https://github.com/aliyunvideo/AliRtcAppServer/tree/master/php#appserver)
2.  创建新工程（Project），将下载的源码复制在工程文件里。
3.  在pom.xml文件中添加Maven依赖。 

    ``` {#codeblock_ybd_a9b_pwl}
    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>jetbrains</groupId>
        <artifactId>maven-rtc</artifactId>
        <version>1.0-SNAPSHOT</version>
        <dependencies>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-rtc</artifactId>
                <version>0.8.0</version>
            </dependency>
            <dependency>
                <groupId>com.sun.net.httpserver</groupId>
                <artifactId>http</artifactId>
                <version>20070405</version>
                <scope>test</scope>
            </dependency>
            <dependency>
                <groupId>commons-cli</groupId>
                <artifactId>commons-cli</artifactId>
                <version>1.2</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-core</artifactId>
                <optional>true</optional>
                <version>3.7.1</version>
            </dependency>
        </dependencies>
    </project>
    ```

4.  单击**Edit Configurations**，在**Vm Options**填入启动参数。 

    ``` {#codeblock_aog_chp_rl4 .language-java}
    --listen=8080
    --appid=xxxxxxxx
    --appkey=xxxxxxxxx
    --gslb=https://rgslb.rtc.aliyuncs.com
    ```

5.  单击**运行**。
6.  验证App Server，请单击[AppServer Verification](http://127.0.0.1:8080/app/v1/login?room=1237&user=jzufp&passwd=12345678)。 

    **说明：** 请将App Server`http://127.0.0.1:8080/app/v1/login`替换成`您的AppServer地址:端口/app/v1/login`。

    -   App Server启动成功。

        ![AppServer成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170801/156394887951338_zh-CN.png)

    -   App Server未启动，访问失败。

        ![AppServer失败](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170801/156394888051340_zh-CN.png)

        **说明：** 音视频通信Password并没有提供校验机制，您可以随意填写，建议默认即可。

7.  校验Token，请单击[Token Verification](http://ossrs.net/talks/ng_index.html?spm=a2c4g.11186623.2.22.22965188TERfAg#/token-check?schema=http&host=127.0.0.1&port=8080&path=%2Fapp%2Fv1%2Flogin&room=1237&user=jzufp&password=12345678)。 
    -   校验Token成功。

        ![Token成功](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170801/156394888051342_zh-CN.png)

    -   校验Token失败。

        ![Token失败](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/170801/156394888051344_zh-CN.png)


AliRtcSDK为您提供完整的频道鉴权开发流程，详情请参见[生成频道鉴权令牌](cn.zh-CN/快速入门/生成频道鉴权令牌.md#)。

