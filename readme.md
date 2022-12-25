![IMG_8185.PNG](https://upload-images.jianshu.io/upload_images/12262980-c5255773ce0eaa3c.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

目前测试大部分蓝牙热敏打印机都能使用，打印速度快，能自定义打印速度，主要用了分包发送解决了Ble低功耗问题，本人测试的是一部汉印的N41BT，看懂代码四通一大的快递单都能打印。

最新开发一个小程序 用来做直播虚拟打单，不是用来做非法事情，是用来做直播热度加持的，就是让直播的时候不断有订单进来，打印机可以不断打单。
本来想用其他小程序，结果发现搜了一圈，没有实际订单啥小程序都用不了，只能测试打印，还不能自定义快递单内容，所以程序员出身的我，决定自己开发一个。
![IMG_8192.PNG](https://upload-images.jianshu.io/upload_images/12262980-119f93ce328dfa93.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![IMG_8193.PNG](https://upload-images.jianshu.io/upload_images/12262980-4efb94c91e6e96c4.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![IMG_8195.PNG](https://upload-images.jianshu.io/upload_images/12262980-6df902d94f3472fa.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


自定义呢就是自己加几个输入框，因为没时间就懒得搞了，不过核心代码在这里，自己改改就行


上面是绘制快递单核心代码

连接蓝牙发现蓝牙代码如下
````
wx.createBLEConnection({
      deviceId: e.currentTarget.dataset.title,
      success: function (res) {
        console.log(res)
        app.BLEInformation.deviceId = e.currentTarget.dataset.title
        that.getSeviceId()
      }, fail: function (e) {
        wx.showModal({
          title: '提示',
          content: '连接失败',
          showCancel: false
        })
        console.log(e)
        wx.hideLoading()
      }, complete: function (e) {
        console.log(e)
      }
    })

````
  连接代码大同小异就不贴了
  


