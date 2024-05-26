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
1. 測試 -> v4l2-compliance -d /dev/video0 -f
2. 顯示所有subdevice -> v4l2-ctl --list-devices
3. 








# *`資料來源`*
https://hackmd.io/@sysprog/rJEhcgoSn
