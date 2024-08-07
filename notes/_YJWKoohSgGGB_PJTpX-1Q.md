---
title: "UX flow"
tags: hackpad
---

# UX flow

> [點此觀看原始內容](https://g0v.hackpad.tw/5H2xveFL3z2)

此文件路徑：[全民除黴計畫hackfoldr](http://hackfoldr.org/app4am) / 系統設計 / ==這裡==

==記得盡量考慮所有會操作到的功能及相關反應：==
- 元素：按鈕、區塊、圖片、硬體功能按鈕
- 使用者動作：單點、長按、滑動、停止、硬體感應器*
- 元素反應：單點、長按、滑動、位置連動

## 怎麼看這頁資訊

- [ ] 此頁存在的目的
- [ ] 大項目 (所有子項目討論定案後勾選)
    - [x] 子項目1  (確定使用，如果計劃在中後期使用也勾此項並註明)
    - [ ] ~子項目2~ (討論後移除)
    - [ ] 子項目3 (未討論或未定案,後面註明狀態)
主要區塊：顯示該頁面的主要功能
次要區塊：方便連結到其他功能或頁面但不刻意強調，甚至稍微隱藏起來的區塊

## I.啟動畫面

- [x] 使用
    - [x] 增加品牌印象
    - [x] 緩衝讀取時間
    - [ ]
- [ ] 不使用
    - [ ] 原因：

## II.功能教學頁

相關頁面：
    - [ ] 第一次開啟App
    - [ ] 第一次進到議題列表
    - [ ] 第一次進到評價畫面
    - [ ]
連結：下一頁、跳過
按紐：

備註：新聞學的教學影片　<--之後看看獨立出來


## III.Menu

- [ ] 表現形式：螢幕左測滑出
- [ ] 選項
    - [x] 回到首頁
    - [x] 議題列表
    - [ ] ~新聞列表~
    - [x] 追蹤列表 (名稱待訂)
    - [x] 啄木鳥定期報告
    - [x] 設定
    - [ ] ~快速設定~

## 1.主頁

- [ ] 相當於App的門面，基本形象及好感度的出發點
- [ ] **NavBar /** ~Tab~
    - [x] Logo (顯示logo時盡量只單獨顯示)
    - [ ] Title
    - [ ] Layout
    - [ ] Filter
    - [ ] Reload (需討論用按鈕或下拉式更新)
    - [ ] Share
    - [ ] Setting
- [x] **主要區塊**
    - [x] **焦點議題 (大圖)**  連結→ 該議題相關新聞列表
    - [x] **精選議題 (**  連結→ 該項議題相關新聞列表
        人工分類後的議題才可被選為精選議題(顯示在首頁)
    - [x] **熱門新聞/使用者自訂新聞(直式，Lazyload)  連結→ 單篇新聞內容**
        新聞列表:今天最新的20篇
> 原本規劃直接在主頁空間往下拉就可以看到新聞列表，但是可能會使得app初始載入速度較慢影響使用體驗，另外在議題與新聞的排版平橫上也比較難以兩全。
> [name=Rhozan]


- [ ] **次要區塊**
    - [ ] 所有議題列表
    - [ ] 新聞列表 → ==轉換到新聞頁面 or 直接在下面載入&展開？==
> 這項的作用在於讓使用者可以快速進到單一項目列表，除了方便性之外，也是推廣讓使用者習慣用議題來看新聞的柔性行銷。
> [name=Rhozan]

- [ ] **系統按紐**
    - [x] BACK：按一次 → ==III.Menu==， 連按兩次→ ==<退出App>==
    - [x] MENU： 叫出→ ==III.Menu==


## 2.議題列表

- [ ] 初期如果無法讓程式自動歸類出議題的話，也許就先不做這個頁面，或是變通為：
    - [ ] 開放編輯資格到G0V或新聞相關社群，實驗看看成效好不好(當然還是要有app帳號)
    - [ ] 不用全部人工輸入議題名稱，人工做不到的部分就顯示系統自動歸類出來的關鍵字
- [ ] ~NavBar~ **/ Tab (議題類別)**
    - [ ] ~Logo (顯示logo時盡量只單獨顯示)~
    - [ ] Title
    - [x] Layout (快速切換 簡單/完整 瀏覽
    - [ ] Filter
    - [x] Reload (需討論用按鈕或下拉式更新)
    - [ ] ~Share~
    - [ ] Setting
- [ ] **主要區塊**
    - [x] **各類別之議題列表**  連結→ 該議題相關新聞列表
- [ ] **次要區塊**
    - [x] 無
- [ ] **系統按紐**
    - [x] BACK：==回上一層==
    - [x] MENU： 叫出→ ==0.功能選單==

## 新聞列表

- [ ] 依據多項參數排序新聞，為此App最常被瀏覽的頁面之一
- [ ] **NavBar / Tab (新聞類別)**
    - [ ] ~Logo (顯示此項時盡量只單獨顯示)~
    - [x] Title
    - [x] Layout (快速切換 簡單/完整 瀏覽
    - [x] Filter
    - [x] Reload (需討論用按鈕或下拉式更新)
    - [ ] ~Share~
    - [ ] ~Setting~
- [ ] **主要區塊**
    - [x] **各類別之議題列表**  連結→ 該議題相關新聞列表
- [ ] **次要區塊**
    - [x] 無
- [ ] **系統按紐**
    - [x] BACK：==回上一層==
    - [x] MENU： 叫出→ ==0.功能選單==

## 追蹤列表

- [ ] 讓使用者能持續關注有興趣/有評論...等等的議題或新聞
- [ ] ~NavBar~ **/ Tab (議題類別)**
    - [ ] Logo (顯示此項時盡量只單獨顯示)
    - [ ] Title
    - [x] Layout (快速切換 簡單/完整 瀏覽
    - [ ] Filter
    - [x] Reload (需討論用按鈕或下拉式更新)
    - [ ] Share
    - [ ] Setting
- [ ] **主要區塊**
    - [x] **各類別之議題列表**  連結→ 該議題相關新聞列表
- [ ] **次要區塊**
    - [x] 無
- [ ] **系統按紐**
    - [x] BACK：==回上一層==
    - [x] MENU： 叫出→ ==0.功能選單==


## 新聞頁-內文

連結：
按紐：

## 評價分析頁

連結：
按紐：

## 新聞頁-打臉

連結：
按紐：

## 新聞頁-長文分析

連結：
按紐：

## 打臉輸入頁

連結：說明頁
按紐：
限制：30~150字、實名登錄

## 長文輸入頁

連結：
按紐：

## 設定頁面

連結：
按紐：

## App可操作功能


1.  瀏覽資訊
2.  轉貼分享
3.  投票評價
    - 快評
    - 評價打臉
    - 評價長文
4.  撰文 (包含附加檔案在內的編輯功能)
    - 抓出違規項目 (打臉)
    - 長文回覆 (分析)
5.  檢舉
6.  功能設定 (不照顯示順序)  (最好是全域式menu方便快速叫出)
    - 帳號綁定
    - 帳號資訊
    - 顯示風格 (不一定會有)
    - 字型大小調整
    - 螢幕亮度調整  (也考慮和一些常用功能拉出去放外面)
    - 新聞屏蔽設定
    - 新聞轉貼設定
    - 使用說明
    - 關於APP (含常見說明)

### 涉及控制裝置硬體的功能

- 螢幕亮度控制
- GPS定位  (顯示附近重要新聞，後期計畫)




## 以下舊資料， 詳細流程說明

### 瀏覽資訊

不用特別說明 (應該不用限制吧？)

### 轉貼分享

- 未綁定使用者：一律轉貼Web網站網址
- 已綁定使用者：
    - 選擇要轉貼Web或原新聞網站，若是原新聞網站則附加目前分數及警語。

### 投票評價

- App 介面
    - 未綁定使用者：只能瀏覽
    - 一般使用者：(前略) → 單篇新聞內文 → 拉到底顯示評論案鈕 → 列出選項 → 投票確認 → 完成評價 (送出即不可更改)
> 可展開看到違規細項但無法選擇。
> [name=Rhozan]

    - 評論員： (同一般使用者) → 如果有選擇細項就進入評論輸入介面 → 撰寫說明 → 完成打臉。
    - 長文回覆(限評論員)：進入議題模式 → 選擇議題 → 選擇發表分析 → 撰寫摘要(超短評)、內文及附加檔案 → 完成。
> 尚需討論： 評論員評論前是否可以看到其他人的評論
> [name=Rhozan]


- PC 介面
    - 未綁定使用者：只能瀏覽
    - 一般使用者：如果已有綁定裝置便可評價，形式相同
    - 長文回覆(限評論員)：仿照一般論壇發文形式，只是需額外選則「違規分類和違規細項」


### 撰文



### 檢舉

- 未綁定使用者：無法檢舉
- 其它使用者：
    - 進到單一新聞頁面 → menu → 檢舉 → 點選理由、附加說明 → 同意條款 → 送出


## Template



