---
title: "GitHub Flow 簡記"
tags: hackpad
---

# GitHub Flow 簡記

> [點此觀看原始內容](https://g0v.hackpad.tw/XTJlD7sjy6u)


這邊記錄一下如果採用 GitHub Flow 來整理 issue 的話，需要哪些動作

### 初始設定

- 到  GitHub 網頁 fork 出原專案 (以下假設專案為 g0v/foo ，fork 出為 nobody/foo)
- 設定 git remote
    - git remote add upstream [https://github.com/g0v/foo](https://github.com/g0v/foo)
- 沒事就跟 upstream 同步一下，確保 fork 出來的不要隔太遠
    - git fetch upstream
    - git merge upstream/master

### 提出 issue

- 直接到母 repo 建立 issue 就好，不需要額外做什麼

### 認領 issue

- 到母 repo 上面回覆自己認領了 (以下假設 issue number = 123)
- 到子 repo 上面建立 branch ，在 branch 內修改
    - git branch issue123-foo-bar # 建立 local branch 名稱為 issue123-foo-bar (後面 foo-bar 是這個 issue 的簡單描述，方便從 branch name 知道做了什麼事)
    - git push origin issue123-foo-bar # 到 github 上面產生 remote branch
    - git checkout issue123-foo-bar #  切換 local branch
- 自己的 branch 修改完成之後，到 [https://github.com/nobody/foo](https://github.com/nobody/foo) 下面，以這個 branch 選擇 Open a pull request
    - 在描述中可以塞  "for close #123" 表示這個 PR 是為了解決 issue 123

### upstream 接受 PR 後

- git fetch upstream
- git merge upstream/master
- git branch -d issue123-foo-bar
- git push origin :issue123-foo-bar

