![IMG_8185.PNG](https://upload-images.jianshu.io/upload_images/12262980-c5255773ce0eaa3c.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

目前测试大部分蓝牙热敏打印机都能使用，打印速度快，能自定义打印速度，主要用了分包发送解决了Ble低功耗问题，本人测试的是一部汉印的N41BT，看懂代码四通一大的快递单都能打印。

最新开发一个小程序 用来做直播虚拟打单，不是用来做非法事情，是用来做直播热度加持的，就是让直播的时候不断有订单进来，打印机可以不断打单。
本来想用其他小程序，结果发现搜了一圈，没有实际订单啥小程序都用不了，只能测试打印，还不能自定义快递单内容，所以程序员出身的我，决定自己开发一个。
![IMG_8192.PNG](https://upload-images.jianshu.io/upload_images/12262980-119f93ce328dfa93.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![IMG_8193.PNG](https://upload-images.jianshu.io/upload_images/12262980-4efb94c91e6e96c4.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![IMG_8195.PNG](https://upload-images.jianshu.io/upload_images/12262980-6df902d94f3472fa.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


自定义呢就是自己加几个输入框，因为没时间就懒得搞了，不过核心代码在这里，自己改改就行
````
printUtil.setCls()//清除缓冲区，防止下一个没生效
      printUtil.setSize(76, 130)//设置标签大小，单位mm.具体参数请用尺子量一下
      printUtil.setGap(0)//设置两个标签之间的间隙，单位mm.具体参数请用尺子量一下
      printUtil.setCls()//清除缓冲区
      printUtil.setText(490, 5, "TSS24.BF2", 0, 2, 2, "快递")//绘制文字
      printUtil.setText(490, 50, "TSS24.BF2", 0, 2, 2, "包裹")//绘制文字
    
      //时间
      let timeTitle = util.formatTime(new Date());
      printUtil.setText(30, 70, "TSS24.BF2", 0, 1, 1,timeTitle)
      //页码
      printUtil.setText(260, 70, "TSS24.BF2", 0, 1, 1, "第1/1页")
      //最外框
      printUtil.setBox(10, 100, 550, 700,2);
      //第一行第一个
      printUtil.setBox(10, 100, 250, 200,2);
      //第一行第二个
      printUtil.setBox(250, 100, 430, 200,2);
      //第一行第三个到底
      printUtil.setBox(430, 100, 550, 700,2);
      //第二行
      printUtil.setBox(10, 200, 430, 300,2);
      //第三行
      printUtil.setBox(10, 300, 430, 370,2);
      //第四行
      printUtil.setBox(10, 370, 430, 490,2);
      //第五行第一个
      printUtil.setBox(10, 490, 230, 700,2);
      //第五行第二个
      printUtil.setBox(230, 490, 430, 700,2);
      //加粗字体
      // printUtil.setFontWidthAndHeight(2, 2);
      printUtil.setText(80, 115, "TSS24.BF2", 0, 4, 4, siteCode)
      //关闭加粗
      // printUtil.setFontWidthAndHeight(1, 1);
      //打印横向条码和文字
      printUtil.setBarCode(50, 205, "128", 58, 0, 0, 2, 2, code)//绘制code128条码
   
      //纵向打印条码和文字
      printUtil.setBarCode(530, 120, "128", 85, 0, 90, 4, 18, code)//绘制code128条码
      // printUtil.printSweepCodeAndTextVertical(450, 680, 85, code);
      // //集散地
      printUtil.setText(30, 310, "TSS24.BF2", 0, 1, 1, "集")
      printUtil.setText(80, 310, "TSS24.BF2", 0, 1, 1, distribution)
  
      // //收件地址
      printUtil.setText( 30, 410, "TSS24.BF2", 0, 2, 2,"收");
      printUtil.setText( 80, 380, "TSS24.BF2", 0, 1, 1,reciptName);
      printUtil.setText(200, 380, "TSS24.BF2", 0, 1, 1,reciptPhone);
      printUtil.setText(80, 410, "TSS24.BF2", 0, 1, 1,reciptAre);
      printUtil.setText(80, 440, "TSS24.BF2", 0, 1, 1,reciptAddress);
      // //寄件地址
      printUtil.setText( 30, 520,"TSS24.BF2", 0, 2, 2, "寄");
      printUtil.setText( 80, 520, "TSS24.BF2", 0, 1, 1,mailName);
      printUtil.setText(50, 580, "TSS24.BF2", 0, 1, 1,mailPhone);
      // //签字栏
      printUtil.setText( 235, 750,"TSS24.BF2", 0, 2, 2, "签字栏");
      // //二维码
      printUtil.setQrcode(235, 497, "L", 9, "A", code)//绘制一个二维码
     
      // //文件名称
      // printUtil.setFontWidthAndHeight(2, 2);
      printUtil.setText( 10, 720, "TSS24.BF2", 0, 1, 1,itemName);
      // printUtil.setFontWidthAndHeight(1, 1);
      // //备注
      printUtil.setText( 10, 780, "TSS24.BF2", 0, 1,1, remark);
      // //已验视
      printUtil.setText(480, 900, "TSS24.BF2", 0, 1, 1, "已验视");
      // //技术支持
      // printUtil.setAlign("center")
      
      printUtil.setText( 0, 950, "TSS24.BF2", 0, 1, 1, "本包裹由通达递提供智慧技术支持");
      printUtil.setPagePrint()//执行打印指令
    
      let buffer = printUtil.getData();
      this.prepareSend(buffer)
````

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
  


