# Day 12 - 選擇比努力更重要(一)

## 前端？後端？都要驗啦！
今天要開始做驗證，先從前端做起
其實本來可以用 `Stimulus`，但呼應本次標題，其實有些驗證很簡單，如果套用 `Stimulus` 則稍嫌麻煩，會要寫 Controller / Target / Function 等等

但如果選對工具的話，其實可以很輕鬆！
也就是說又要來用新套件幫忙啦！

## 繼續安裝繼續爽
[文件](https://alpinejs.dev/essentials/installation)底加

但本次因為使用 `Importmap`，另外也牽扯到後續打算用 class name / nesting 切換驗證狀態

所以！
必須從頭開始，改用 `PostCSS` 來重新安裝 `TailwindCSS` 跟本次的 `AlpineJS`

首先處理 `PostCSS` 環境

```bash
./bin/bundle add cssbundling-rails
./bin/rails css:install:postcss
```

接著移除 Gem `tailwindcss-rails`，還有一些跟這個 gem 有關的指令
並按官方文件從 PostCSS 的方式安裝 TailwindCSS

```bash
npm install -D tailwindcss postcss autoprefixer
```

此時基本上 config 都會幫你套好

接著開始處理 `AlpineJS`

```bash
./bin/importmap pin alpinejs@3.13.0
```

```
# app/javascript/application.js
...
import Alpine from 'alpinejs'

Alpine.start()
```

這樣就可以開始套上 Apline 做一些簡單的驗證了

今天基本上只有這樣，其實主因還是很多相關的設定要做微調，中間不斷嘗試，但還是成功了（？

總之，真正套上去做驗證要明天才能開始

