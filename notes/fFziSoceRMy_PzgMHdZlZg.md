---
title: "[foda.io] hackfoldr 哪裡好用？哪裡不好用？還想要有什麼功能？"
tags: hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/bNkNzMRWse6)

hackfoldr redesign  需求訪談，歡迎社群成員、gov成員、公司行號各種組織、個人user許願

## Hackfoldr → foda.io

g0v grants提案上線囉！
[https://grants.g0v.tw/projects/587997fc55fa75001ef55eea](https://grants.g0v.tw/projects/587997fc55fa75001ef55eea)

## 以下許願池

- ethercalc  常常連不上
- option/tag 只能用純文字設定，也許可以設計更好的介面
> 考慮快速選擇常用option、下拉選單、所見即所得編輯等等
> [name=chihao y]

- 希望可以使用 HackMD 作為來源 [hackfoldr/hackfoldr 2.0#57](https://github.com/hackfoldr/hackfoldr-2.0/issues/57)
- 手機版要使用實機測試，有聽說介面會卡卡的
> iOS/Android app又是另一回事了 XD
> [name=chihao y]

> iOS superbil 有更新計畫 [https://itunes.apple.com/tw/app/hackfoldr/id919010837?l=zh&mt=8](https://itunes.apple.com/tw/app/hackfoldr/id919010837?l=zh&mt=8)
> [name=ipa c]

- 程式碼可以稍微重構一下
- 可以參考看看 gitbook 的介面 (？)
- 連結順序可以直接拉動調整，不需要進 ethercalc 改
> [ipa chiu](https://g0v.hackpad.tw/ep/profile/od9zls3wnWG): 會覺得需要巢狀folder嗎？
> [name=chihao y]

- 方便搜尋，現在超難搜尋到 beta.hackfoldr，所以也很難找到自己過去編輯過的 hackfoldr
> [Yun-Chen Chien](https://g0v.hackpad.tw/ep/profile/Ejqy5OUbvui): 意思是要讓  Google  能搜尋到foldr的內容嗎？
> [name=chihao y]

> 算是吧，但是在我自己記起 beta.hackfoldr.org 之前，我連 hackfoldr 的 beta 網址都找不到
> [name=Yun-Chen C]

- foldr內搜尋（小四）
- foldr介面整合Google doc文件權限管理（小四、chihao）
- 介面希望乾淨一點 (Shu)
    - label 堆疊後會長的有點亂,
    - folder/items/selected item 的 style 可以設計得更直覺
    - 陰影的運用有點太頻繁，回應上面的留言，可以參考 [gitbook](https://www.gitbook.com/) +1  或是 [feedly](http://feedly.com)
> 現在有哪些覺得不乾淨的地方嗎？XD
> [name=chihao y]

- 介面上方的儲存提醒「save/存檔」，會遮蔽到 hackpad 功能列
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_568b274062eca86f2feab352bf4e8ec0)
- typography會加強（chihao）
- 希望可以有按鈕可以把嵌入的頁面另開分頁開啟，不會被嵌入 hackfoldr 內（小蟹）
> 了解。現在在option設定{target: "_blank"}無法滿足需求嗎？
> [name=chihao y]

- [http://www.slideshare.net/autang/hackfoldr-pdistw](http://www.slideshare.net/autang/hackfoldr-pdistw)（au @ hackath21n 提案）
    - allow better visibility on e.g. Facebook (au)
    - static hackfoldr
        - 輸入beta.hackfoldr.org/g0v-hackath21n，產生g0v-hackath21n.html
            - 網址相同，分享不會404
        - 網址要短
        - 更新要快
        - .csv, .json每分鐘匯入gh-pages自動備份內容？（magic-mirror）
        - 只要有gov.tw email就可以建foldr，邀請人協作
        - 越簡單越好
    - [PDIS/web#1](https://github.com/PDIS/web/issues/1)
        - authenticating a *.gov.tw/sinica.edu.tw user: [https://github.com/PDIS/tools-manage-sandstorm/blob/master/auto\_auth\_user.js#L83](https://github.com/PDIS/tools-manage-sandstorm/blob/master/auto_auth_user.js#L83)
- [Hackfoldr與公務員訪談](https://g0v.hackpad.tw/Hackfoldr-IYApEmPmPI7)@hackath21n
- 進入 hackfoldr 的某一個頁面網址，左側的目錄欄位並沒有打開，可能預設即不展開，以至於使用者會不曉得當下頁面是在哪一個層級位置之中，雖然有可能管理者在後台本來的設定即不展開，但對於使用者來說，造訪該頁面的時候，我認為使用者者可以在左側欄位看到該頁面所從屬的層級是比較好的。
    - 例如點擊此頁面後（[http://hackfoldr.org/POPonFire/XpdD57S2RIZ](http://hackfoldr.org/POPonFire/XpdD57S2RIZ)）左側目錄因為沒有預設展開，所以會不曉得此頁面「公有地砍柴網頁或公開資料網址」是屬於「data & DB」的層級之中。
- 從訪問整理出來的需求
> 訪談記錄在：[公務員與Hackfoldr](https://g0v.hackpad.tw/Hackfoldr-IYApEmPmPI7)
> [name=chihao y]

    - 最大問題：資安的擔心（peggy）
    - 個別管理文件權限要很小心（peggy）
    - Google Spreadsheet要發佈，所以搜尋得到，所以文件需要鎖得很好，常用Anyone with link，這樣就不太行（peggy）
        - 很容易出錯（chihao）
        - 自己maintain gmail list控管權限（小四）
    - 比起網站，hackfoldr覺得不太正式，無法取代「架站」這件事（peggy）
    - 市府沒有Google Account（chihao、社會局）
    - 小四：數位落差
- custom domain（洪國峰）
- ttcat
    - hackfoldr沒有landing page、英文introduction
    - 現在加了g0v search，才能search
    - 要列出誰使用hackfoldr
    - 要有募款video
    - 列出重要的use case、inspire大家，通常都是
    - 讓別人知道：hackfoldr 很短很快同時讓很多人看到
    - 內容都是中文，外國人看不懂
    - foldr api --> 自己做版型
    - 第一次使用的步驟教學

## 參考

Hackfoldr目前的repo：[https://github.com/hackfoldr/hackfoldr-2.0-forkme](https://github.com/hackfoldr/hackfoldr-2.0-forkme)

