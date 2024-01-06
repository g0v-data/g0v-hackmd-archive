---
title: "G0V 進擊的專案 (Project Hub)"
tags: g0v.us,hackpad
---

# G0V 進擊的專案 (Project Hub)

> [點此觀看原始內容](https://g0v.hackpad.tw/kiBwRTQKh7T)

最新進度：11/25/2014
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_133fd830fe378db7dabe6701ccf360f8)

1) 用Github activity 計算活躍度
2) 照活躍度排名
3) 匯入所有G0V 專案 Repos 並計算活躍度 (但專案名稱會是英文,而且會跟少數現有但沒有輸入Github url的G0V專案重複)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_908aa1845f50afc66f6a37b16284c02f)
4) 對有Homepage的專案加上首頁圖示

Logo Design
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_a8d2195498b63c3b0fa0fd8970f768f1)

HOME
> 這個是[https://github.com/g0v/project-hub-mockup之後的版本嗎?](https://github.com/g0v/project-hub-mockup之後的版本嗎?)
> [name=Chun L]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_5b04a233c609f5f27d19caf1b42ae8c0)
首頁的右邊那欄東西 Site Filter (Side Bar?)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_54e46e846cbd121a407fb5e6e02bc4b9)
徵求底下是：前端、後端、設計、插畫、企劃、書寫、宣傳
> wow
> [name=Yuan C]

> 這圖為什麼要這麼大...網站全部要用黑體喔!
> [name=Miia C]


Site structure
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8c5d4629899f62620a454fb908d11daa)
Individual project page
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_953cffeac04606d64ecc9306900f0999)

11/24 Idea
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_d9b70262d054c84c3713ff4d8edd9496)



To-Do:
1.  Project information:
    1.  ~Show updated timestamp, created timestamp~
    2.  ~Link to github repo~
    3.  ~Needs (Developer, Data, Marketing, Design)~
    4.  ~Issue count~
    5.  ~Project Status: Production, In progress ...~
    6.  ~Screenshot for production site (link to the production site)~
        1.  [~https://github.com/browserstack/ruby-screenshots/~](https://github.com/browserstack/ruby-screenshots/)
        2.  [~http://www.browserstack.com/screenshots/api~](http://www.browserstack.com/screenshots/api)
        3.  ~Browserstack API access requires $199 plan 囧~
        4.  ~used URLBOX API instead, free 14days trial, but image link maybe void after then~
2.  ~Project Points~
    1.  ~C~~a~~l~~culate project points based on last-commit-time, issues-count, issues-reply-time, etc~
    2.  ~create a  search filter "points" and rank projects based on points~
3.  Navigation
    1.  Sort by updated\_at, issue\_count, project point
    2.  Navigation mode for projects (by popularity, last update)
    3.  Tag should be an another UI widget
    4.  in the search bar, input one word and hit enter should create a filter and clear out the search bar
4.  g0v project template
    1.  Submit github repo url
    2.  Validate g0v_project.json from each github project
    3.  Import g0v_project.json to Firebase

Current Websites:
[http://g0v.github.io/project-hub-mockup](http://g0v.github.io/project-hub-mockup)
[http://g0v.github.io/oh-my-hub/#/projecthub/home](http://g0v.github.io/oh-my-hub/#/projecthub/home)
[http://hack.g0v.tw/project](http://hack.g0v.tw/project)

github repo:
[https://github.com/g0v/](https://github.com/g0v/oh-my-hub)[o](https://github.com/g0v/oh-my-hub)[h-my-hub](https://github.com/g0v/oh-my-hub)

Test data set:
[~https://glaring-torch-1033.firebaseio.com/~](https://glaring-torch-1033.firebaseio.com/)
[https://g0v-project-hub.firebaseio.com/projects](https://g0v-project-hub.firebaseio.com/projects)
> You are not authorized to view this Firebase. 
> [name=Miia C]

Use this one with latest screenshots and scores, etc

To view the database try:
[https://g0v-project-hub.firebaseio.com/projects](https://g0v-project-hub.firebaseio.com/projects.json)[.json](https://g0v-project-hub.firebaseio.com/projects.json)


References:
[http://projects.betanyc.us/#!/](http://projects.betanyc.us/#!/)

Images:
[https://www.flickr.com/creativecommons/by-sa-2.0/](https://www.flickr.com/creativecommons/by-sa-2.0/)

Libraries:
[https://github.com/ajaxorg/node-github](https://github.com/ajaxorg/node-github)
[https://github.com/erkobridee/angularjs-github-info](https://github.com/erkobridee/angularjs-github-info)

