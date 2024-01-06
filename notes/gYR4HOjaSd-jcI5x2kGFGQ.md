---
title: "鄉民關心你 - 專案開發指南"
tags: kuansim,hackpad
---

> [點此觀看原始內容](https://g0v.hackpad.tw/t4obguzZFbd)


### 技術架構(Technique Selection)


- Programming Language:
    - Web: [LiveScript](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDAQFjAA&url=http%3A%2F%2Flivescript.net%2F&ei=afm3UebdE4TTkAW4lYDwCg&usg=AFQjCNHLh2n5SJLJCBB-yTcUJpC4KnqEhQ&sig2=J4XpRoDfOvq4lYkC_wBEMQ) (Frontend and Backend)
    - Glue Tool: Python or any.
- Data Exchange: [JSON](http://www.json.org/)
- Auth: pgrest + nodejs passport
- Backend PgREST:
    - Restful DB: [Postsql](http://www.postgresql.org/) \+ [PgRest](http://postgre.st/)
        - 介紹簡報: [node.js in the database](http://www.slideshare.net/autang/pg-rest-osdctw2013)
        - [https://npmjs.org/package/plv8x](https://npmjs.org/package/plv8x)
    - Test Framwork: [Mocha](http://visionmedia.github.io/mocha/)
- Backend ROR
- Frontend Web:
    - bootstrap
    - [semantic-ui](http://semantic-ui.com/)
    - HTML5 applications Assembler:
        - [Brunch](http://brunch.io/) (....) (in develop branch)
        - [ng-boilerplate](https://github.com/ngbp/ng-boilerplate) (in car branch)
    - MVW Framwork: [AngularJS](http://angularjs.org/)
    - _CSS Authoring Framework:_ [Compass](http://compass-style.org/)
    - Visualization lib: [D3.js](http://d3js.org/)
    - Test Framwork: [Karma](http://karma-runner.github.io/0.10/index.html)
- Frontend Mobile APP
    - Framwork: Any
- Version Control: [Git](http://git-scm.com/)
- Continuation Testing: [Travis](https://travis-ci.org/)
- Develop VM: [Vagrant](http://www.vagrantup.com/)
- Deploy: [Chef](http://www.opscode.com/chef/), [Berkshelf](http://berkshelf.com/)
- Server OS: [GNU/Linux Ubuntu](http://www.ubuntu.com)
- Fake Data Generator:
    - [MoreText](http://more.handlino.com/)
    - QuickCheck-like modules
        - Python: [pytest-quickcheck](https://pypi.python.org/pypi/pytest-quickcheck/)
        - Haskell: [quickcheck](http://www.haskell.org/haskellwiki/Introduction_to_QuickCheck)
- Third party service.
    - webpage screenshot capture: [urlshot ](https://g0v.hackpad.tw/uMqcJrauA7C)
        - [http://blog.darkthread.net/post-2013-08-29-phantomjs.aspx](http://blog.darkthread.net/post-2013-08-29-phantomjs.aspx)
    - 新聞比對(news diff)
            - 國內: [http://newsdiff.g0v.ronny.tw/](http://newsdiff.g0v.ronny.tw/)
            - 國外: [http://newsdiffs.org/](http://newsdiffs.org/)

### Source Code


All: [https://github.com/g0v/kuansim](https://github.com/g0v/kuansim)
前端(Chrome Extension): [https://github.com/g0v/kuansim](https://github.com/g0v/kuansim_chrome)[_chrome](https://github.com/g0v/kuansim_chrome)
前端(Web): [https://github.com/g0v/kuansim-frontend](https://github.com/g0v/kuansim-frontend)
後端(Restful DB): [https://github.com/g0v/kuansim-backend](https://github.com/g0v/kuansim-backend)
後端(ROR): [https://github.com/g0v/kuansim-rails](https://github.com/g0v/kuansim-rails)
Chef Cookbook: [https://github.com/kuansim-cookbooks/](https://github.com/kuansim-cookbooks/)
DevOps codes: [https://github.com/kuansim-](https://github.com/kuansim-devops)[devops](https://github.com/kuansim-devops)

### 專案管理模型


- It is done when it is done
- [TDD](http://en.wikipedia.org/wiki/Test-driven_development) is preferred, but without unit testing is fine.
- [Git branching mode](http://nvie.com/posts/a-successful-git-branching-model/) (非強求, 但新功能不要直接在master 做)
- [Git commit style](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)

### 準備開發環境


- 安裝 Vagrant
    - 閱讀[利用 Vagrant 開發g0v.t](http://hychen.wuweig.org/blog/2013/06/01/develop-g0v-project-with-vagrant/)[ang'](http://hychen.wuweig.org/blog/2013/06/01/develop-g0v-project-with-vagrant/)[w 專案](http://hychen.wuweig.org/blog/2013/06/01/develop-g0v-project-with-vagrant/)
- 安裝 Berkshelf
    $ vagrant plugin install vagrant-berkshelf
- 安裝 Git
- 安裝 [git-flow](http://ihower.tw/blog/archives/5140) , or [flowhub ](https://pypi.python.org/pypi/flowhub/0.5.1a)
- 安裝 [editconfig](http://editorconfig.org/)
- 取得源碼
    $ git clone git@github.com:g0v/kuansim.git
- 啟動DB
    - $ cd kuansim/cookbooks/kuansim
    - kuansim/cookbooks/kuansim $ vagrant up
- 開啟瀏覽器打 [http://localhost:](http://localhost:3000/collections)[3](http://localhost:3000/collections)[0](http://localhost:3000/collections)[0](http://localhost:3000/collections)[0/collections](http://localhost:3000/collections), 即可操作rest api.
    - 停止 service
        - kuansim/cookbooks/kuansim $ vagrant ssh -c "stop kuansim"
- 啟動static web
    - $ cd kuansim/frontend/web
    - $ scripts/server.sh
- 使用方式見
    - import data: [https://github.com/g0v/moedict-data-twblg/blob/master/Makefile](https://github.com/g0v/moedict-data-twblg/blob/master/Makefile)
    - plv8x: [https://npmjs.org/package/plv8x](https://npmjs.org/package/plv8x)


### 準備開發環境 For Windows

據說目前 windows 的安裝方式壞掉了 , 似乎無法抓到 Vbox 檔案 (我是沒有人但我不會修) - 20140325
1.  安裝 Vagrant (1.3.4) [http://downloads.vagrantup.com/](http://downloads.vagrantup.com/)
2.  安裝 virtalbox [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
    1.  確定電腦的 _Virtualization Technology_ enabled
        1.  how? google "\[motherboard\] bios VT"
    2.  Environment variable -> path added C:\\Program Files\\Oracle\\VirtualBox;
    注: Vagrant 1.3.4 只支援 virtalbox 4.0,4.1,4.2 版本
3.  安裝 git (**1.8.4**) [http://git-scm.com/download/win](http://git-scm.com/download/win)
    1.  try cmd -> git (看看有沒有這個指令)
4.  安裝 mingw [http://sourceforge.net/projects/mingw/files/](http://sourceforge.net/projects/mingw/files/)
    1.  MinGW install manager-> Basic Setup -> select
        1.  mingw-developer toolkit
        2.  mingy32-base
        3.  msys-base
    b. Installation -> apply change
    c. environment variable -> path added  C:\\MinGW\\bin;C:\\MinGW\\msys\\1.0\\bin
5.  cmd (開啟-> cmd \[Enter\])
    1.  git clone [https://github.com/g0v/kuansim.git](https://github.com/g0v/kuansim.git)
    2.  git checkout develop    // 確保在 develop branch
    3.  cd kuansim/cookbooks/kuansim
    4.  vagrant plugin install vagrant-berkshelf
    5.  vagrant up
        1.  有可能 第一次fail 但是不要慌，第二次應該OK
        2.  看到 INFO: Chef Run complete in 1419.211913507 seconds 表示成功了!!
    6.  vagrant ssh 就可以進入 vm 開發
    7.  cd /opt/kuansim/backend
    8.  npm start
    9.  開啟瀏覽器 [http://127.0.0.1:3000/collections](http://127.0.0.1:3000/collections) 應該會有些資訊 like \["bookmarks","news","tags","users","webpages"\]


