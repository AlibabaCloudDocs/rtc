# Android SDK动态加载so文件方案

Android SDK提供so文件动态加载的功能，可以有效的减少安装包文件的大小。通过阅读本文，您可以了解在集成SDK时如何进行so文件的动态加载。

传统安装包文件包含so文件，因此安装包文件通常会比较大，用户在下载使用时不太方便。使用so文件动态加载方案，即so文件不打包到apk里，在安装完并打开应用的时候通过后台下载so文件，将下载的so文件加载到应用中。阿里云RTC Android SDK提供动态加载方案所需的SDK分离包，将so文件和aar文件分离，开发者可以将aar文件打包进apk里，将较大的so文件放到云端进行下载，可以极大的减少安装包体积，方便用户下载使用。

## 集成SDK

方法一：Maven集成

1.  在根目录的build.gradle中添加Maven仓库地址：

    ```
    allprojects {
        repositories {
            google()
            jcenter()
            //添加RTC需要的Maven地址
            maven {
                url "http://maven.aliyun.com/nexus/content/groups/public/"
            }
        }
    }
    ```

2.  在项目的/app/build.gradle文件中，添加如下行：

    ```
    dependencies {   
            ...   
        //依赖的RTC SDK  
        implementation 'com.aliyun.rtc:AliRTC:1.17.41.2102238'
    }
    ```

    **说明：** 此处Maven依赖的版本仅供参考，获取最新的Maven依赖，请参见[精简版SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

3.  下载并解压so文件，下载地址，请参见[精简版SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

4.  在代码中添加如下代码，加载so文件。

    ```
    System.load("so文件绝对路径");
    ```

    **说明：**

    -   下载后的文件解压后包含aar和so文件，请根据实际情况选择其中某一个so文件即可。
    -   此处不能使用`System.loadLibrary()`方式加载so文件，是因为`System.loadLibrary()`的参数为so文件名（不包含文件的扩展名），而且必须是在JVM属性`java.library.path`所指向的路径中，其他的路径不能识别，同时由于受到权限限制，下载的so文件没有办法保存在JVM属性`java.library.path`所指向的路径中，因此不能使用此方法；于此相反，使用System.load\(\)时，System.load\(\)的参数可以是任意路径，只要路径为so文件的绝对路径即可，因此进行so文件加载时，只能使用此方法。
5.  在/app/src/main/AndroidManifest.xml文件中添加如下代码，获取相应的设备权限。


方法二：手动集成

1.  下载并解压Android SDK，下载地址，请参见[精简版SDK](/cn.zh-CN/SDK参考/SDK下载.md)。

2.  复制SDK文件AliRTCSdk.aar到App模块下的libs文件夹中。

3.  在代码中添加如下代码，加载so文件。

    ```
    System.load("so文件绝对路径");
    ```

    **说明：**

    -   下载后的文件解压后包含aar和so文件，请根据实际情况选择其中某一个so文件即可。
    -   此处不能使用`System.loadLibrary()`方式加载so文件，是因为`System.loadLibrary()`的参数为so文件名（不包含文件的扩展名），而且必须是在JVM属性`java.library.path`所指向的路径中，其他的路径不能识别，同时由于受到权限限制，下载的so文件没有办法保存在JVM属性`java.library.path`所指向的路径中，因此不能使用此方法；于此相反，使用System.load\(\)时，System.load\(\)的参数可以是任意路径，只要路径为so文件的绝对路径即可，因此进行so文件加载时，只能使用此方法。
4.  在/app/src/main/AndroidManifest.xml文件中添加如下代码，获取相应的设备权限。


## 后续操作

-   由于动态加载方案不能确保每次都会成功，如果so文件加载成功，可直接进入App；如果so文件没有加载成功，App会崩溃，建议执行降级操作或者重新加载so文件，成功之后才允许进入App。
-   建议在App空闲时下载so文件，不要在应用进入之后再去下载so文件，提升使用体验。

