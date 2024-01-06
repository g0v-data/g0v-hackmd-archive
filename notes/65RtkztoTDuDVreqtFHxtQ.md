# Docker 說明文件

## 參考資料
* [Docker](https://www.docker.com/)
* [Docker Hub](https://hub.docker.com/search?q=&type=image)
* [基本介紹與安裝教學](https://larrylu.blog/step-by-step-dockerize-your-app-ecd8940696f4)
* [Docker-從入門到實踐(網路書籍)](https://philipzheng.gitbooks.io/docker_practice/content/)
* [Docker學習筆記](https://peihsinsu.gitbooks.io/docker-note-book/content/docker-machine.html)
* [Dockerfile參數介紹](https://www.jinnsblog.com/2018/12/docker-dockerfile-guide.html)
* [Docker Hub 介紹](https://ithelp.ithome.com.tw/articles/10191139)
* [Docker 指令操作介紹](https://blog.longwin.com.tw/2017/01/docker-learn-initial-command-cheat-sheet-2017/)
* [Docker-composer 常用指令](https://blog.csdn.net/skh2015java/article/details/80410306)
* [Docker-composer介紹](https://blog.techbridge.cc/2018/09/07/docker-compose-tutorial-intro/)
* [Docker-composer介紹](http://blog.maxkit.com.tw/2017/03/docker-compose.html)

## 主要結構說明
Docker 包括三個基本概念 :
1. 映像檔（Image）
1. 容器（Container）
1. 倉庫（Repository）

* image : 
    Docker 映像檔就是一個唯讀的模板。映像檔可以用來建立 Docker 容器。
    例如：一個映像檔可以包含一個完整的 ubuntu 作業系統環境，裡面僅安裝了 Apache 或使用者需要的其它應用程式。
    Docker 提供了一個很簡單的機制來建立映像檔或者更新現有的映像檔，使用者甚至可以直接從其他人那裡下載一個已經做好的映像檔來直接使用
    
    > [name=黃俊智] Dockerfile : 建立image所需撰寫的檔案,可在裡面增加自己的一些操作,讓image在開啟後就有相對應的環境或設定可以使用
* container : 
    Docker 利用容器來執行應用。
    容器是從映像檔建立的執行實例。
    它可以被啟動、開始、停止、刪除。
    每個容器都是相互隔離的、保證安全的平台。
    可以把容器看做是一個簡易版的 Linux 環境（包括root使用者權限、程式空間、使用者空間和網路空間等）和在其中執行的應用程式。
> [name=黃俊智] 註：映像檔是唯讀的，容器在啟動的時候建立一層可寫層作為最上層。
> 每個Container相當於獨立的vm電腦,可有多個,使用docker-compose 進行管理會較方便
* Repository : 
    倉庫是集中存放映像檔檔案的場所。有時候會把倉庫和倉庫註冊伺服器（Registry）混為一談，並不嚴格區分。實際上，倉庫註冊伺服器上往往存放著多個倉庫，每個倉庫中又包含了多個映像檔，每個映像檔有不同的標籤（tag）。
    倉庫分為公開倉庫（Public）和私有倉庫（Private）兩種形式。
    最大的公開倉庫是 Docker Hub，存放了數量龐大的映像檔供使用者下載。 大陸的公開倉庫包括 Docker Pool 等，可以提供大陸使用者更穩定快速的存取。
    當然，使用者也可以在本地網路內建立一個私有倉庫。
    當使用者建立了自己的映像檔之後就可以使用 push 命令將它上傳到公有或者私有倉庫，這樣下次在另外一台機器上使用這個映像檔時候，只需要從倉庫上 pull 下來就可以了。
    * 註：Docker 倉庫的概念跟 Git 類似，註冊伺服器可以理解為 GitHub 這樣的託管服務。

## 壹、Docker 相關說明
### 零、參考資料
* 常用指令 : run、exec、ps、rm、rmi、images

### 一、指令說明
#### 1、Docker 相關指令
1. 啟動 Docker
    * ` sudo service docker start`
2. 版本資訊
    * `docker version`
    * `docker info`
3. 登入Docker
    * `docker login`

#### 2、Image 相關指令
1. build (建立 Image 運用 Dockerfile )
    * `docker build --no-cache --force-rm -t <<image-name>> <<Dockerfile Path>>`
        * ex: `docker build -t testImage .`
    > [name=黃俊智] `-t` 設定該 Image 的 tag
    > `--no-cache` 將暫存檔案移除重新建立
    > `--force-rm` Always remove intermediate containers
    > `<<image-name>>`為這個 Image 命名
    > 該目錄需要有 Dockerfile 才可 build 出 Image
2. search (搜尋線上Image清單)
    Default 由 Docker hub內進行搜尋
    * `docker search <<image-name>>`
        * ex: `docker search ubuntu`
3. pull (抓取)
    * `docker pull <<image-name>>:<tag>>`
        * ex: `docker pull ubuntu:latest`
        * ex: `docker pull ubuntu:16.04`
4. push (推送到 Docker Hub 上)
    * `docker push <<image-name>>`
    > [name=黃俊智]於 push 前需要先進行 docker login 動作 
    > 並增加 image 的 tag`docker tag <<image-name>> <<DockerHub帳號/Image Name>>`
5. images (Local Image List)
    * `docker images`
6. rmi ( Delete Image )
    * `docker rmi -f <<image id>>`
    >[name=黃俊智] docker images 可以看到 image id
    > 參數 `-f` 為強制刪除 
    * `docker rmi $(docker images -q)`
    * `docker rmi docker images -qa`
    >[name=黃俊智] 移除所有 images
    * `docker rmi $(docker images -f "dangling=true" -q)`
    >[name=黃俊智] 移除所有沒有 tag 的 images

#### 3、 Container 相關指令
1. ps    ( Container List )
    * `docker ps -a -l -q`
    > [name=黃俊智] `-a` 執行、停止的Container皆列出來
    > `-l` 最新創建的 Container
    > `-q` 僅顯示 `CONTAINER ID`
2. start (啟用 Image 產生的 Container)
    * `docker start <<CONTAINER ID>>`
    > [name=黃俊智] `CONTAINER ID` 由 ps 內取得
3. stop  (停用 Image 產生的 Container)
    * `docker stop <<CONTAINER ID>>`
    > [name=黃俊智] `CONTAINER ID` 由 ps 內取得
4. run   (執行 Image 產生的 Container)
    * `docker run -d <<CONTAINER TAG>>` 會自動執行 docker pull + 啟動並進入背景執行
        * ex: `docker run -d laravel`
    * `docker run -it <<CONTAINER TAG>> bash` 會自動執行 docker pull，跑起來自動執行 bash 程式進入此 Container
        * ex: `docker run -it laravel bash`
    * `docker run --rm <<CONTAINER TAG>> bash` Container 執行停止(`docker stop <<CONTAINER TAG>>`)後，會自動移除
        * ex: `docker run --rm laravel bash`
    * `docker run -d -p <<HOST PORT>>:<<CONTAINER PORT>> <<CONTAINER TAG>>` 設定Container Port轉到到外部的Port上
        * ex: `docker run -d -p 80:80 laravel`
    * `docker run -d -p <<HOST PORT>>:<<CONTAINER PORT>> -e MYSQLROOTPASSWORD=1234 <<CONTAINER TAG>>` 設定密碼參數;`-e`:設定環境變數
        * ex: `docker run -d -p 80:80 -e pw=1234 laravel`
    * `docker run -d --name <<CONTAINER NAME>> -m 512m -p <<HOST PORT>>:<<CONTAINER PORT>> <<CONTAINER TAG>>` `-m`:設定最大記憶體; --name:設定 Container 名稱
        * ex: `docker run -d --name laravel_web -m 512m -p 80:80 laravel`
    * `docker run -d --name <<CONTAINER NAME>> -p <<HOST PORT>>:<<CONTAINER PORT>> -p <<HOST PORT>>:<<CONTAINER PORT>> -v <<CONTAINER 內的目錄>>:<<本地端目錄>> <<CONTAINER TAG>>` 掛載外部目錄到 Container內
        * ex: `docker run -d --name laravel_web -p 80:80 -v ~/app:/app`
    * `docker run -v <<volume_name>>:<< Container 內的目錄>>`
        * ex: `docker run -v volume_test:/db/data`
    > [name=黃俊智] `-d`:背景執行
    > `-p`:設定port
    > `-e`:設定環境變數
    > `-v`:對應目錄
    > `-m`:設定最大記憶體
    > `--name`:設定 Container 名稱
5. rm    (刪除 Container )
    * `docker rm -f <<CONTAINER ID>>`
    > [name=黃俊智] `-f` 強制刪除
    > `CONTAINER ID` 由 ps 內取得
    * `docker rm $(docker ps --filter status=exited -q)`
    > [name=黃俊智] 刪除目前所有停止的 Container
    * `docker rm $(docker ps -a -q)`
    > [name=黃俊智] 刪除所有 Container
    * `docker ps -a | awk '{print $1}' | xargs --no-run-if-empty docker rm # ps -a`
    > [name=黃俊智] 刪除全部 stop 的 Container
6. exec  (於 Container 內執行指令)
    * `docker exec -i -t <<CONTAINER ID>> <<cmd指令>>`
        * ex: `docker exec -it <<CONTAINER ID>> /bin/bash`
    * `docker exec -i -t <<CONTAINER TAG>> <<cmd指令>>`
        * ex: `docker exec -i -t <<CONTAINER TAG>> /bin/bash`
    > [name=黃俊智] `-i` Keep STDIN open even if not attached, 保持 STDIN 開啟, 即使未連接。讓 CONTAINER 的 terminal 保持打開.
    > `-t` Allocate a pseudo-TTY, 讓Docker分配一個虛擬終端（pseudo-tty）並進入到 CONTAINER 的 terminal 內。
7. inspect (查看 Container 的詳細資訊)
    * `docker inspect <<CONTAINER TAG>>`
    > [name=黃俊智] 可使用grep 取得特定資料 
    > ex(取得IP資訊): `docker inspect <<CONTAINER TAG>> | grep IPAddre`
8. port (查看 Container 的 Port)
    * `docker port <<CONTAINER ID>>`
9. top (查看 Container 目前正在執行的 process)
    * `docker top <<CONTAINER ID>>`
10. kill (砍掉目前正在跑得 Container )
    * `docker kill <<CONTAINER ID>>`
    * `docker kill $(docker ps -q)` 刪除目前所有 Container
11. volume (用於將 Container 的資料存於外部使用, Container刪除也不會被影響)
    * `docker volume create --name <<volume_name>>` 新增一個 volume, 會於本機端增加一個資料夾`<<volume_name>>`給予使用(大部分預設在 var ( /var/snap/docker/common/var-lib-docker/volumes/ )下面)
        * ex: `docker volume create --name volume_test`
    * `docker volume ls` 列出已設定的 volume
    * `docker volume rm <<volume_name>>` 刪除已設定的 volume
        * ex: `docker volume rm volume_test`
    > [name=黃俊智] 於 docker run 上設定對應關係
    > ex: `docker run -v <<volume_name>>:/data` 其中`/data`為 Container 內的資料夾路徑
    > 可利用 docker-compose 達到該目的
    > 可以在共用目錄內安裝軟體, 提供給其他 Container 直接使用
    > ex: `docker run -v ~/app:/app --workdir /app node yarn init -y`
12. log 
    * `docker log <<CONTAINER ID>>`
13. rename (重新命名 Container )
    * `docker rename <<CONTAINER ID>> <<new name>>`
14. cp (將 Container 內的資料複製到本地端上)
    * `docker cp <<CONTAINER ID>>:<< Container 內的目錄>> <<本地端目錄>>`
        * ex: `docker cp <<CONTAINER ID>>:/etc/group /tmp`

>[name=黃俊智] 未整理內容(不常使用)
Attach、commit、save、load、export、import

---
## 貳、Dockerfile 相關說明
### 零、參考資料
* [參數 ENV DEBIAN_FRONTEND說明](https://docs.docker.com/engine/faq/)
* [ARG 與 ENV 的不同](https://vsupalov.com/docker-arg-env-variable-guide/)
* [SSH_PRIVATE_KEY殘留問題](https://vsupalov.com/
-docker-image-clone-private-repo-ssh-key/)
* 可設定在gitlab上, 位於`專案->Setting->Packages->Container Registry`內
* `<<EOF EOF` : 在需要互動的cmd指令內 增加該指令去做填寫的動作(大仔提供)
### 一、Dockerfile Example Code
``` Dockerfile
FROM ubuntu:18.04

MAINTAINER mike@program.com.tw
LABEL version="1.0" description="Laravel Test" by="Mike Huang" maintainer="mike@program.com.tw"

ENV DEBIAN_FRONTEND=noninteractive
# ARG DEBIAN_FRONTEND=noninteractive
# ENV LANG=C.UTF-8 LC_ALL=C.UTF-8 LANGUAGE=C.UTF-8
# ENV JAVA_HOME=/jdk1.8.0_152
# ENV PATH=$PATH:/jdk1.8.0_152/bin

WORKDIR /var/www/html

# COPY test.text /
# ADD supervisord.conf /etc/supervisord.conf

RUN apt-get -y update

EXPOSE 443

CMD ["apache2ctl", "-D", "FOREGROUND"]
# CMD supervisord -c /etc/supervisord.conf

# 搭配使用
# ENTRYPOINT ["apache2ctl"]
# CMD ["-D", "FOREGROUND"]

```
### 二、參數說明
1. `＃` : 註解

2. `FROM` : 基底image, 可以從docker hub上查找所需要的image去做基底
    * `FROM <<image name>>`
        * ex:`FROM ubuntu:18.04`
    > [name=黃俊智] 可透過`docker search`查找所需的image, 也可直接前往[Docker hub](https://hub.docker.com/)內查找所需的image

3. `MAINTAINER` : 維護者,僅說明而已
    * `MAINTAINER <<維護者>>`
        * ex:`MAINTAINER mike@program.com.tw`

4. `LABEL` : Metadata的相關資訊
    * `LABEL <key>=<value> <key>=<value> <key>=<value>...`
        * ex: `LABEL version="1.0" description="<<說明文字>>" by="<<user name>>" maintainer="維護者"`
    > [name=黃俊智] 可透過`docker inspect`查看該Dockerfile內所寫的LABEL資訊

5. `ENV` :設定環境變數 ( 可修改系統參數。設定後可用於 Dockerfile 的 RUN 與 `docker run` 內。於 running Container 階段使用 )
    * `ENV <key> <value>`
        * ex:`ENV DEBIAN_FRONTEND noninteractive`
    * `ENV <key>=<value> <key>=<value> <key>=<value> ...`
        * ex:`ENV DEBIAN_FRONTEND=noninteractive`
    >[name=黃俊智] 使用變數的方式`$變數`
    >安裝時出現對話框時出現的錯誤,可以透過`DEBIAN_FRONTEND=noninteractive`進行規避
    >不建議設定在環境變數中
    >建議使用`RUN DEBIAN_FRONTEND=noninteractive apt-get install -y python3`方式進行

6. `ARG` :設定在建置映像檔時可傳入的參數 (與`ENV`雷同，可用於 Dockerfile 的 RUN，但是在啟用後無法使用(ENTRYPOINT、CMD、`docker run`)。僅於 Building 階段使用)
    * `ARG <name>[=<default value>]`
        * ex: `ARG built_user=mike`
    >[name=黃俊智] 若未設定預設值或需覆蓋預設值,則在build階段中設置
    > ex:`docker build --build-arg built_user=MikeHuang -t <<image-name>> .`

7. `WORKDIR` :設定工作目錄，當設定WORKDIR後，Dockerfile中的RUN、CMD、ENTRYPOINT、COPY、ADD等指令就會在該工作目錄下執行
    * `WORKDIR <<CONTAINER 目錄>>`
        * ex: `WORKDIR /var/www/html`

8. `RUN` : 在該 image 建構( build )時所需執行的 shell, 有兩種方式可以使用
    * `RUN <<command line>>`
        * ex: `RUN apt-get -y update`
    >[name=黃俊智] 默認使用`/bin/sh -c`進行
    > `\`:斷行 
    > `&&`:串接多個指令;
    > `;`:分隔指令
    * `RUN ["<<可執行文件>>", "<<param1>>", "<<param2>>"]`
        * ex:`RUN ["executable", "param1", "param2"]`
    >[name=黃俊智] exec執行, 不常使用

9. `EXPOSE` :宣告在映像檔中預設要使用(對外)的連接埠
    * `EXPOSE <<PORT>>`
        * ex: `EXPOSE 443`

10. `CMD` : 當 image 啟動為 Container 時要執行的指令,分為三個格式
    * `CMD ["<<可執行文件>>","<<param1>>","<<param2>>"]`
        * ex: `CMD ["apache2ctl", "-D", "FOREGROUND"]`
        * ex: `CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]`
    * `CMD [param1","param2"]`若有設定 ENTRYPOINT 則可以使用該方式進行設定
    * `CMD <<command line>>`
        * ex: `CMD /usr/sbin/apache2ctl -D FOREGROUND`
    >[name=黃俊智]**Dockerfile內只能有一行CMD,若有多行CMD則只有最後一行會生效**
    > `apache2ctl -D FOREGROUND`:在啟用apache時,為了避免docker認為指令已結束而exit, 固使用該指令讓apache在console界面的前端運行。

11. `ENTRYPOINT` :與`CMD`雷同, 分為兩個格式, 與`CMD`不同的是,`ENTRYPOINT`一定會被執行, 且可以在`docker run` 後攜帶參數使用, 可搭配 CMD 使用
    * `ENTRYPOINT <<command line>>`
        * ex: `ENTRYPOINT /usr/sbin/apache2ctl`
    * `ENTRYPOINT ["<<可執行文件>>","<<param1>>","<<param2>>"]`
        * ex: `ENTRYPOINT ["apache2ctl", "-D", "FOREGROUND"]`
        * 搭配`CMD`使用, ex: 
            `ENTRYPOINT ["apache2ctl"]`
            `CMD ["-D", "FOREGROUND"]`
    > [name=黃俊智]**Dockerfile中止能有一行ENTRYPOINT,若有多行則只有最後一行會生效**
12. `COPY` :複製本地端的檔案/目錄到image內的指定位置, 有兩種格式
    * `COPY --chown=<user>:<group> <<來源路徑>> <<來源路徑>> <<來源路徑>> ... << Image 內目的地路徑 >>`:可以額外使用`--chown=<user>:<group>`修改檔案所屬用戶與群組
        * ex: `COPY READEME.md test.json ./`
    * `COPY --chown=<user>:<group> ["<<來源路徑>>", "<<來源路徑>>", "<<來源路徑>>", ..., << Image 內目的地路徑 >>
        * ex: `COPY ["READEME.md", "test.json", "./"]`
13. `ADD` :和COPY一樣，可將本地端的檔案/目錄加到映像檔的指定位置內, 可使用url方式將檔案下載至指定位置。若檔案為tar壓縮文件,格式為gzip、bzip2、xz的狀況,會自動解壓縮到該目錄去
    * `ADD --chown=<user>:<group> <<來源路徑>> <<來源路徑>> <<來源路徑>> ... << Image 內目的地路徑 >>`
    > [name=黃俊智] 官方不建議使用url的方式做相關的處理, 建議使用`RUN`的 `curl`、`wget`方式使用
14. `VOLUME` :建立本機或來自其他容器的掛載點,VOLUME的值可以是JSON的Array格式，也可以是純文字
    * `VOLUME [“/data”]`
15. `USER` :指定運行Container時的用戶名稱或UID 
    * `USER <<daemon>>`
        * ex: `USER root`
16. `ONBUILD` :若這個映像檔是作為其他映像檔的基底時，便需要定義ONBUILD指令。於原本的Dockerfile內不會執行,在被其他Dockerfile內當作基底(FROM)時,才會於該Docker file內執行
    * ex: `ONBUILD ADD . /home/tmp`
    * ex: `ONBUILD mkdir -p /home/demo/docker`
---
## 參、docker-compose 相關說明
* 常用指令 : up、exec、ps、down
### 一、docker-compose.yml Example Code
``` yml
version: '3'：
services: # services 關鍵字後面列出 web, redis 兩項專案中的服務
  web:
    build: . # Build 在同一資料夾的 Dockerfile（描述 Image 要組成的 yaml 檔案）成 container
    ports:
      - "5000:5000" # 外部露出開放的 port 對應到 docker container 的 port
    volumes:
      - .:/code # 要從本地資料夾 mount 掛載進去的資料
    links:
      - redis # 連結到 redis，讓兩個 container 可以互通網路
  redis:
    image: redis # 從 redis image build 出 container

```
### 二、docker-compose.yml參數說明
**YAML 檔案格式，使用空格來縮排**
1. `version`: 目前使用的版本，可以參考官網
2. `services`: services 關鍵字後面列出 web, redis 兩項專案中的服務
    1. `image`: 使用的 docker image
    2. `build`: Dockerfile所在位置,若未設定image,則使用build方式執行
        * `context`:
        * `dockerfile`:
        * `args`:
            * `buildno`:
            * `gitcommithash`:
        * `cache_from`:
        * `labels`:
        * `shm_size`:
        * `target`:
    4. `ports`: 外部露出開放的 port
    5. `volumes`: 要從本地資料夾 mount 掛載進去的資料
    6. `restart`: 
    7. `environment`: 
    8. `links`: 連結到 redis，讓兩個 container 可以互通網路
    9. `networks`:
    10. `depends_on`:
    11. `expose`:
    12. `extra_hosts`:
    13. `deploy`:
        * `replicas`:
    15. `configs`:
    

### 三、docker-compose 指令說明

1. `docker-compose version`
2. `docker-compose config`
3. `docker-compose build`
4. `docker-compose ps`
5. `docker-compose up`
    * `--no-start`參數, 代替`docker-compose create`
7. `docker-compose down`
17. `docker-compose start` 少用
18. `docker-compose stop` 少用
10. `docker-compose kill` 少用
11. `docker-compose restart` 少用
13. `docker-compose rm` 少用
14. `docker-compose pull`
15. `docker-compose push`
17. `docker-compose port`
18. `docker-compose exec`
19. `docker-compose logs`
---
## 肆、Docker Machine

---
## 伍、Docker Swarm

---
## 陸、Supevisor 進程管理工具
使用 Python 進行相關管理
需要進行安裝動作, 並設置`supervisord.conf`檔案
於dockerfile內 需要將該檔案複製進去 `ADD supervisord.conf /etc/supervisord.conf`
並啟動`CMD supervisord -c /etc/supervisord.conf`
### 一、簡易介紹

### 二、supervisord.conf Example Code
``` conf

```
### 三、參數說明
1. `[supervisord]`:
    * `nodaemon=true`: true:保持supervisord在前端運行
        * ex: `nodaemon=true`
2. `[program:<<程序命名>>]`:
    * `command=<<執行程序路徑>>`:可執行程序的路徑
        * ex: `command=/bin/bash -c "/usr/sbin/apache2ctl -DFOREGROUND"`
    * `startsecs=<<秒數>>`:保持開啟N秒後,視同啟動成功(可不設)
        * ex: `startsecs=5`
