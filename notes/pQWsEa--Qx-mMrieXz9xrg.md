# 零營運費用開源開發

:::info
如何使用 Github(pages+actions) 搭建一個零營運費用的政府資料爬蟲網站。
:::

## 前言

過去做一個政府資料爬蟲網站，需要架設一個伺服器，爬網站資料後上傳到網路空間。後來有了無伺服器(serverless)後，可使用Cron+Lambda(AWS)爬資料後傳到S3。儘管許多g0v方案會使用Github作為資料的空間以節省費用，但不管哪種方式都需要一些基本費用(包含伺服器運算與數據傳輸等)。
    
筆者將以近期的一個開源專案做範例，分享如何使用Github達成零營運費用的開源開發。

## 專案簡介

- [共筆：健保醫療品項費用查詢介面 跳坑首頁](https://g0v.hackmd.io/7jJGJcf-RraLLwocmCB20A)
- [Github專案源碼](https://github.com/chunyenHuang/nhi-open-data-tool)
- [專案網站](https://chunyenhuang.github.io/nhi-open-data-tool)


### 目標

使用健保署提供的公開資料(csv)，搭建一個簡易的搜尋頁面。

### 使用工具

- 爬蟲
    - NodeJS
    - Puppeteer
    - Github Actions (每日執行)
- API
    - Github Raw Data (json)
- 網頁
    - Github Pages (gh-pages)
    - ReactJS
    - IndexedDB (Local cache)
    - Github Actions (發布)

### 流程

1. 每日下午5點執行健保署爬蟲(Github Actions)
2. 抓取資料後轉換成JSON，並Commit&Push到Github
3. 用戶使用的網站向Github索取JSON資料

## 實作

### 爬蟲

基本上使用[Puppeteer](https://pptr.dev/)讀取網頁，下載對應的csv和ods檔案後，轉換成json儲存在本地資料夾。

- Puppeteer 抓資料
    https://github.com/chunyenHuang/nhi-open-data-tool/blob/master/data/getSources.js
- 下載csv並轉換成json，將大檔分成小檔(index)
    https://github.com/chunyenHuang/nhi-open-data-tool/blob/master/data/process.js
- 資料
    https://github.com/chunyenHuang/nhi-open-data-tool/tree/master/data/latest
    ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bf636f1a7688f4940e4b89c41766310c.png)
    

### Github Actions

本篇的重點，將分成兩部分，每日執行爬蟲與網站發布。

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a3378149e7bdb64fb9c8b0039a48e78.png)


#### 每日執行爬蟲

https://github.com/chunyenHuang/nhi-open-data-tool/blob/master/.github/workflows/data-process.yml

```yaml
name: Daily Data Process

on: # 何時執行
  schedule:
    - cron: "0 9 * * *" # 當台北下午5點下班時間
  push:
   branches: [ master ] # 當master更新的時候

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
      with:
        persist-credentials: false
        fetch-depth: 0
    - name: Install Dependencies
      uses: actions/setup-node@v1
      env:
        PUPPETEER_SKIP_CHROMIUM_DOWNLOAD: 'true'
      with:
        args: install
    - run: npm ci
    - name: Create local changes
      timeout-minutes: 15 # 延長執行時間
      uses: mujo-code/puppeteer-headful@master
      env:
        CI: 'true'
      with:
        args: npm run process # 執行爬蟲
    - name: Commit files
      timeout-minutes: 15
      run: | # Commit&Push回到Github Repo
        git config --local user.email "action@github.com"
        git config --local user.name "GitHub Action"
        git commit -m "更新健保署資料" -a
    - name: Push changes
      uses: ad-m/github-push-action@master
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }} # 以內建，無需額外設定

```

#### 網站發布

https://github.com/chunyenHuang/nhi-open-data-tool/blob/master/.github/workflows/publish.yml

```yaml
name: Publish Webpage

on: # 何時執行
  push:
    branches: [ master ] # 當master更新時

jobs:
  publish:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [12.x] # 設定環境

    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v1
      with:
        node-version: ${{ matrix.node-version }}
    - name: Install Dependencies
      run: npm ci
      working-directory: web
    - name: Build
      run: npm run build
      working-directory: web
    - name: Deploy GitHub Page
      uses: peaceiris/actions-gh-pages@v3.5.7
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./web/build
```

### Github Pages

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6703f0c1097f71604b2c0ec218f4eb7c.png)

- [gh-pages](https://www.npmjs.com/package/gh-pages)
