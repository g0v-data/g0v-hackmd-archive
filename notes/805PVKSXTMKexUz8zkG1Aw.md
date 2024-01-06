---
name: 在本機設定好 jothon 的開發環境
tags: 教學, jothon-net, Github
image: https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_88806705f8936490e7b80a46f84aba2b

description: 設定 jothon 的開發環境，開啟本機伺服器預覽 jothon 網。
---

# 在本機設定好 jothon 的開發環境

## 安裝 nodejs
- jothon 網是透過 nodejs 運作的，所以我們需要先安裝好它。
- 根據 nodejs 官方的說明，我們需要在 Terminal 依序輸入下列指令完成安裝：
```shell=
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
# 第一個指令是將安裝資訊從網路上抓下來的意思。
# 網址最後有寫 12.x ，代表我們要安裝這個版本。

sudo apt-get install curl
# 如果執行後電腦跟你說它沒有 curl 這個程式，請輸入這段指令（反之則跳過）。

sudo apt-get install -y nodejs
# 安裝 nodejs
```
- 如果你想安裝其他版本的 nodejs，可以到下列網址去找，頁面也有告訴你輸入的指令。https://github.com/nodesource/distributions/blob/master/README.md

## fork jothon-net

- 接下來我們要從正式的程式庫複製一份給自己使用。
- 到 https://github.com/g0v/jothon-net 頁面點選右上角的 fork 即可複製。
- 你複製好的 repo 會在 `https://github.com/(你的帳號ID)/jothon-net`。
- 請放心在自己的 repo 上測試或操作，並不會影響原本被 fork 的 repo。

## clone jothon-net 到本機

- 在自己的 repo 頁面點選 `Clone and download`，會浮出對話框。
- 在對話框內，選擇 `Clone with HTTPS`，如果有設定 SSH key 請選擇 `Clone with SSH`。
- 選擇好後複製對話框提供給你的連結。
- 開啟 Terminal 後輸入 `git clone 連結`，即可複製一份 repo 到本機。
- 複製好後就可以看到在你的家目錄下有一個專門存放這個專案的資料夾 `jothon-net`，在 Terminal 或透過檔案管理程式都可以看得到。
```shell=
ls 
# 是 list 的縮寫，意思是請電腦告訴我現在有哪些檔案跟資料夾。

cd jothon-net
# 進入 jothon-net 資料夾，輸入資料夾名稱到一半時按 Tab 鍵，電腦會幫你 auto-complete
```

## 安裝 jothon-net 使用的程式
- 一般來說每個專案都會使用到其他開源專案所提供的程式， jothon-net 這個專案也不例外。
- 這些資訊會寫在 `package-full.json`、`package-lock.json`、`package.json`，說明一個專案用到那些其他人提供的 package。
- 確認已經在 `jothon-net` 的資料夾後，輸入：
```shell=
npm ci
# npm 全名 nodejs package manager，安裝跟 nodejs 有關的程式時都會用到它。
# ci 全名 clean install。
```
- 輸入安裝指令後會花一段不長也不久的時間安裝完成，安裝好後電腦會回覆一些警告資訊，請不用太擔心，通常這些訊息就只是告訴你其他 package 有最新的版本而已。

## 瀏覽本機的 jothon 網
- 到這邊為止我們的開發環境都準備好了，下一個章節會針對 jothon 網討論，教你如何要新增一個 jothon 成員、如何新增下一次大松資訊，這些基本的網站維護都會了之後，相信你之後也能舉一反三，自己一個人修改網站上的資訊。
- 以上講的這些維護，當然都會希望說在正式放在網路上前，自己先看過一遍網站的呈現是不是跟自己想的一樣，所以先在本機自己確認過一遍，是很常見的操作。
- 在 `jothon-net` 資料夾裡輸入指令 `npm start`，即可在自己的電腦上建立網頁伺服器，再打開左側工具列的 firefox ，在網址上輸入 `localhost:3000` 就可以看到本機的 jothon 網了。

![](https://i.imgur.com/CYbtCQh.png)

- 同時你會發現沒辦法在 Terminal 上輸入下一個指令，這是因為網頁伺服器就一直維持開啟的狀態的關係，如果要輸入其他指令，必須先關掉網頁伺服器，按下`Ctrl`+`c`即可結束伺服器。