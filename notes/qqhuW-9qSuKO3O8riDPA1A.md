# 問題與解法
1. 問題描述:2025/01/07使用許先生的chatweb打包失敗跳出錯誤訊息
```bash=
Unable to find image 'chatweb:latest' locally
docker: Error response from daemon: pull access denied for chatweb, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.
```
並且執行 `docker load < chatweb.tar` 正常，執行 `docker images` 也有該映像存在。
* 解法:經測試看起來像是tag夾帶未知字符導致再linux環境無法辨識，重新tag即可。先執行 `docker load < chatweb.tar`然後再執行`docker images` 取得IMAGE_ID ,最後重新tag `docker tag IMAGE_ID chatweb:latest`,接著執行docker run的相關指令即可。
