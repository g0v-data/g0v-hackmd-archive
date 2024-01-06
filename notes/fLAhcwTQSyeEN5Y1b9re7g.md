---
title: "moedict-amis line bot"
tags: 萌典,amis,hackpad
---

# moedict-amis line bot

> [點此觀看原始內容](https://g0v.hackpad.tw/znE1Jj0g3Rw)

隨手紀錄一下在新的 DigtalOcean Droplet 上安裝阿美語萌典 line bot 。

Line Bot 的 callback URL 需要 https (不確定會不會驗證簽章，假設會好了...)
所以要安裝 Let's Encrypt

```
apt-get update
apt-get dist-upgrade
cd /opt
apt-get install git python-pip build-essential python-dev libffi-dev libssl-dev
pip install pyopenssl ndg-httpsclient pyasn1
pip install urllib3 --upgrade
git clone https://github.com/letsencrypt/letsencrypt /opt/letsencrypt
./letsencrypt-auto --standalone -d amis.noip.me

```
改一下 default locale
```
locale-gen zh_TW.UTF-8
vim /etc/default/locale


