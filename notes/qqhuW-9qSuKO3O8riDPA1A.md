# 問題與解法
1. 問題描述:2025/01/07使用許先生的chatweb打包失敗跳出錯誤訊息
```bash=
Unable to find image 'chatweb:latest' locally
docker: Error response from daemon: pull access denied for chatweb, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.
```
並且執行 `docker load < chatweb.tar` 正常，執行 `docker images` 也有該映像存在。
* 解法:經測試看起來像是tag夾帶未知字符導致再linux環境無法辨識，重新tag即可。先執行 `docker load < chatweb.tar`然後再執行`docker images` 取得IMAGE_ID ,最後重新tag `docker tag IMAGE_ID chatweb:latest`,接著執行docker run的相關指令即可。

2.問題描述:2025/01/10使用許先生的puhui.tar從.net 7 升級成 .net 8 出現健康度問題 回傳500還503有點忘了。對外的口是在docker run時決定的所以GCP端口與防火牆應該沒事。docker logs 查看事有正常啟動。
* 解法：查看https://learn.microsoft.com/zh-tw/aspnet/core/migration/70-80?view=aspnetcore-9.0&tabs=visual-studio .net 7 升級成 .net 8的技術文件 發現若使用默認阜號升級後將從80改為8080，使用docker logs確認確實啟動的阜號為8080，修改.sh中的docker run內部端口即正常啟動，當日下午開會與許先生敲定puhui.tar專案綁定阜號80，之後部署使用原來的.sh檔即可。
(https://learn.microsoft.com/zh-tw/dotnet/core/compatibility/containers/8.0/aspnet-port)