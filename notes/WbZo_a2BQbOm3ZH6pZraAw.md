---
title: "g0v Summit 直播組 SOP"
tags: g0v-summit,hackpad
---

# g0v Summit 直播組 SOP

> [點此觀看原始內容](https://g0v.hackpad.tw/Ii29Gy0NxGU)


上層 hackfoldr: [http://beta.hackfoldr.org/g0v-summit-sop](http://beta.hackfoldr.org/g0v-summit-sop)

## 前置

### 規劃架構

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_04b4095c09d67020c02adf1d7b668c68)

### 募集工人

- R0 /> 導播 - 沖天, 攝影師 - macpaul
- R1 /> 導播 - Steven Liu, 攝影師 - 小鳥
- R2 /> 導播 - 恩瀚, 攝影師 - Henry ~黑田~
- 後勤 /\> Stella, Mifu

### 實際演練

- 架構試架一次
- 全員到齊在線路組演練一次

### 租設備

- 此次 九晴天攝影器材出租 統編免押金, 約9k
- 購買一顆1TB隨身硬碟存後製影片, 約1.5k

## 現場

- 提前一天下午至現場R0, R1, R2架設設備
    - 投影機 R0使用VGA 1024\*768, R1使用VGA 1024\*768, R2使用HDMI
    - 投影片筆電 R0使用VGA, R1使用VGA, R2使用HDMI
    - 攝影機位置不要離講者太遠, 避免有人在前方走動 （通常在左前）
    - 將 導播機 與 攝影機 收回中研院旅館放置
- Day1
    - 8點到會場, 一個會場領一個攝影包, 設備都整理好在裡面
    - 攝影師在換講者時要重新錄影, 讓影片檔是分段的
    - 後勤人員需監看直播頻道的畫面
- Day2
    - R0一早就架設, R1 R2 只有下午有講者, 因此 10am才開始架設
    - 攝影師在換講者時要重新錄影, 讓影片檔是分段的
    - 後勤人員需監看直播頻道的畫面
    - 收設備歸還租借的設備（使用廂型車）

## 後製

- 剪輯 攝影機 畫面並上傳
- 剪輯 導播機 畫面並上傳
- 將連結更新至 [http://summit.g0v.tw/2016/schedules](http://summit.g0v.tw/2016/schedules)
> ffmpeg -i xxx.mov -threads 2 -vcodec h264 -af "pan=1c|FC=FL,volume=5" xxx\ \[live\].mp4
> [name=劉宇庭]

- 剪輯影片封面 講者、議程名字
- 剪輯影片 片頭、片尾

## 附錄

剪輯 影片檔案太大無法分工, 只能單一人輪流作業
場佈時除架設備, 留時間測試直播訊號, 確認直播正常

[http://proav.roland.com/categories/video_mixers/](http://proav.roland.com/categories/video_mixers/)
R0導播機 [http://proav.roland.com/promos/v-1200hd/](http://proav.roland.com/promos/v-1200hd/)
ˇ360直播 [http://teradek.com/pages/sphere](http://teradek.com/pages/sphere)

