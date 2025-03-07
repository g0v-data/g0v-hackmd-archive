# 碩昱 Collect your documents with a book

View the book with "<i class="fa fa-book fa-fw"></i> Book Mode".

https://fontawesome.com/v4/icon/thermometer-quarter

MsSql 部屬
---
*參考網頁:
https://learn.microsoft.com/zh-tw/sql/linux/quickstart-install-connect-docker?view=sql-server-ver16&tabs=cli&pivots=cs1-bash*

* 從 Microsoft Container Registry 提取 SQL Server 2022 (16.x) Linux 容器映像。(應該是要抓，我有抓不過moboxterm沒找到，後來docker run系統自動下載)
`docker pull mcr.microsoft.com/mssql/server:2022-latest`

* 建立容器(這種寫法有一定的順序性 隨意調整可能無法執行)
```
docker run -e "ACCEPT_EULA=Y" \
   -e "MSSQL_SA_PASSWORD=RrB)syvZA8]tyDb5=1jZ" \
   -p 1433:1433 \
   -v $MSSQL_HOME:/var/opt/mssql/data \
   --name mssql2022 \
   --ip 172.20.0.5  \
   --network puhui-test \
   --restart always \
   --user root \
   -d mcr.microsoft.com/mssql/server:2022-latest
```
*  ### 針對sqlcmd 信任問題(憑證)  在後面加上-C即可以受信任身分使用
`docker exec -it mssql2022 /opt/mssql-tools18/bin/sqlcmd -S localhost -U SA -P "RrB)syvZA8]tyDb5=1jZ" -C`

* 新增mssql-tools18至路徑
```
touch ~/.bashrc
echo 'export PATH=$PATH:/opt/mssql-tools18/bin' >> ~/.bashrc
source ~/.bashrc
```

## 使用碩昱提供的sql建立初始DB:
*  `cd "/home/puhui/tingShen/"`
*  上傳.sql 並使用docker 傳到容器內
`docker cp INIT_ITRI_PUHUI.sql mssql2022:/tmp/INIT_ITRI_PUHUI.sql`

* 進入MSSQL容器內 執行SQL(上面有新增路徑可直接使用sqlcmd，根據不同的.sql內容，有些前面加上USE ITRI_PUHUI   GO  選擇DB)
`sqlcmd -S localhost -U SA -P "RrB)syvZA8]tyDb5=1jZ" -i /tmp/INIT_ITRI_PUHUI.sql -C`

.net網頁部署流程
---
1. 先使用 git clone或 git pull 下載
2. 載好進入 04.SourceCode 資料夾並執行</br> `tar -cvf folder.tar .\ITRI_PUHUI` </br> 將 ITRI_PUHUI 資料夾打包成 folder.tar
3. 上到mobaxterm，如果有ITRI_PUHUI資料夾，</br> 先執行`rm -rf ITRI_PUHUI/` 移除，</br> 在執行`tar -xvf folder.tar` 解壓縮
4. 在mobaxterm上進入ITRI_PUHUI資料夾，上傳寫好的</br>deploy_ITRI_PUHUI.sh檔，再進入ITRI_PUHUI.Web更</br>換裡面的appsetting.jason檔
5. 回到ITRI_PUHUI資料夾，執行`source deploy_ITRI_PUHUI.sh`部署


















<i class="bi bi-bank2"></i>
<i class="fa fa-book" aria-hidden="true"></i>
<i class="fa fa-thermometer-quarter" aria-hidden="true"></i>
Examples
---
- [Book example](/s/book-example)
- [Slide example](/s/slide-example)
- [YAML metadata](/s/yaml-metadata)
- [Features](/s/features)

Themes
---
- [Dark theme](/theme-dark?both)
- [Vertical alignment](/theme-vertical-writing?both)

###### tags: `Templates` `Book`
