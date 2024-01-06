# gitlab-ci.yml 說明文件

## 0. 
* https://medium.com/nick-%E5%B7%A5%E7%A8%8B%E5%B8%AB%E5%AD%B8%E7%BF%92%E8%A8%98/%E6%95%99%E5%AD%B8-gitlab-ci-%E5%85%A5%E9%96%80%E5%AF%A6%E4%BD%9C-%E8%87%AA%E5%8B%95%E5%8C%96%E9%83%A8%E7%BD%B2%E7%AF%87-ci-cd-%E7%B3%BB%E5%88%97%E5%88%86%E4%BA%AB%E6%96%87-cbb5100a73d4?
* https://juejin.im/post/5b1a4438e51d4506d1680ee9
* https://medium.com/nick-%E5%B7%A5%E7%A8%8B%E5%B8%AB%E5%AD%B8%E7%BF%92%E8%A8%98/gitlab-ci-%E5%85%A5%E9%96%80%E7%AD%86%E8%A8%98-%E5%96%AE%E5%85%83%E6%B8%AC%E8%A9%A6%E7%AF%87-156455e2ad9f
* https://gitlab.com/DevOpsTaiwan/coscup2017-workshop-101/blob/master/composer.json
* https://xenby.com/b/178-%E6%95%99%E5%AD%B8-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8gitlab-ci%E4%BE%86%E9%81%94%E5%88%B0%E8%87%AA%E5%8B%95%E5%8C%96%E6%B8%AC%E8%A9%A6%E8%88%87%E4%BD%88%E7%BD%B2
* https://kheresy.wordpress.com/2019/02/13/gitlab-ci-cd/
* https://greddywork.gitlab.io/greddyblogs/2019/02/19/gitlabCicd/

## 1. Example Code
```yaml=
image: ruby:2.1
services:
    - postgres
before_script:
    - bundle install    
after_script:
    - rm secrets
stages:
    - build
    - test
    - deploy
job1:
    stage: build
    script:
        - execute-script-for-job1
    only:
        - master
    tags:
        -docker5+4x5=25
```
## 2.主要參數說明
* image : 使用的docker image
* stages : 定義需要pipline的階段, 用範例來看 需要跑三個階段, 會依照順序進行
* before_script : 在每個job運行之前需要執行的命令
* after_script : 在每個job運行之後需要執行的命令
* cache : 定義一組文件列表, 可在執行階段中使用
* variable : 變數定義
* services : 使用的docker服務
* job1 : Job1名子,可自定義
    * stage : 為在哪個階段執行
    * script : 要執行的cmd
    * only : 執行在哪個issue內(一般來說僅master會做這樣的設定)
    * tags: 使用哪個gitlab-runner去跑, 若沒宣告 則用default的image
    * artifacts : 
        * expire_in : 
        * paths : 
    * cache : 
        * key : 
        * paths : 
    * dependencies : 
    * when : 

## 3.細部說明
* before_script 後面的資訊為cmd line的語法, 會依序執行, 反斜線不會有換行效果, && 不會有段行效果, 每一個語法皆需要使用 - 進行分隔執行, 一般都會先在image內將大致環境設定好, 剩餘的會在composer內進行處理
* stages 一般分為 init->build-> test->deploy
* variable定義變數 : https://juejin.im/post/5b1a4438e51d4506d1680ee9


## gitlab runner
* 說明網址: 
    * https://xenby.com/b/178-%E6%95%99%E5%AD%B8-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8gitlab-ci%E4%BE%86%E9%81%94%E5%88%B0%E8%87%AA%E5%8B%95%E5%8C%96%E6%B8%AC%E8%A9%A6%E8%88%87%E4%BD%88%E7%BD%B2
    * https://medium.com/@mvpdw06/%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-gitlab-ci-ebf0b68ce24b
* 必須先安裝好Docker
* 需要在專案的Settings->CI/CD->Runners取得specific Runner manually資訊
    * url: https://gitlab.com/
    * token: 3prCrzWF-Jzj-JuuLu-j
* /path/to/config 為config存放位置
- 建立 gitlab runner的docker
```shell= script
docker run --rm -t -i -v /path/to/config:/etc/gitlab-runner --name gitlab-runner gitlab/gitlab-runner register
```
``` text
Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
    https://gitlab.com/
Please enter the gitlab-ci token for this runner:
    3prCrzWF-Jzj-JuuLu-j
Please enter the gitlab-ci description for this runner:
    [f5523acb9c2b]:try gitlab ci/cd
Please enter the gitlab-ci tags for this runner (comma separated):
    test1
Registering runner... succeeded                     runner=3prCrzWF
Please enter the executor: custom, docker, docker-ssh, parallels, shell, ssh, virtualbox, kubernetes, docker+machine, docker-ssh+machine:
    docker
Please enter the default Docker image (e.g. ruby:2.6):
    ubuntu:16.04
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded! 
```
- 啟動 gitlab runner
    - /path/to/config為設定檔資料夾位置
        - ~/work/git/mike/config 
``` shell= script
docker run -d --name gitlab-runner --restart always -v /path/to/config:/etc/gitlab-runner -v /var/run/docker.sock:/var/run/docker.sock gitlab/gitlab-runner:latest
```
- 啟動後 可以在專案的Settings->CI/CD->Runners->Runners activated for this project看到該runner

## 基本製作流程
1. 將docker製作出來 內部設定所需相關環境(apache, php laravel安裝, http、https設定)
2. 設定gitlab-ci步驟分佈
    2.1. 設定init步驟 : 基本coding style驗證
    2.2. 設定build步驟 : composer install、.env設定、php artisan key創建
    2.3. 設定test步驟 : php artisan migrate測試、unit test測試、
    2.4. 設定 depoly-test : 將資料部屬到測試機器
    2.5. 設定 depoly : 將資料部屬到正式機器,一般設定在master內

## 相關工具
* git
* docker
* gitlab runner
* composer
* docker-compose
* 