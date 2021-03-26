# Web

通过阅读本文，您可以了解到Web端互动模式的接入流程。

1.  实例化对象。

    ```
    var aliWebrtc = new AliRtcEngine();
    ```

2.  设置onUpdateRole（角色切换）监听。

    **说明：** 在互动模式下，当调用setClientRole接口返回true，并且收到onUpdateRole回调获取到正确新值时才表示切换成功。

    ```
    aliWebrtc.on("onUpdateRole",(data) => {
        console.log(data);
    })
    ```

3.  设置用户角色。

    该方法在加入频道前后都可以调用，调用前您必须先停止推流。

    ```
    /**
     * @param  role 角色，0：互动角色；1：观众角色
     * @return 调用成功返回true，失败返回false
     */
    aliWebrtc.setClientRole(role);
    ```

4.  设置频道类型。

    **说明：** 接入互动模式，需要将channelProfile设置为1。

    ```
    /**
     * @param  channelProfile 频道类型，0：通信模式；1：互动模式；2：低延迟互动直播模式
     * @return 调用成功返回true，失败返回false
     */
    aliWebrtc.setChannelProfile(channelProfile)
    ```

5.  检测浏览器是否支持RTC SDK。

    ```
    aliWebrtc.isSupport().then(re => {
        console.log(re);
    }).catch(err => {
      console.log(err)
    })
    ```

    更多信息，请参见[isSupport](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)。

6.  加入频道。

    成功加入频道后，互动角色可以进行推流，观众角色不能进行推流。

    ```
    /**
     * @param authInfo 鉴权信息
     * @param displayName 显示名称
     */
    aliWebrtc.joinChannel(authInfo,displayName).then(()=>{
        //加入频道成功
    }).catch((err)=>{
      if(err.errCode === 33622275){
        //加入频道失败，频道类型错误
      }else{
        //加入频道失败，其他错误
      }
    })
    ```

    **说明：** authInfo为服务端下发的鉴权信息，生成Token操作及authInfo参数，请参见[服务端生成Token方式](/cn.zh-CN/常用功能/生成Token.md)。

    更多接口详情，请参见[AliRtcEngine接口](/cn.zh-CN/SDK参考/Web SDK/AliRtcEngine接口.md)。


