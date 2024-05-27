# V4L2 底層筆記
```
架構圖
```

>流程:
1. Opening the device
1. Changing device properties, selecting a video and audio input, video standard, picture brightness a. o.
1. Negotiating a data format
1. Negotiating an input/output method
1. The actual input/output loop
1. Closing the device

> 參數:
1. 
>指令:
v4l2-ctl: 設定
v4l2-format: 
v4l2-capture: 

測試 -> v4l2-compliance -d /dev/video0 -f
顯示所有subdevice -> v4l2-ctl --list-devices
顯示詳細訊息 -> v4l2-ctl -d /dev/video0 --all
查詢指定格式下支援分辨率 -> v4l2-ctl --list-framesizes=NV12 -d /dev/video0
查詢鏡頭可用的分辨率 -> v4l2-ctl --list-formats-ext --device /dev/video0
顯示鏡頭參數 -> v4l2-ctl -d /dev/video0 --list-ctrls
取得/dev/video* name -> cat /sys/class/video4linux/video*








# *`資料來源`*
```
v4l2 指令相關
```
https://blog.csdn.net/wangyijieonline/article/details/104966501
https://blog.csdn.net/TyearLin/article/details/131726154
https://zhaoxuhui.top/blog/2021/09/23/v4l2-introduction-and-usb-camera-bayer-raw-data.html
https://developer.aliyun.com/article/1489668
https://hackmd.io/@YungHuiHsu/ryhRTZpt3
```
v4l2 底層流程
```
https://blog.csdn.net/oqqYuJi12345678/article/details/93755475
https://www.cnblogs.com/jliuxin/p/14129308.html
https://blog.csdn.net/huang_165/article/details/86217004