---
title: '題目：LUNAR SURFACE OPERATIONS: REAL-TIME COLLABORATION 月球表面行動：即時合作 '
---
:::success
[回 2021 NASA 黑客松挑戰中文翻譯 Challenge](https://g0v.hackmd.io/4DIbh5k4R-SNBq3FdGMIjQ?both)
:::

題目：LUNAR SURFACE OPERATIONS: REAL-TIME COLLABORATION 月球表面行動：即時合作 
===
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9af41117538aa9664ea43ab38713b2d.jpeg)
[官網原文](https://2021.spaceappschallenge.org/challenges/statements/lunar-surface-operations-real-time-collaboration/details)

# Full Details 完整說明

> As astronauts collect data on the Moon, NASA and the worldwide scientific community will be documenting and reviewing the information in real time. Your challenge is to create an application to allow NASA flight controllers and the broader scientific community to collaborate and compare notes on lunar mission data as it is collected.

隨著太空人在月球上搜集資料，美國國家航空暨太空總署(NASA)和全球科學界將及時地紀錄並審查這些資訊。你的挑戰是要創建一款應用程式，讓NASA的飛行控制員和廣大的科學界在搜集月球數據的任務上，能夠互相合作和比較。

## Details 詳細描述
### Background 背景說明
> During the Artemis lunar missions a very broad community will be following the lunar surface EVAs (Extravehicular Activities) or spacewalks. Throughout these EVAs crewmembers will be taking photographs, audibly describing what they see, and collecting samples to help answer some of the biggest mysteries regarding the Moon, Earth, and our solar system.
> 
> Many people on Earth will be involved in documenting and reviewing this information in real time in addition to the post-mission operations debriefs and scientific research. In the current record-keeping approach implemented for human spaceflight, each flight control team member creates and maintains a console log to record the information necessary to support his/her job duties. This console log becomes part of the official record of the mission. (See video for an example excerpt of a console log written from the perspective of EVA TASK when a crew performed a PGT operation.) Using this present-day system, each flight control team member creates a console log in isolation. In other words, there is no way for a flight controller to simultaneously see the live creation of logs by others or to synchronize multiple people's logs to compare notes with different authors during or after a mission.

在阿提米絲Artemi月球任務期間，一個非常廣大的團體將密切關注月球表面的艙外活動(EVA)或太空漫步。在這些艙外活動中，機組人員將拍攝照片，用聲音描述他們所看到的內容，並收集樣本以解答一些有關月球、地球和太陽系的最大謎團。

除了任務後的操作匯報和科學研究之外，地球上的許多人將參與即時記錄和審查這些訊息。在當前太空飛行所實施的記錄保存方法中，每個飛行控制團隊成員都會創建並維護一個控制台日誌，以記錄支持其工作職責所需的訊息。該控制台日誌成為任務正式記錄的一部分。（請參閱影片，以了解當機組人員執行 PGT 操作時從 EVA TASK 的角度編寫的控制台日誌範例摘錄。）使用當今的系統，每個飛行控制團隊成員都可以單獨創建控制台日誌。換句話說，飛行控制員無法同時查看其他人即時創建的日誌，也無法同步多人的日誌，以便在任務期間或任務後與不同作者進行比較。

### Objectives 目標
> The goal of this challenge is to create an application that can immediately and seamlessly integrate console log information of many users (at least 100+ users on the same network). Such an application could be valuable to real-time mission support and long-term record keeping of future lunar human spaceflight missions for the benefit of scientific communities and the public.
> 
> The demonstration of this capability does not require actual mission data; multi-person logging events on any subject can be used to demonstrate your application.

此挑戰的目標是創建一個應用程式，該應用程式可以立即且連續地整合許多用戶（同一網路上至少 100 多位用戶）的控制台日誌訊息。 這樣的應用程式對於為科學界和公眾利益，在未來月球太空飛行任務的即時任務支持和長期記錄保存，可能是有價值的。

這種能力的展現不需要實際的任務數據； 關於任何主題的多人日誌事件都可用來示範你的應用程式。

### Potential Considerations 潛在考量
> Your application should allow:
> -	Multiple simultaneous users creating their own console logs
> -	Real-time live editing of logs that are viewable to anyone on the same network
> -	Users to select which logs to view (on demand)
> -	A user to see his/her own console intermixed with the logs from others selected, which could be arranged by time, 'entry topic,' author, or other attributes.
> -	Console log metadata that includes (at a minimum) a timestamp for every entry and a text entry (an entry could also include images)
> -	The ability to input sample type, written information including descriptions, time tags, hardware used, along with upload of supporting files (photo, video, and audio)
> -	The capability to add future input fields including user name, 'console seat/position,’ or other attributes
> -	Users to tag/link log entries from other authors to their own logs
> -	Each user to 'officially approve' his/her log once the user is ready. This action will create a permanent unmodifiable log that becomes the official written record for that user's profile.
> 

> Your application should prohibit:
> -	Users from overwriting or deleting other user’s inputs
> -	Application access from unapproved people
> -	Potential keywords you can search online: Apollo in real time

你的應用程式應該能夠:
* 讓多位用戶同時創建自己的控制台日誌
* 實況直播編輯日誌，使同一網路上的任何人都可以查看
* 允許用戶選擇要查看的日誌(在有需求時)
* 使用戶可以看到他/她自己的控制台與其他人選擇的日誌混合在一起，這些日誌可以按時間、“條目主題”、作者或其他屬性排列
* 控制台日誌裡的詮釋資料，包括（至少）每個條目的時間戳記和文本條目（條目還可以包括圖像）
* 能夠輸入樣本類型、書面訊息，包括事件描述、時間標籤、使用的硬體以及輔助文件（照片、影片和音頻）的上傳
* 添加未來輸入字段的功能，包括用戶名、“控制台座位/位置”或其他屬性
* 用戶將其他作者的日誌條目標記/連結到他們自己的日誌
* 一旦用戶準備好，每個用戶都可以“正式批准”他/她的日誌。 此操作將創建一個永久不可修改的日誌，將成為該用戶個人資料的正式書面記錄

你的應用程式應該禁止:
* 用戶覆蓋或刪除其他用戶輸入的內容
* 未經批准的人進入應用程式
* 可以在線上搜尋的潛在關鍵詞：阿波羅即時資訊


# Resources 相關資源
> <https://2021.spaceappschallenge.org/challenges/statements/artfully-illuminated-asteroids/resources>

