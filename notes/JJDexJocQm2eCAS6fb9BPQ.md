# Skridea Backend

## 運作環境

* PHP v7.2.18+
* MySQL 5.7.24
* Laravel 5.8.x
* 資料庫編碼
  * `charset: utf8mb4`
  * `collation: utf8mb4_unicode_ci`
* Vue.js 2.6.10+

## 預備事項

* 建置後台資料庫（utf8mb4_unicode_ci），需對應專案ENV設定中的 **DB_DATABASE**

* DNS設定
  * 本地端 e.g. sudo vi /etc/hosts
  * 測試機請於 [CLOUDFLARE](https://dash.cloudflare.com/3d653215b48a261000fae89060eb636c/skridea.com/dns) 中設定

* LINE官方頁面設定
  * callback URL：decode server url、前台網址(LIFF)
  * Login Channel中Linked OA
  * LIFF
  * Message Channel中Webhook (e.g. 測試機為 webhook-dev.skridea.com/{Message Channel Id} )

## 環境 domain 說明

專案之後台將 subdomain 設定為 Company Key

e.g. 

- https://coolbe.skridea.ngrok.io
- https://coach.skridea.ngrok.io
- https://develop.skridea.ngrok.io

故開發時架設使用 https://develop.skridea.ngrok.io 作為開發測試站

## Nginx Header 設定

跨網域問題需在 nginx conf 加上下列 code

```
add_header 'Access-Control-Allow-Origin' '*' always;
add_header 'Access-Control-Allow-Methods' 'GET,POST,PUT,DELETE,PATCH';
add_header 'Access-Control-Allow-Headers' 'Authorization, Content-Type, Channel';
```

需開放 PUT、DELETE、PATCH

**且需在 Allow-Hedaers 加上 Channel、Uuid**

## 安裝步驟

## 後端

1. cd 專案目錄底下 && `cp .env.example .env` 並修改 `.env` 之環境變數 (DB 設定等)

2. `composer install` 安裝相依套件

3. `composer demo` 初始化專案

## 前端

4. cd /views `cp .env.example .env.development` && `cp .env.production` 並修改 `.env.development` &&`.env.production` 之環境變數 (DB 設定等)
   * VUE_APP_USE_GOOGLE_API_RECAPTCHA 於開發環境，可設定false

5. 安裝相依套件 `yarn install`

6. 開發時於 `views` 下執行 `yarn serve`、正式環境執行 `yarn build`

## 使用套件

### 前端 Vue.js

[pretty-checkbox-vue](https://github.com/hamed-ehtesham/pretty-checkbox-vue) Checkbox

[vue-snotify](https://github.com/artemsky/vue-snotify) 右下方通知訊息

[v-calendar](https://github.com/nathanreyes/v-calendar) 日期選擇器(無時間)

[vue-ctk-date-time-picker](https://github.com/chronotruck/vue-ctk-date-time-picker) 日期選擇器(有時間)

[vue-multiselect](https://github.com/shentao/vue-multiselect) Select (可多選、tag)

[vee-validate](https://github.com/baianat/vee-validate) 表單驗證器

[vue-quill-editor](https://github.com/surmon-china/vue-quill-editor) 文章編輯器

[vue-scrollto](https://github.com/rigor789/vue-scrollto) scroll 至指定位置

[vuedraggable](https://github.com/SortableJS/Vue.Draggable) 支援使物件可拖移

[vue-js-modal](https://github.com/euvl/vue-js-modal) Vue Modal

[vue-upload-component](https://github.com/lian-yue/vue-upload-component) Vue 檔案上傳

[vue-filepond](https://github.com/pqina/vue-filepond) 檔案上傳 (圖片、影片、聲音...)

-> 相關輔助套件 

1. [filepond-plugin-image-vlidate-size](https://github.com/pqina/filepond-plugin-image-validate-size) 驗證圖片大小

2. [filepond-plugin-file-validate-size](https://github.com/pqina/filepond-plugin-file-validate-size) 驗證檔案大小

3. [filepond-plugin-file-validate-type](https://github.com/pqina/filepond-plugin-file-validate-type) 驗證檔案類型

4. [filepond-plugin-image-preview](https://github.com/pqina/filepond-plugin-image-preview) 圖片預覽

5. [filepond-plugin-media-preview](https://github.com/nielsboogaard/filepond-plugin-media-preview) 影片預覽 (第三方套件)

6. [filepond-plugin-file-encode](https://github.com/pqina/filepond-plugin-file-encode) 抓取 DataBase64

7. [filepond-plugin-file-poster](https://github.com/pqina/filepond-plugin-file-poster) 網址圖片預覽

8. [FilePondPluginFileValidateType](https://pqina.nl/filepond/) 驗證檔案類型

9. [FilePondPluginImageExifOrientation](https://pqina.nl/filepond/) 圖片控制器

10. [FilePondPluginImageCrop](https://pqina.nl/filepond/) 剪裁照片

11. [FilePondPluginImageResize](https://pqina.nl/filepond/) 變換大小

12. [FilePondPluginImageTransform](https://pqina.nl/filepond/) 照片變形

13. [FilePondPluginImageEdit](https://pqina.nl/filepond/) 編輯照片

[vue-clipboard2](https://github.com/Inndy/vue-clipboard2) 複製、剪下套件

[v-tooltip](https://github.com/Akryum/v-tooltip) Vue Tooltip

[vue-chart](https://github.com/apertureless/vue-chartjs) Vue 圖表

[vue-color](https://github.com/xiaokaike/vue-color) 顏色選擇器

[V-Emoji-Picker](https://github.com/joaoeudes7/V-Emoji-Picker#readme) 顏文字

[vue-infinite-scroll](https://github.com/ElemeFE/vue-infinite-scroll) scrollBar套件 (置底觸發 Function) - 目前這個沒有用到

[vue-easy-lightbox](https://github.com/XiongAmao/vue-easy-lightbox) LightBox (幻燈片 點擊圖片會顯示 Modal 彈窗)

[vue-infinite-loading](https://peachscript.github.io/vue-infinite-loading/zh/guide/) scrollBar套件 (目前都用這個, 上拉下拉都可以觸發）

[vue-lazy-load](https://github.com/hilongjw/vue-lazyload) 圖片懶加載

[js-xlsx/sheetjs](https://github.com/SheetJS/sheetjs) Excel 前端上傳預覽 下載 套件(目前停用)

[d3.js](https://github.com/d3/d3) 圖形化工具, 可轉 csv 為 JSON 或 TEXT

## 環境設定

### supervisord

先手動建立 log 資料夾，並確定權限沒問題

`mkdir /var/www/backend/storage/logs/queue`

`chown -R nginx:nginx /var/www/backend/storage/logs/queue`

  1. 需監聽 `php artisan queue:work --daemon --queue=default` 來執行一般 Job

```
[program:backend-default-queue]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/bin/php /var/www/backend/artisan queue:work --daemon --queue=default
numprocs=1
numprocs_start=0
autostart=true
autorestart=true
user=nginx
startsecs=1
startretries=3
exitcodes=0,2
stopsignal=TERM
stopwaitsecs=10
redirect_stderr=false
serverurl=AUTO
```

  2. 需監聽 `php artisan redis:webhook-monitor` 來監聽 webhook redis

```
[program:backend-redis-monitor]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/bin/php /var/www/backend/artisan redis:webhook-monitor
autostart=true
autorestart=true
user=nginx
numprocs=1
```

  3. 需監聽 `php artisan queue:work --daemon --queue=line-event` 來執行 LINE EVENT JOB

```
[program:backend-line-event-queue]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/bin/php /var/www/backend/artisan queue:work --daemon --queue=line-event
numprocs=1
numprocs_start=0
autostart=true
autorestart=true
user=nginx
startsecs=1
startretries=3
exitcodes=0,2
stopsignal=TERM
stopwaitsecs=10
serverurl=AUTO
```

  4. 需監聽 `php artisan queue:work --daemon --queue=line-richmenu` 來執行 LINE RICHMENU JOB

```
[program:backend-line-richmenu-queue]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/bin/php /var/www/backend/artisan queue:work --daemon --queue=line-richmenu
numprocs=1
numprocs_start=0
autostart=true
autorestart=true
user=nginx
startsecs=1
startretries=3
exitcodes=0,2
stopsignal=TERM
stopwaitsecs=10
redirect_stderr=false
serverurl=AUTO

```

  5. 需監聽 `php artisan queue:work --daemon --queue=line-message` 來執行 LINE MESSAGE JOB(聊天室)

```
[program:backend-line-message-queue]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/bin/php /var/www/backend/artisan queue:work --daemon --queue=line-message
numprocs=1
numprocs_start=0
autostart=true
autorestart=true
user=nginx
startsecs=1
startretries=3
exitcodes=0,2
stopsignal=TERM
stopwaitsecs=10
serverurl=AUTO
```

  6. 需監聽 `php artisan queue:work --daemon --queue=line-multicast` 來執行 LINE MULTICAST JOB

```
[program:backend-line-multicast-queue]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/bin/php /var/www/backend/artisan queue:work --daemon --queue=line-multicast
numprocs=5
numprocs_start=0
autostart=true
autorestart=true
user=nginx
startsecs=1
startretries=3
exitcodes=0,2
stopsignal=TERM
stopwaitsecs=10
redirect_stderr=false
serverurl=AUTO

```

  7. 需監聽 `laravel-echo-server start` 來執行 Laravel ECHO SERVER 監聽聊天室訊息

```
[program:laravel-echo-server]
process_name=%(program_name)s_%(process_num)02d
directory=/var/www/backend
command=/usr/local/bin/laravel-echo-server start --dir=/var/www/backend
autostart=true
autorestart=true
user=root
```

以上皆設定完成後，需執行 `systemctl restart supervisord` 重啟服務。

## Laravel Echo Server

1. 全域安裝 laravel-echo-server

`yarn global add laravel-echo-server`

2. 執行 `laravel-echo-server start`

## 新增 Flex Message

`app/Services/LINE/FlexResolve` 中新增 Class 判斷

`app/Services/LINE/FlexMessage` 中新增 Class 並實作 Interface

