---
title: 違章工廠舉報系統第 10 次小聚
tags: Disfactory, 違章工廠, 違章工廠舉報系統
---

# 違章工廠舉報系統第 10 次小聚

時間：20191023
地點：地球公民基金會北辦
線上：N/A

## 參與者簽到

- simon
- yukai
- Aaron (鉦寰)
- 小海
- Sandra
- Hubert
- 星翰
- yellowsoar
- pm5
- Andy
- IU


## 待討論


## 會議記錄

Sandra 設計增加新頁面：【安全須知】（內文於雜記區）
https://scene.zeplin.io/project/5d9decce4115306bdddd04a3

## 雜記區

【安全須知】請參考以下建議，前往違章工廠拍照蒐證
場勘：假裝路過，檢查有無監視器；尋找適合拍照的隱蔽處
藏身：盡量避開監視器、他人視線；盡量在隱蔽處拍照（例如：車上、民宅內、樹叢間、遠方）
避嫌：假如地點不夠隱密，請用手機拍照，降低他人戒心
速離：拍到1張清晰照片即可離去
應變： 假如有人上前問話，請表現得「充滿好奇心」，試著跟對方聊天（例如：好奇水電師傅的施工技術），再伺機離開。


開發測試環境設置教學：

```bash
git clone http://github.com/Disfactory/Disfactory
sudo service docker restart
docker-compose up -d #可測試 8000 port
```

建首筆測試資料庫：

```bash
docker ps # 查看docker pid
docker exec -it pid /bin/bash # 進docker container

python3 manage.py makemigrations;migrate;shell
```

```python
api.models.Factory(lat=23,lng=120,point=django.contrib.gis.geos.Point(1,1),status_time='2019-10-23').save()
下次開始測試各 views function.
```

VSCode remote ssh

Docker 環境設置:

WSL + Docker = 先不要
docker-compose 解 wsl 的路徑會出問題，volumn 怎試都掛不上去

Windows 直接在原本的 shell 操作 Docker for Windows 就好
