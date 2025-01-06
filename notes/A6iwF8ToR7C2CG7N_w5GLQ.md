# Collect your documents with a book

View the book with "<i class="fa fa-book fa-fw"></i> Book Mode".

https://fontawesome.com/v4/icon/thermometer-quarter


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
