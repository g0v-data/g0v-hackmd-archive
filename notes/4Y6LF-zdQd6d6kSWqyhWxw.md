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
列出鏡頭可控制參數 -> v4l2-ctl -d /dev/video0 --list-ctrls
取得/dev/video* name -> cat /sys/class/video4linux/video*
取得 v4l2 debug message -> echo 1 >/sys/class/video4linux/video0/debug
印出訊息 -> echo 0xffff > /sys/module/uvcvideo/parameters/trace
v4l2-ctl -d /dev/v4l-subdev2 <command line>
待整理：



https://emb.hqyj.com/Column/Column409.htm
https://dri.freedesktop.org/docs/drm/userspace-api/media/v4l/func-mmap.html
-----dpkg-----
https://doc.embedfire.com/linux/rk356x/build_and_deploy/zh/latest/building_image/make_pakage_of_deb/make_pakage_of_deb.html
https://blog.csdn.net/weixin_43824344/article/details/120694693

# *`資料來源`*
```
v4l2 指令相關
```
https://blog.csdn.net/wangyijieonline/article/details/104966501
https://blog.csdn.net/TyearLin/article/details/131726154
https://zhaoxuhui.top/blog/2021/09/23/v4l2-introduction-and-usb-camera-bayer-raw-data.html
https://developer.aliyun.com/article/1489668
https://hackmd.io/@YungHuiHsu/ryhRTZpt3
https://wiki.luckfox.com/zh/Luckfox-Pico/Luckfox-Pico-V4L2/
v4l2-ctl-subdev源碼:
https://github.com/kuscsik/v4l-utils/blob/master/utils/v4l2-ctl/v4l2-ctl-subdev.cpp
https://elixir.bootlin.com/linux/v3.2/source/drivers/media/video/v4l2-subdev.c#L275
kernel API:
https://www.kernel.org/doc/html/v4.9/media/uapi/v4l/vidioc-subdev-g-frame-interval.html#c.v4l2_subdev_frame_interval
https://linuxtv.org/downloads/v4l-dvb-apis/


```
v4l2 底層流程
```
https://blog.csdn.net/oqqYuJi12345678/article/details/93755475
https://www.cnblogs.com/jliuxin/p/14129308.html
https://www.cnblogs.com/arnoldlu/p/18111445
https://blog.csdn.net/huang_165/article/details/86217004
架構大全-> https://blog.csdn.net/ldl617/article/details/115063305
https://wiki.st.com/stm32mpu/index.php?title=STM32MP13_V4L2_camera_overview&oldid=89014