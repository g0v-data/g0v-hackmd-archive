---
tags: disinfo
---

Build selenium / chromedrive server
=====

需求 from pm5：
要讓爬蟲透過 remote 到 chromedriver 進行爬蟲，需要兼顧安全性

相關的middleware:
https://github.com/disinfoRG/ZeroScraper/blob/master/newsSpiders/middlewares.py#L67

Remote 到 chromedriver 本身不難，官方有相關的遠端連線教學 https://chromedriver.chromium.org/getting-started

重點應該是安全性，幾個做法
1. 掛一個 squid 正向代理 + passwd 在前面，目前我在 middleware 有看到 PROXY 的連線方式，可行性蠻高的
2. VPN ?
3. 

----

我會用第一種方法先建立 


還沒寫完待補QQ

> 看起來不錯⋯⋯ [name=pm5]
> 我們的 middleware 用 proxy 的地方是 chromedriver <-> web site 這一段。這裡我們需要的是 selenium <-> remote webdriver server 這一段的安全性，避免 remote webdriver server 被人拿去用，所以不太一樣。
> 
> 我們這一段如果要用 proxy 接 + basic authentication，大概要 patch 一下 selenium.webdriver.remote.remote_connection [這附近](https://github.com/SeleniumHQ/selenium/blob/master/py/selenium/webdriver/remote/remote_connection.py#L95)的程式。
> 
> 比較麻煩的可能是 HTTPS，不太確定 webdriver client 端支援有沒有什麼問題（雖然看起來可以）。有 HTTPS 的話，那 API security 通常的作法會用 token 也是要 patch remote_connection，所以這方面差不多。
> 
> 另外用 tunneling/VPN 的方法好像有人[遇到過問題](https://github.com/SeleniumHQ/selenium/issues/5859#issuecomment-406367132)。其他人嘗試 HTTPS 的[經驗](https://github.com/SeleniumHQ/selenium/issues/5073#issuecomment-348750241)也可以參考看看。
> 
> 總之掛一個 proxy 的方式我覺得可以繼續嘗試看看⋯⋯真的很卡關的話那就鎖 IP 吧 XD
> [name=pm5]


----

更新一下環境套件

```
sudo apt-get update -y
sudo apt-get upgrade -y
```

安裝 docker

```
#移除舊 docker
sudo apt-get remove docker docker-engine docker.io 

#安裝 docker
sudo apt install docker.io

#啟動且開機自動啟動
sudo systemctl start docker
sudo systemctl enable docker

```

安裝 chrome

```
wget -c https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb


sudo dpkg -i google-chrome-stable_current_amd64.deb

# 如果安裝有錯誤的話
sudo apt-get install -f


```


開一個專案資料夾放 chromedriver

```
mdkir /usr/share/node/chromedriver
cd /usr/share/node/chromedriver

npm install chromedriver

# 需要安裝 libnss3
apt-get install libnss3

# 測試
npx chromedriver

Starting ChromeDriver 83.0.4103.39 (ccbf011cb2d2b19b506d844400483861342c20cd-refs/branch-heads/4103@{#416}) on port 9515
Only local connections are allowed.
Please see https://chromedriver.chromium.org/security-considerations for suggestions on keeping ChromeDriver safe.
ChromeDriver was started successfully.


# 需要讓他背景執行，用 pm2 管理

```



