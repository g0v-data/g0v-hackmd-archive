---
tags: infras, 基礎建設, jothon-online
---
# jitsi-screen 分割畫面小幫手

:::info
* [g0v github repo](https://github.com/g0v/jitsi-screen)
* [ronny的總統盃版本](https://github.com/ronnywang/jitsi-screen)
* [github pages(screen2控制台)](https://g0v.github.io/jitsi-screen/screen2.html)
:::
## todo
- [x] merge to g0v repo
- [x] 重新命名screen2平台名稱 => 揪己家 Jo Jitsi Plus
- [ ] 場景相關
    - [x] 可以將場景存到 LocalStorage
    - [x] 可以手動新增、刪除場景
    - [x] 可以將現有場景匯出成單一 JSON 檔
    - [x] 可以從單一 JSON 檔匯入場景
    - [ ] 可以輸入網址，並從支援 CORS 的遠端 JSON 載入場景設定
    - [ ] HTML 編輯器
- [ ] 成員相關
    - [ ] 可以編輯成員並存到 LocalStroage
    - [ ] 可以切成限定成員模式（每個成員有自己的獨立網址，確保只有成員可以參加）或自由加入模式（參與者可自行輸入名字）
    - [ ] 成員可以分組功能？
    - [ ] 整合成員狀態功能（是否在線上，場景是否有同步）
    - [ ] 有雙視窗版本和單視窗版本（雙視窗可以給雙螢幕用，一個是控制台，另一個是顯示畫面。單視窗只用在顯示畫面）
    - [ ] 如果攝影機畫面沒被人看或是只需要被看 360p 就降低畫質傳送
- [ ] 新client端