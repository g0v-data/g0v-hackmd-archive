---
tags: g0v-summit, 2020
---

# Proposal 提案系統技術文件

## 相關資訊

* 提案系統由三個 application (API backend, frontend, discuss) 組成，採前後端 API 架構。
* 帳號管理統一由 API server 做 oauth，目前有 FB, google, github, slack 登入，slack 登入需要 slack admin approve。
* 建立帳號以後，會同步寫入 common domain cookie，discuss 會讀取 common domain cookie，所以 discuss 不用另外登入。

### Todo & discuss

#### 徵件公告後的修改流程 08/15

- 使用者旅程：
  1. 身為**確定中選的講者**，我想要有一個方便更改、確認稿件、講者資訊的網站，讓我在必要時，可以修改。
  2. 身為**議程組**，我想要有一個方便審查稿件修改的功能，減少與講者信件往返、組內溝通的成本
  3. 身為**議程組**，我想要有一個修改稿件、講者資訊的後台，讓我在必要時也能主動更新官網內容
- 發布時間點：
  - 08/22: 讓入選的講者可以更改他們的議程
  - 議程公開時（預計 09/01 售票）：完成通知、審核、以及更新主網站的資料流程
- 需要的額外功能： 
  1. ~~審稿確認網站~~新頁面：提供 `議程組` 審核與管理新增的修改（類似 Github PR ）
     - 在徵件網站，顯示所有入選，顯示最後的版本有沒有被 verified
     - 需要 email 當 oAuth white list
     - 在 `/me` 標是不是 admin
     - 顯示 diff ，API 提供多版本
  3. ~~送信機器人：檢查是否有新稿件，並會送通知信的~~
     1. 須提供信件文案，理想上支援雙語，方便 `議程組` 直接轉寄給講者，但不強求
     2. 可定期檢查，或 push notification ，看實做方式
     3. **在徵件網站**
  4. ~~讓議程組編輯議程，並合併進主網站的邏輯~~
- 需要調整的既有功能：
  - `徵件網站`：
     1. **howard** `後端` 將提案公開顯示的版本，固定在目前的版本，就算之後講者有任何修改，也不改變顯示的內容
        - [x] 幫 project 上有沒有被選上（幫忙手動標）
        - [x] 幫 version 上 verified: `boolean`
     2. **howard** `後端` 送信機器人：檢查是否有新稿件，並會送通知信的
        1. 須提供信件文案，理想上支援雙語，方便 `議程組` 直接轉寄給講者，但不強求
        2. [x] 有新增 version 時，寄信
        3. 文案：
           - 標題： `[稿件變更審查] {{提案華語}} {{提案英語}}`
           - 內文：
             ```
             {{提案人1的顯示名稱}}的提案：{{提案華語}} {{提案英語}} ，提交新的變更囉。

             1. 請點此審查： {{審查網址}} 
             2. 若要聯絡作者，請寄信至 {{投稿帳號信箱}}

             變更內容：
             1. {{變更欄位名，英語即可}}
                - 變更前： {{最後一版 verified 的內容}}
                - 變更後： {{最後一版未 verified 的內容}}
             2. {{另一個變更的欄位}}
                - 變更前： ...
                - 變更後： ...
             ```
           - 審查網址： `https://propose.summit2020.g0v.tw/proposal-admin?id=<project_id>`
        5. [x] 寄出異動內容
     4. [x] **howard** `後端` 讓入選提案可以被講者修改
     7. [x] **howard** `後端` 一個需要 API key，可以取得所有已錄取的議程的所有欄位（包含不公開）資料的 API ，供 `機器人`、`主網站 CICD` 使用
     8. **howard** `後端` 提供 `議程組` 審核與管理新增的修改（類似 Github PR ）
        - [x] 需要 email 當 oAuth white list
        - [x] 在 `/me` 標是不是 admin
        - [x] 顯示 diff ，API 提供多版本
        - [x] 審核 API
     3. [x] **ddio** `前端` 讓入選提案可以被講者修改
     5. [x] **ddio** `前端` 在講者編輯後，提醒講者這些更改必須經過議程組同意後，顯示於主網站，徵件網站的顯示內容將不會再更新
         - 編輯時
         - 如果最新版 verified === false
         - **ddio** ==須提供文案==
     9. [ ] **ddio** `前端` 提供 `議程組` 審核與管理新增的修改（類似 Github PR ）
        - 在徵件網站，顯示所有入選，以及是否 verified
        - 在 `/me` 標是不是 admin
        - 顯示 diff ，API 提供多版本（最後一次 verified + 最後一版）
     10. `前端` `後端` `很久之後` 在活動結束後，轉為靜態網站，減少維護成本
     11. 瀏覽投稿頁，在 API 修改後，error
  - `主網站`：
     1. [ ] **ddio** 新增議程修改、合併的邏輯，並將確定的議程資料存到 git 的雙語語系檔
     2. [ ] **ddio** 給議程組的 airtable
- 工作流程：
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6ee345b3181f926f755fdac98c882db9.jpg)
  - ==8/22 確定議程時：==
    1. `議程組` 提供確定錄取的稿件標題 + ID 給 `Howard?`，手動更新資料庫
  - ==講者想要修改議程時：==
    1. `講者` 登入議程網站，編輯稿件內容，點選儲存
    2. `審稿確認網站` 顯示目前所有 8/22 後新增的修改，以及每項修改是否已被 `議程組` 同意
    3. `機器人` 發現有講者修改稿件，將更改的部份，以及 `審稿確認網站` 的連結，發送通知信到議程組群組信箱（ programming@summit.g0v.tw？）
    4. `議程組` 在收到通知信後，點選連結進入 `審稿確認網站` ，進行審核，審核期間可自行與講者溝通修正內容，最後同意修改的內容
    5. `Summit 主網站` 在收到修改確認後，更新 `Summit 主網站` 議程資訊
  - ==議程組想要修改議程時：==
    1. `議程組` 進入議程組專用 Airtable ，找到想要修改的議程，並更新想要修改的欄位
    2. `Summit 主網站` 在收到修改確認後，更新 `Summit 主網站` 議程資訊
  - ==當 `講者` 與 `議程組` 修改到同一個欄位時：==
    1. 以取下列兩者較晚更新的：
       1. `講者` 最後一次被同意的修正
       2. `議程組` 最後一次的修正
- 目前的限制：
  - 不可修改議程時間
- 需要的額外資料：
  - 議程組 email 清單
  - 確認錄取的稿件標題 + ID

#### 停止投稿 @ 7/15 23:59:59

前端
- [x] remove index page btn
- [x] remove `/proposal-create` route
- [x] cannot be updated without any version

後端
- [x] remove `Project Create` API

#### Prepare stage

* `F2E` Frontend framework
* `F2E` Mutiple language
* `F2E` Frontend pages
* `F2E` Frontend UI enhance
* `Howard` [v] Embed discuss
* `Howard` discuss UI enhance
* `Howard` [v] Clear draft after save
* `Howard` [v] Set enable after save
* Production deploy - 6/4
* Timeline
    * Production 6/4
    * Stop proposal 6/28
    * Stop discuss 7/30
    * Stop edit 8/2
    * Announcement 8/23 or 8/28

### 技術線
* 後端(API backend) - Node.js + express + mongodb + PM2
* 前端 - vue / vue-cli
* Web servece - nginx
    * reserve proxy 3000 to api backend
    * reserve proxy 4567 to discuss
* 討論區(Discuss) - nodebb (nodejs, mongodb)

### Stage server
* proposal - propose.summit2020.pre-stage.cc
* api - api.summit2020.pre-stage.cc
* discuss - discuss.summit2020.pre-stage.cc

### Production server
* to do

### 程式碼

* UI - https://github.com/g0v/summit_proposal

### 功能討論
https://g0v.hackmd.io/hgCQwo6hT2SFO2fH-8a-Kw

## 開發文件

### 前端頁面

#### 跨頁功能 

- [x] 1 - `lai` 頁面權限控管，讓編輯相關頁面，只有登入者、提案者才能進入
- [x] 2 - 登出時的友善提示
- [x] 3 - `ddio` 基本的英文資訊，例如選單、登入、提案與各種 CTA 按鈕，確定非華語讀者可以順利讀到專案
- [x] `lai` 4 - 用環境變數設定後端 API 網址，方便切換 staging / production
- [x] `lai` 5 - header/title tag + og:xx twitter:xx

#### 共用 Common

`Lai`

* [x] 1 - Header (RWD)
    * Logo
    * 首頁
    * 投稿列表
    * 投稿辦法
    * FAQ
    * 關於我們
    * 歷年議程
    * 登入 or Avatar (Avatar hover )
* [x] 2 - Footer
    * Copyright（須確定要用 Copyright 而不是 CC）
    > 應該是要 cc，是我弄錯 [name=Howard]
    > CC 也有問題，目前使用條款看起來其實只能用 Copyright ，因為提案可以不同意以 CC 釋出 XDDD  [name=ddio]
    > 這樣啊，那還是先放 copyright 好了，由儉入奢易嘛 [name=Howard]
    * 其他 resource (目前先不放)
* [x] 3 - `Lai` Login Modal
    * FB、Google、guthub、slack
    * 需顯示同意書（[文案](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view#g0v-summit-2020-%E5%80%8B%E4%BA%BA%E8%B3%87%E6%96%99%E8%92%90%E9%9B%86%E3%80%81%E8%99%95%E7%90%86%E5%8F%8A%E5%88%A9%E7%94%A8%E5%90%8C%E6%84%8F%E6%9B%B8)）


#### 首頁 (Main page)

`Lai`

- [x] 1 - `Lai` Hero - [文案](https://g0v.hackmd.io/7WDoYrC9Tla0qqk8RlO4ow?view#%E9%A6%96%E9%A0%81%E5%9C%96)
  * 瀏覽投稿 -> Proposal List
  * 我要投稿 -> Proposal Create
- [x] 2 - `Lai` 關於 g0v Summit - [文案](https://g0v.hackmd.io/7WDoYrC9Tla0qqk8RlO4ow?view#%E9%97%9C%E6%96%BC-g0v-Summit)
- [x] 3 - `Lai` 投稿辦法 - [文案]  -> 發問slack (https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view)
  * 投稿主題
  * 投稿時程(講者報名截止待決議)
  * 投稿方法(文字待 finalize)
- [x] 4 - `Lai` FAQ - [文案](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view#FAQ)
- [x] 5 - `Lai` 關於我們
   * 議程委員會 - [文案](https://g0v.hackmd.io/@Ywy8O1oUT1yJQUYgOPmfsw/rky9LmWj8)
   * g0v 介紹 - [文案](https://g0v.hackmd.io/7WDoYrC9Tla0qqk8RlO4ow?view#g0v-%E4%BB%8B%E7%B4%B9)
- [x] 6 - `Lai` 歷年議程
   * 2018 開放了？然後咧！ https://summit.g0v.tw/2018/agenda/
   * 2016 拆後重建 https://summit.g0v.tw/2016/schedules

#### 投稿列表頁 (Proposal List)

`Lai`

- [x] 1 - 列出所有已存檔的投稿，雙語資訊並列
- [x] 2 - Keyword search (欄位待定)，前端處理
- [x] 3 - 前端 pagination
- [x] 4 - 點選後進入個別投稿頁
- [x] 5 - 若為提案者，可直接點選進入修改頁面 -> 移至管理頁面
- [x] 6 - 作者本人給他一個 button 可以去編輯和提醒 draft
- [x] 7 - 搜尋先轉小寫
- [x] 8 - 主圖是選填的，加個灰底

#### 管理投稿頁

`Lai`

- [x] 1 - 顯示所有我建立的投稿
- [x] 2 - 標註尚未存檔，只有草稿的投稿
- [x] 3 - 可點選投稿，進入修改頁面
- [x] 4 - 若為提案者，可直接點選進入修改頁面
- [x] 5 - 加上提醒有 draft (待測)
- [x] 6 - 點選的手指頭

#### 詳細投稿資訊頁 (Proposal Detail)

`Lai`
- [x] 1 - 顯示所有公開資訊，雙語資訊並列
- [x] 2 - 若為提案者，顯示隱私資訊，點選後可進入修改頁面(移到管理)
- [x] 3 - 顯示 versions -> 都全部顯示，version 從 1 開始
- [x] 4 - embed discuss
- [x] 5 ? 所有欄位都要放嗎？例如是否接受錄影紀錄 -> 都全部顯示-> 欄位有其他的要注意
- [x] 6. RWD
- [x] 7. 顯示講者資訊


#### 建立投稿/修改投稿 (Proposal Edit)

`ddio`

[欄位參考](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view#%E6%8A%95%E7%A8%BF%E6%96%B9%E6%B3%95)

覺得今年 COSCUP 的徵件頁面設計滿好的，用字也比較親切，可參考
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4e9eca6fb0c1013ab0e9211861cef242.png)


- [x] 1 - 建立投稿時，先在後端開好 id ，方便和重用修改投稿的 component
- [x] 2 - 欄位同時顯示雙語，開頭先讓提案人選擇文件主要語言 / First Language ，相關欄位的必填根據主要語言調整
- [x] 3 - 先填稿件內容，再填提案人資訊，提案人 1 ~ n 人，n 根據提案形式而有不同
- [x] 4 - 若資料有變動，blur 時存 draft，其餘時間 throttle 30 秒存 draft
- [x] 5 - 支援將圖片存在 imgur
- [x] 6 - 各欄位長度、格式、必填檢查

#### 0606 網站上線前調整
- [x] 1 - `Lai` meta 調整 -> follow API
- [x] 2 - `Lai` 網站部分內容可以加入有翻譯的英文內容
     - FAQ
- [x] 3 - `Lai` 加入 形式
- [ ] 4 - `hkazami` 翻譯投稿方法
- [x] 5 - `Lai` 投稿時程更新，請參照[投稿時程表](https://g0v.hackmd.io/iqKSTK42QXu3iRB2vGnLFw?view#%E6%99%82%E7%A8%8B%E8%A1%A8)
- [x] 6 - `Lai` 登出時的友善提示 -> 簡單的 alert
- [x] 7 - `Lai` 登入 lightbox z-index 要蓋住其他頁(例如detail 的 cover)
- [x] 8 - `ddio` 提醒文字可以加上英文


### Use case
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_381607bc8294db1679fc3440483f49b9.jpg)

### Signin flow
1. Redirect to {APIURL}/auth/{provider}[?authCallback=https://my.frontend.com/auth-handler]
    * https://{APIURL}/auth/google 
    * https://{APIURL}/auth/facebook 
    * https://{APIURL}/auth/github 
    * https://{APIURL}/auth/slack 
2. Get token in query string
    * 登入完後，API server 會 redirect 回 authCallback，預設為 https://{FRONTENDURL}/auth，這個可以在 API server config.js 修改，也能直接在第一步驟加入 ?authCallback=xxxxx 傳入。
    * 建議將 token 存入 cookie。 (server 自己也會設好 cookie ，可跨討論區使用)
    * 需要授權的頁面，將 token 帶入 headers。
    ```
    Authorization: Bearer {token}
    ```
    
### Object define

#### User Object
* fields that owner only (_id, email, sub, provider)
```
{
    // User ID
    "_id": "xxxxx",
    
    // User email
    "email": "xxxxx@xxxx.xxx",
    
    // User 大頭圖片
    "picture": "https://xxxxx",
    
    // oauth Provide's user ID
    "sub": "xxxxx",
    
    // User name
    "name": "xxxxx",
    
    // Google or Facebook or Github or Slack
    "provider": "google"
    
    "isAdmin": true/false,
}
```
#### Project Object
* Project list 僅會顯示最後一個 version。
* 有登入才會有 draft。
```
{
    // project id
    "_id": "5ec767f91d6715034a828f5a",
    
    // user object
    "user": {User Object},
    
    // 目前統一是 summit2020，用以之後擴充
    "topic": "summit2020",
    
    // 用於表格 blur 暫存，防止使用者斷線重整遺失內容
    "draft": {Form Object},
    
    // 是否有送出的紀錄 aka versions.length > 0
    "enable": true/ false,
    
    // 每次 save 都會是新的 version
    "versions": [
        {Form Object},
        {Form Object},
        {Form Object}
    ],
    
    // 是否為 owner
    owner: true/false,
    
    // 是否入選
    selected: true/false,
    
    // admin 才會顯示，可以用 current 來判斷目前是否有新版本需要審核
    verify: {
        current: null or last non-verified,
        prev: last verified,
    }
    
    
}
```

#### Form Object
* Form Object 由前端補充，後端單純做 Read、Write。
* Backend config.js 可以定義公開欄位，project owner 才能看到所有欄位。
```javascript
{
    // docLanguage: ENUM, // required, zh-tw or en, 文件的主要語言, 
    // 因 0601 議程組討論後，不限制語言，所以刪除
    speakers: [{
        private_name: "", // required
        private_email: "",  // required
        private_gender: "", // required
        private_phone_number: "",
        private_accept_travel: Boolean, // required, 願意前往台灣
        display_name: "", // required
        organization: "",  // required, 組織或社群名稱
        avatar_url: "", // required
        city: "", // required, 講者所在地
        info_url: URL, // required, 講者資訊連結
        bio: "", // required, bio && bio_en 至少填一個, max 150 chars
        bio_en: "", // required, bio && bio_en 至少填一個, max 100 words
        
        // 因 0601 議程組決議，每個講者都要有
        private_channel: "",  // required, 你是如何知道 g0v 雙年會的
        private_channel_other: "", // optional, 選其他時
        private_misc: "", // 其他想說的話
    }], // max 2 if 演講, 4 if 主題論壇, 3 if 工作坊
    
    title: "", // required, 雙語至少則一
    title_en: "", // required
    summary: "", // required, 雙語至少則一, max 350 chars
    summary_en: "", // required, max 250 words
    oral_language: ENUM, // required, 演講使用的語言
    oral_language_other: "", // 其他時自填
    format: ENUM, // required, 形式（演講、主題論壇、工作坊）
    topic: ENUM, // required, 主題分類（請見 CFP 文件）
    three_keywords: ["", "", ""], // required
    related_url: "", 相關專案資訊連結
    cover_image: URL,
    is_presentation_cc40: Boolean, // required
    is_slide_cc40: Boolean, // required
    
    // extra info from backend
    createdAt: {iso 8601},
    verified: Boolean,
}
```

### API doc
* Patch or Post 使用 json body
* 成功請求回應 200，若有 body 皆為 json format
* 輸入錯誤回應 400，目前未加入錯誤 message
* 系統錯誤回應 500

#### User self info
```
Auth required: true

[GET] /user/me

Response:
{User Object}
```


#### User info
```
Auth required: false

[GET] /user/:id

URL parameter:
User._id

Response:
{User Object}
```

#### Project List
```
Auth required: false

[GET] /projects

Response:
[
    {Project Object},
    {Project Object},
    {Project Object}
]
```

#### Selected Project List for CICD
```
Auth required: true
Authorization: Bearer xxxx

[GET] /_/projects

Response:
[
    {Project Object},
    {Project Object},
    {Project Object}
]
```

#### Project Detail
```
Auth required: both

[GET] /project/:id

URL parameter:
Project._id

Response:
{Project Object}
```

#### Project Create
```
Auth required: true

[POST] /project

Response:
{
    // project ID
    "_id": "xxxxxxxx"
}
```

#### Project Draft
```
Auth required: true

[PATCH] /project/:id

URL parameter:
Project._id

Request Body:
{Form Object}

Response:
{}
```

#### Project Update/submit/save
```
Auth required: true

[POST] /project/:id

URL parameter:
Project._id

Request Body:
{Form Object}

Response:
{}
```

#### Project verified
```
Auth required: true (admin)

[POST] /project/:id/verified

URL parameter:
Project._id

Request Body:

Response:
{}
```

### imgur 上傳圖片
* HTML
```htmlmixed=
<button @click="$refs.file.click()">Upload</button>
<input type="file" ref="file" @change="handleFileUpload()" hidden />
```
* vue methods
```javascript=
async handleFileUpload() {
  let formData = new FormData();
  formData.append("image", this.$refs.file.files[0]);
  let imgur = await this.$axios.post(
    "https://api.imgur.com/3/image",
    formData,
    {
      headers: {
        "Content-Type": "multipart/form-data",
        Authorization: "Client-ID c5dc0de7bf21467",
      },
    }
  );
  let imgurID = imgur.data.data.id;
  
  // image url will be `https://i.imgur.com/${imgurID}h.jpg`
},
```

### 嵌入討論區
1. HTML
```
<a id="nodebb-comments"></a>
```
2. Javascript
```
const config = {
  // discuss URL
  discussURL: "https://discuss.summit2020.pre-stage.cc",

  // project._id
  projectID: "4",

  // project title
  projectTitle: "測試標題",

  // discuss category ID
  // 可能會調整，但之後會固定
  categoryID: 3,
};

var nbb = {};
var nodeBBURL = config.discussURL;
var articleID = config.projectID;

var articleData = {
  title_plain: config.projectTitle,
  url: location.href,
  tags: [],
  markDownContent: "",
  cid: config.categoryID,
};

(function () {
  nbb.script = document.createElement("script");
  nbb.script.type = "text/javascript";
  nbb.script.async = true;
  nbb.script.src =
    nodeBBURL + "/plugins/nodebb-plugin-blog-comments/lib/general.js";
  (
    document.getElementsByTagName("head")[0] ||
    document.getElementsByTagName("body")[0]
  ).appendChild(nbb.script);
})();
```




## 建置文件
1. Install nodejs 12.x + yarn(NPM) + PM2
2. Install mongodb 4.x
3. Install nodebb
4. Install Backend
    1. git clone backend
    2. Setup config.js
    3. Startup app.js
5. Install Discuss
    1. Install [nodebb](https://docs.nodebb.org/installing/os/)
    2. Install [nodebb-plugin-blog-comments](https://github.com/psychobunny/nodebb-plugin-blog-comments)
    3. fix plugin issue (replace the file content)
        * [node_modules/nodebb-plugin-blog-comments/library.js ](https://github.com/tnstiger/nodebb-plugin-blog-comments/blob/master/library.js)
        * [node_modules/nodebb-plugin-blog-comments/public/lib/general.js](https://github.com/tnstiger/nodebb-plugin-blog-comments/blob/master/public/lib/general.js)
        * [node_modules/nodebb-plugin-blog-comments/public/templates/comments/comments.tpl](https://github.com/tnstiger/nodebb-plugin-blog-comments/blob/master/public/templates/comments/comments.tpl)
        * [node_modules/nodebb-plugin-blog-comments/public/css/comments.css](https://github.com/tnstiger/nodebb-plugin-blog-comments/blob/master/public/css/comments.css)

    4. Install [nodebb-plugin-session-sharing](https://github.com/julianlam/nodebb-plugin-session-sharing)
    5. Rebuild and restart nodebb
    ```
    ./nodebb build
    ./nodebb restart
    ```
    6. Setup session-sharing config
    ```
    Set field below:
    Cookie Name: shareToken
    Cookie Domain: pre-stage.cc (這個要看 domain, common doamin name)
    JWT Secret: secret
    ```
    7. Setup 
    ```
    Access-Control-Allow-Origin Regex: .+
    Access-Control-Allow-Credentials: true
    ```
6. Install Frontend
    1. git clone frontend
    2. yarn install
    3. setup config.js
    4. yarn build
7. Install Web service
    1. Install nginx
    2. Apply 3 domain SSL (proposal, frontend, discuss)
    3. setup .conf from 3 application
    
