---
title: Shoutout bug report
tags: web3
---

# Shoutout bug report


請大家用以下格式寫 bug
Status 請留給工程師填寫

- [ ] issue date:
Title：
Severity/Priority：
Description：
Environment：
Steps to reproduce：
Expected result：
Actual result：
Attachments (screenshots, videos, text)：
Issue taker :
Status :


---




- [ ] **for 昶維&Matt大大** 時間 2023.3.31 from Peixing
Title：SOB重複發文
Severity/Priority：
Description：使用者先發了一篇SO文，SOB會同步發一篇訊息，但如果有修改需求，重新編輯了SO原文後送出，SOB會把原PO跟編輯過後的文當成兩條獨立資料，再發一條SOB訊息，編輯幾次就會發幾次，造成洗版狀況。

SO原PO:修改"超勾" --->"超勾錐" https://g0v-tw.slack.com/archives/C046ZFGTWQK/p1680253534012839?thread_ts=1680178274.325589&cid=C046ZFGTWQK
SOB訊息：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a6444f23cfaea68abd249d25f1bd38a9.png)


Environment：
Steps to reproduce：
Expected result：
Actual result：
Attachments (screenshots, videos, text)：
Issue taker :
Status : 還需修正中，應該下週會好，也會再問一下 Tim。


---
- [ ] issue date: 2023.04.29 from Peixing
Title：**SO內容沒有進來、數量計算有誤**
Severity/Priority：
Description：
讚爆數量似乎無法正確計算?
4/19登入的時候是172，前幾天登入是170，剛剛登入變成168
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5a483db57bdbc7734a73f311691b2621.png)

在比對了個人版的數量，發現是有些so內容沒有抓到，比如4/21的紀錄就沒有進來，在個人版看不到，在公共版也沒有
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ffbd4fe2a28f7b6d8926a4c60ca8c40c.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a0976d51ba602a0fa5961f177b99cc90.png)


Environment：
Steps to reproduce：
Expected result：
Actual result：
Attachments (screenshots, videos, text)：
Issue taker :
Status : 目前不確定原因為何，可能是七天以前的會不見，改底層邏輯，不是去抓而是把訊息送進資料庫。從底層改需要一兩週的時間。

---
- [ ] issue date:2023.05.17-18 Peixing
Title：**SOB消失惹...**
Severity/Priority：
Description：發文之後，沒有出現SOB跟gif QQ
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_953e6574466c63b12edf6a82cd4afde2.png)

Environment：
Steps to reproduce：
Expected result：
Actual result：
Attachments (screenshots, videos, text)：
Issue taker :
Status 

----


## Closed issues

---
- [x] issue date: 2023.04.24 from 豆腐
Title：**抓到ShoutOut bot的自己的發文**
Severity/Priority：
Description：
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7f63f576ccef178acda153f7b4f60d1d.png)

補充：主要發生在個人版，而且抓到的SOB發文包含自己送出的SO XD
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_9857db51be7ffcdaf2d1db08d6cf7368.jpg)

Environment：
Steps to reproduce：
Expected result：
Actual result：
Attachments (screenshots, videos, text)：
Issue taker :
Status : 目前先加了一段防止的程式碼，目前是沒有這個問題了，先 Close

---
