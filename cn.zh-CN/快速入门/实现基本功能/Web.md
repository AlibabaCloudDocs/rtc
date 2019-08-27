# Web {#task_1180891 .task}

阿里云音视频通信的基本功能包含创建实例、加入频道、本地发布和订阅远端、离开频道等。当您成功创建实例，您可以进行本地预览视频功能，进行简单的预览和测试。

您需要集成WebSDK，详情请参见[集成WebSDK](cn.zh-CN/快速入门/集成客户端SDK/Web.md#)。

1.  创建AliRtcEngine。 

    ``` {#codeblock_2b8_1ou_4ge .language-javascript}
    var aliWebrtc = new AliRtcEngine();    // 不支持多实例   
    ```

    1.  本地预览。在创建完AliRtcEngine实例后，您可以通过video标签播放。 

        ``` {#codeblock_df0_slj_a2x .language-java}
        aliwebrtc.startPreview(
            video    // html中的video元素
        ).then(()=>{
        }).catch((error) => {
            // 预览失败
        });
        ```

2.  加入频道。 

    ``` {#codeblock_li5_4yx_lo2 .language-java}
    aliwebrtc.joinChannel({
        userid,         // 用户id，只能由数字、字母、下划线组成
        channel,        // 频道
        appid,          // 应用id
        nonce,          // nonce
        timestamp,      // 时间戳
        gslb,           // gslb
    },displayName).then((obj)=>{
        // 入会成功
    } ,(error)=>{
        // 入会失败，这里console下error内容，可以看到失败原因
        console.log(error.message);
    });              
    ```

    **说明：** joinChannel需要传递两个参数。第一个是频道鉴权令牌信息，需要您搭建App Server调用音视频通信的API去获取；第二个参数是频道里显示的用户名。

3.  发布或取消发布本地流。 
    -   发布本地流。如果需要让远程订阅本地的流，需要调用publish接口，发布本地流，远程会接收到onPublisher事件。

        ``` {#codeblock_3n6_slo_lkd}
        aliwebrtc.publish().then(()=>{
        } ,(error)=>{
            console.log(error.message);
        });
        ```

    -   取消发布本地流。当您取消发布本地流时，远程会收到onUnPublisher事件。

        ``` {#codeblock_hcr_kn1_7zb}
        aliwebrtc.unPublish().then(()=>{
        } ,(error)=>{
            console.log(error.message);
        });
        ```

4.  订阅onPublisher事件或onUnPublisher事件。 

    -   订阅onPublisher事件。当远程人员推流时，在SDK里会触发onPublisher事件， 通过订阅这个事件，能够得到频道里已经推流的人员。

        ``` {#codeblock_6fx_b35_q7n}
        aliwebrtc.on('onPublisher',(publisher) =>{
            //远程发布者userId
            console.log(publisher.userId);
            //远程发布名字
            console.log(publisher.displayName);
            //远程流内容，streamConfigs是数组。
            console.log(publisher.streamConfigs);
          });
        ```

    -   订阅onUnPublisher事件。当远程用户结束推流时，会触发这个事件。

        ``` {#codeblock_ryd_rsj_r5c}
        aliwebrtc.on('onUnPublisher',(publisher) =>{
            //远程发布者userId
            console.log(publisher.userId);
            //远程发布名字
            console.log(publisher.displayName);
        });
        ```

    **说明：** onPublisher、onUnPublisher事件只有加入频道以后才会触发。

5.  订阅或取消订阅远程流。 
    -   订阅远程流。userId是用户Id。

        ``` {#codeblock_0sp_lmq_3v3}
        aliwebrtc.subscribe(userId).then((userId)=>{
        },(error)=>{
            console.log(error.message);
        });
        ```

        成功订阅远程流以后。 订阅成功到和远程人员建立链接是一个异步的过程，需要订阅onMediaStream事件，得到远程流的stream对象，通过video元素播放。

        ``` {#codeblock_bgb_vbg_vw0}
        aliwebrtc.on('onMediaStream',(subscriber, stream)=>{
            var video = document.getElementByTag('video');
            aliwebrtc.setDisplayRemoteVideo(
                subscriber,        // onMediaStream中返回的参数
                video,             // html中用于显示stream对象的video元素
                stream             // onMediaStream中返回的参数
            )
        });
        ```

    -   显示远程流。在onMediaStream消息中，调用setDisplayRemoteVideo来显示远程流。

        ``` {#codeblock_f91_flo_1ot}
        aliwebrtc.setDisplayRemoteVideo(
            subscriber,        // onMediaStream中返回的参数
            video,               // html中用于显示stream对象的video元素
            stream             // onMediaStream中返回的参数
        )
        ```

    -   取消订阅。通过unSubscribe可以取消订阅远程流。userId是用户Id。

        ``` {#codeblock_b0w_jqp_imp}
        aliwebrtc.unSubscribe(userId).then(() => {
        },(error)=>{
            console.log(error.message);
        });
        ```

6.  离开频道。 

    ``` {#codeblock_wlo_l0x_xhg}
    aliwebrtc.leaveChannel().then(()=>{
    } ,(error)=>{
        console.log(error.message);
    });
    ```


获取示例代码，您可以通过单击[音视频通信WEB SDK使用申请](https://page.aliyun.com/form/act878195301/index.htm)。

