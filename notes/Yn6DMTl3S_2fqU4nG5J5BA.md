---
title: 議程：數位韌性實驗室_Off-the-grid network 技術交流
tags: 議程組, summit2026, program, programming, summit, 議程
---
# 圓桌討論_數位韌性實驗室：Off-the-grid network 技術交流

> 歡迎爆改，比路上飆車族還爆改的那種爆改 [name=paulpengtw]

## 上到官網的議程介紹
 
這場圓桌只談實作。我們將邀請在戰區和叢林裡實際運作去中心化通訊系統的人，以及處理服務和雲端架構的台灣開發者，一同交流拆解技術。dComms 團隊將細說他們在烏克蘭的技術決策，包含聯邦式協定的選擇、本地伺服器的分散部署、以及 P2P 內容遞送在基礎設施遭攻擊時的實際狀況與瓶頸。Michael Suantak 帶來的是另一種極端條件下的工程問題：在沒有穩定電力與專業維運人力的偏鄉，如何讓 mesh 網路和本地伺服器被社區自主維護並持續運作。藉由實作的技術交流，歡迎台灣開發者們套回在地情境，一起討論怎麼蓋替代網絡，怎麼系統化？

## 時間/日期/地點
> 這個有點難改 [name=paulpengtw]
- May 24th Sun.
- 1530 - 1630 (+8)
- 中研院人文館 4F RH 交誼廳
- 因為是圓桌討論，所以隨時會有與會者冒出來

## 與會者/主持人

### 政策桌
- MG Lee
- Lulu Keng
### 技術桌（英文進行）
- Aidan (from [equalitie.org's dComm project](https://dcomm.net.ua/en/))
- Michael Suantak ([Myanmar's off-grid mesh network](https://metagov.org/media/pages/projects/groundwork-fellowship/documentation/c5751620c5-1713959979/building-a-decentralized-secure-and-private-communication-system-for-myanmar-michael-suantak-1.pdf))
- 戴辰宇 ([gd of HITCON](https://hacker.org.tw/about/supervisor/))
- 尤理衡 ([開源網路維運](https://seadog007.me/) )
- poga ([maintainer of g0v.social](https://g0v.social/@poga))
- 彭　宬 ([g0v DigiResiThon](https://s.g0v.tw/resi))

## 技術桌實際上想要圓桌與會者們聊什麼
- this roundtable is for those write the code and run the servers. So what we wish paticipants to bring is more about the engineering details: the technical decisions behind running decentralized communication stacks on distributed local hosting under sustained infrastructure stress, the tradeoffs between protocol choices (Matrix vs. Briar vs. Delta Chat) given different failure modes, and the real gaps everyone identified that remain unsolved. 
- some of the projects that prticipants built and operated live wartime conditions, including deploy federated services on local servers across Ukrainian cities, keeping Matrix and Mastodon instances reachable even when upstream connectivity was severed; plus what worked and what didn't when deploying mesh in difficult terrain, how you designed for community maintainability rather than requiring a permanent technical team on site, and what the realistic coverage and reliability limits of these architectures are when you're building them with constrained resources. 
- our paticipants is not looking for abstract policy frameworks: they want to talk about how exactly does architect local-first federation, what broke in production when infrastructure was under attack, and how tools like Ceno's P2P content distribution and Ouisync's serverless file sync actually performed when centralized alternatives went dark.


