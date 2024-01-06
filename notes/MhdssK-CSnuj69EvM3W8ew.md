---
name: 安裝 git 及設定 github 帳戶授權
tags: 教學, Ubuntu, git, Github
image: https://github.com/fluidicon.png
description: 如何在 Linux 類作業系統安裝 git，並綁定 github 帳號。
---

# 如何設定在本機設定 github 帳戶

## 開啟 Terminal

- 首先，開啟並登入你的 Ubunut 虛擬機。
- 點選左側工具列第一個工具 Search your computer，在搜尋列輸入 terminal，點選使用 Terminal（終端機）工具。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5376c38ebf39963699b7b61ccd0cbc8c)

- 打開後就會看到一個黑板，這是一個非常強大的工具，透過輸入文字跟電腦互動、給電腦指令，接下來我們會用 Terminal 做很多事情，每個使用的指令都會盡量說明清楚。

## 安裝 git

- 接下來我們要安裝 git 這個軟體，運用 git 來跟網站 Github 互動。
:::info

📚 **補充說明**
- **git** - 一個程式版本控管的軟體。
- **Github** - 一個網路服務平台，讓大家把自己的程式碼託管在這個平台上，並利用 git 軟體來控管版本，其名稱的字尾 hub 是樞紐、中心的意思。

:::

- 首先我們要得到最新的軟體資訊清單，這樣才能載到最新的 git，在 Terminal 裡頭輸入：
```shell=
sudo apt-get update
```

- 輸入指令按下 Enter↵ 後，電腦就會一邊更新清單，一邊說明更新的進度，結束後才能繼續輸入下一個指令。

:::info
📝**指令說明**
- **sudo** - 一種說法該指令是 super user do 的縮寫，寫在 sudo 後面的指令，代表我想要用更高的權限執行指令，有點像是在 Windows 系統中，「以系統管理員身分執行」的動作，通常下 sudo 指令後會需要輸入你的電腦密碼。
- **apt-get update** - apt-get 是 ubuntu 預設的軟體包管理器，意思就是說在這台電腦上，你要處理軟體的更新、下載都需要下 apt-get 的指令，後面的 update，就是我們要求 apt-get 這個軟體做的事情，去更新最新的軟體清單。
- 下指令時（apt-get），一般而言都會伴隨著參數（update），最常見的參數就是去查詢軟體的版本，輸入以下的指令後電腦就會回覆你 apt-get 的版本。
```shell=
apt-get -v
```
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_694ca888e3f1cb2009103f545e8a6d1e)
:::

- 得到最新的軟體清單後，輸入安裝 git 的指令，其中 apt-get 是指令（command），後面兩個是參數（arguments）
```shell=
sudo apt-get install git
```
- 安裝時電腦會再次跟你確認是否要安裝，輸入 Y 後繼續。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_db365988c9b6f3aba6534dc3cf8dd130)

- 通常會透過確認版本來檢查軟體是否安裝好了，輸入指令後如果有回覆版本號碼，代表你已安裝完成。

```shell=
git --version
```

- :tada: 恭喜您，你安裝好了 git 。 

## 用 git 與 Github 互動

用 git 去取得 Github 上面的程式時，只要是重要的操作（例如刪除、修改程式），都會需要輸入帳號密碼，接下來我們透過一個簡單的任務來練習、熟悉操作的過程。

:::info
❕ 任務
在 Github 建立一個程式庫（repository），再透過本機的 git 幫程式庫新增一個檔案。
:::

1. 在 Github 網站，點選頭像 → Your repositories → New → 輸入 repo 名稱 → 按下 create
2. 接下來我們要把這個 repo 複製一份到本機，點選 HTTPS → 複製 repo 網址

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_91348659bc3e674654c1e8d6824f28d2)


3. 回到 Terminal 依序輸入指令：

複製 repo
```shell=
git clone 複製的網址
```

4. 現在我們在 repo 資料夾裡建一個檔案，並試著將這個檔案送上 Github，除了用 Terminal 之外，也可以善用 Ubuntu 提供的 GUI（圖形化使用者介面）來新增一個檔案，點開工具列的第二個程式 Files，進入 repo 資料夾，右鍵新增一個檔案，操作方式就跟你習慣的作業系統差不了多少，你複製的 repo 資料夾會在 Home 裡頭。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_58872fadf1f6ec255dfe3633632a8562)

5. 現在檔案也創好了，剩下就是把檔案送上 Github，在這之前我們需要在 git 裡頭設定認證功能，回到 Terminal 輸入以下指令（# 開頭的為註解，不用輸入）：

```shell=
git config --global credential.helper cache
# 啟用認證幫手。

git config --global credential.helper 'cache --timeout=3600'
# 設定密碼的暫存時間，這樣一來不用一直輸入密碼，以這指令為例為暫存3600秒，即1小時。
```

6. 終於要送出檔案了，依序步驟為：進入專案資料夾、加入檔案（add）、提交變更（commit）、推送出去（push）

:::warning
🔔 提醒 
git 會看你人在哪個專案資料夾裡來判斷你要處理的是哪一個 repo，所以每個 repo 都會有各自的資料夾，你要用 git 處理哪個專案，第一件事就是要先進去那個專案資料夾。
:::

```shell=
cd repo名稱
# 進入 repo，cd（change directory）這個指令就是進入要去資料夾的意思

git add filename
# 將你想要提交的單一檔案加入清單。

git add --all
# 或者你也可以把repo所有的檔案都加入，到時 git 會很聰明得只幫你推送有變更的檔案。

git commit -m "提交變更時附加的訊息"
# 提交變更，通常提交時也會順便說明一下你做了哪些事情。

git push
# 正式推送到 Github 上，由於這個步驟會改寫 repo，
# 所以這一步就會需要輸入帳號密碼，請依照電腦回覆的提示輸入，
# 推送結果是成功或失敗都會跟你回報。
```

7. 回到 Github 網站查看你的 repo ， 確認新增的檔案送了上去。

:::success
:tada::tada: 恭喜你，任務完成，泡杯咖啡、吃個小點心獎勵自己吧！
:::
