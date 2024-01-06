---
title: 違章工廠舉報系統第 9 次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第 9 次小聚

時間：20191016
地點：地球公民基金會北辦
線上：N/A

## 參與者簽到

- yukai
- 柏憲
- simon
- pm5

## 待討論


## 會議記錄

- GitHub Org 有 Logo 啦！今日 KPI 達成（逃
    - ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bc972a636ed3a5e0def1b7a9fd37df71)


## 雜記區

TODO: 整理到 repo 的 `docs/` 裡面

Install on GCP ubuntu free tier

```bash
sudo apt-get update


# Install docker
# 
# https://docs.docker.com/v17.09/engine/installation/linux/docker-ce/ubuntu/
# 參考最新的 docker 安裝方式
sudo apt-get install docker-ce
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose # https://docs.docker.com/compose/install/
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

sudo service docker start

# Docker installation end

#　https://oranwind.org/-solution-qi-dong-docker-compose-fa-sheng-error-couldnt-connect-to-docker-daemon-at-httpdockerlocalunixsocket-is-it-running-cuo-wu/

# if sudo service docker start failed
sudo gpasswd -a ${USER} docker
# 登出登入使用者
sudo su
su your_user_name


cd ~/
mkdir Projects
cd Projects

# clone projects
git clone https://github.com/Disfactory/Disfactory
cd Disfactory/backend
docker-compose up -d


vi gis_project/settings.py #'34.80.197.40'
```

Virtualbox

激推 LMDE (Linux Mint Debian Edition)！
