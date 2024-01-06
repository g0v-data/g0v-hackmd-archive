---
title: "⭐ 步驟 - 如何使用 gitbook 寫書"
tags: 新手教學,零時的學習不能等,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/wHnCZ8AyqBe)


```
### 什麼是 gitbook


```
gitbook 是好用的寫書工具，可以用來解釋有點複雜、沒辦法一頁說完的事情。當你開始寫書，它就馬上自動生出一個線上閱讀的網址，讓你可以把最新進度貼給別人看，你寫到哪，別人就可以看到哪。像是：
```
- [自經區](https://fepztw.github.io/)[自經區手冊](https://fepztw.github.io/)[手冊](https://fepztw.github.io/)
- [群](https://crowdfunding.vtaiwan.tw/)[眾募資](https://crowdfunding.vtaiwan.tw/)、[公司法](https://closelyheld.vtaiwan.tw/)（vTaiwan之後還會有 8~9 本）
- [憲餅食譜100道](http://ipa.gitbooks.io/constitution100/content/)

### 跟 gitbook 有關的宅宅名詞們


- git 是幫你管理文件版本的工具，它管的文件通常是程式碼，但也可以是一般純文字文件
- github 是幫你管理 git 的工具，原本在用的人比較多是工程師，但網頁介面變得越來越和藹可親、推出可愛的 app 以後，越來越多正常人使用了
- gitbook 是幫你利用 github 的版本管理功能來寫書的工具，為了讓正常人使用所以有 web editor，如果需要離線寫書的話也有可愛的 app 可以用

## 步驟


### 申請 github 與 gitbook 帳號


1.  **申請 github 帳號**
    - 帳號申請：[https://github.com/](https://github.com/)![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_74481743b36c1d24f05737c9cd60bc0b)
    - （optional）如果需要離線寫書的話，要另外：下載與安裝 github app
        - mac 版下載：[github for mac](https://mac.github.com/)
        - windows 版下載：[github for windows](https://windows.github.com/)
2.  **申請 gitbook 帳號**
    - 帳號申請：[https://www.gitbook.com/](https://www.gitbook.com/)
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_14d6041038306e3887b4b778f04982ad)
    - （optional）如果需要離線寫書的話，要另外：下載與安裝 gitbook app
        - linux 版 / mac 版 / windows 版下載：[gitbook editor](https://github.com/GitbookIO/editor-legacy)
> 離線版停止維護了 XD 如果可以用 Chrome/Firefox 的話，推薦使用線上編輯界面
> [name=Audrey T]

> 線上編輯界面目前實測，IE10 無法使用。
> [name=Audrey T]

    - （optional）加入 g0v 零時政府的 GitBook 團體：[https://www.gitbook.com/@g0v](https://www.gitbook.com/@g0v)

### 在 gitbook 開一本新的書


很簡單，在一登入的 dashboard 畫面，按下 create a new book 綠色按鈕，輸入書名跟想要的網址就可以了。
1.  瞧瞧這好精美的 dashboard![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_873480024b415ab4bb3f2d595b1762a6)
2.  瞧瞧這好精美的 new book![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_6182f1dc19a0045fb40c05bf4f4f8b8c)

### 開始寫書

打開 Editor 之後，從左上角的 Table of Contents 選擇要編輯的檔案

### 寫到一個段落，存檔發佈

按 Save 按鈕儲存（上方工具列最左邊那個）

### 請別人來幫忙寫書

1.  個人帳號底下的書
    1.  在書的設定頁（Settings）邀請協作者（ Collaborators）
2.  團體（organization）底下的書
    1.  將別人加入團體，並給予編輯權限
    2.  在書的設定頁（Settings）邀請協作者（ Collaborators）
    以上兩種方式可設定標示作者的方式不同。

### 寫別人的書

需被加入擁有該書的團體，或是被加為協作者。

### 在沒有網路的地方寫書

可能得透過 Git 在本地端編輯了。

## gitbook  架構

gitbook主要分為四個部分。

### SUMMARY.md

這是書籍的目錄結構，裡面是內容的部份。結構請參考此：
[http://help.gitbook.io/book/chapters.html](http://help.gitbook.io/book/chapters.html)
> 如果要指定子目錄的檔案，子目錄開頭不能是底線
> [name=nchild]


### README.md

這是書籍的前言，不用把它加在目錄結構裡面。

### 1-0.md 1-1.md 1-2.md.....

這些是章節內容，如1-2代表第一章第二節。不過命名方式沒有強制，只要SUMMARY中有定義就可以。

### cover.jpg cover_small.jpg

這是封面
尺寸如下：
cover.jpg 1800x2360
cover_small.jpg 200x262

### book.json

參數設定用，說明請見：[http://help.gitbook.com/format/configuration.html](http://help.gitbook.com/format/configuration.html)
> 使用 structure 為 readme 重新指向時，目標檔案要在根目錄。
> [name=nchild]


## Working with GitHub

如果要用 GitBook 連結一個現有的 GitHub repo.，則必須有該 repo. 的權限。
以 g0v dev team 的 repo. 為例，需要：
- 找一個已經在 [g0v GitHub](https://github.com/orgs/g0v/people) 團體裡面的人，然後請他將你的帳號加入 [dev team](https://github.com/orgs/g0v/teams/dev)
- 請至您  GitHub  的帳號 email  收信，並同意邀請加入  g0v
- 在 GitBook 帳號設定（Account Settings）裡面連結你的 GitHub 帳號（Connect to GitHub）
- 找一個已經在 [g0v Gitbook](https://www.gitbook.com/@g0v) 團體裡面的人，然後請他加入你的帳號

### 參考書本內容

[https://github.com/billy3321/TaiwanFEPZS](https://github.com/billy3321/TaiwanFEPZS)
### 相關文件

[http://gitbookio.gitbooks.io/documentation/](http://gitbookio.gitbooks.io/documentation/)

