---
title: "vTaiwan架站指南"
tags: vTaiwan.tw, hackpad
---

# vTaiwan架站指南

> [點此觀看原始內容](https://g0v.hackpad.tw/lejAGhPK0Jm)


### A機器：

[https://github.com/discourse/discourse_docker](https://github.com/discourse/discourse_docker)
discourse，以docker安裝discourse，預設就有提供json API
- containers/app.yml
  DISCOURSE\_ENABLE\_CORS: true
 DISCOURSE\_CORS\_ORIGIN: '*'

CloudFlare Rules:
```
https://talk.vtaiwan.tw/t/topic/.json
https://talk.vtaiwan.tw/c/.json
Custom Cache: On
Edge Expire: 2hr (or 1hr for pro)
Browser Cache: 30min

```
- 在管理員->API->產生金鑰
- 開一個總帳號（如 sdparty），授予板主、管理員、信任等級四
- 首頁按「新分類」，安全設定如下：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9bdaff67c84e33fd8ddcf9828b8db338)
- 新分類的預設文章作者，如果要改成系統用戶，可以按右上方的扳手按鈕，按「選取要移動的文章」、「選取全部」、「變更擁有者」即可。

基本設定裡，將子分類設為固定順序：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_84b6730920dc0066fb6da9c3e75e55c5)
取得分類的 ID:
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7f74222cc2c16ab7bc0a7c426c242bee)

### B機器：

靜態網站機器，以angular串起gitbook及discourse
[https://github.com/g0v/vtaiwan.tw](https://github.com/g0v/vtaiwan.tw)

### 小字典：

在 Google Spreadsheet 裡，複製 [vTaiwan 小字典](https://docs.google.com/spreadsheets/d/1CGni6oPLXliLGWleBSCHYd3zQfsiIc5-SSOfS3F9TTg)（File -> Make a Copy -> Move to Drive），將頁籤名稱改成與討論議題同名，再按 Publish：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_aecfb0bdca4eaefcffe060bc615a6b9d)

### GitBook 建置（本機端）：


在 package.json 裡，spreadsheet ID 從 published sheet 處取得，再加上頁籤序號到「republish:lexicon」即可。

```
sudo npm i -g gitbook
npm i
npm run republish:lexicon
gitbook install
env API_KEY="discourse API key" gitbook build
npm run republish:lexicon

```
在 book.json 裡，parent\_category\_id 由上述「分類 ID」取得：
```
    "discourse": {
    "url": "https://talk.sdparty.tw/",
       "api_key": "",
       "api_username": "sdparty",
       "parent\_category\_id": 5,
       "parent\_category\_name": "問題討論：新經濟"
    }


```
### patch pg 以支援中文全文檢索


在discourse機器上，進入app內
```
su postgres
psql
update pg\_database set encoding = pg\_char\_to\_encoding('UTF8') where datname = 'discourse' AND encoding = pg\_char\_to\_encoding('SQL\_ASCII');

```
再回到外層，launcher rebuild app 即可。（[pull request](https://github.com/discourse/discourse_docker/pull/130) 已送回上游）

### patch onebox gem 以支援  FB、PTT 貼文


在discourse機器上，進入app內

修改 /var/www/discourse/Gemfile

把

```
gem 'onebox'

```
修改為

```
gem 'onebox', git: 'https://github.com/billy3321/onebox.git'

```
在/var/www/discourse內執行

```
bundle install --no-deployment
bundle update onebox

```
修改 /var/www/discourse/config/unicorn_launcher

在檔案上方加入：

```
export FACEBOOK\_APP\_ID=""
export FACEBOOK\_APP\_SECRET=""

```
最後，重開機器即可！

