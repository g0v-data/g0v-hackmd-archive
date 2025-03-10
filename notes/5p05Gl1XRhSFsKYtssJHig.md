# 2024-02-23 Recap
###### tags: `School`, `recap`
## Recap

- 做新功能要先 commit 存檔
- 修舊 bug 要先 commit 再切回去修
- git commit message 格式
    
    [Git Commit Message 這樣寫會更好，替專案引入規範與範例](https://wadehuanglearning.blogspot.com/2019/05/commit-commit-commit-why-what-commit.html)
    
- 好用工具 & 技巧
    - go2hell
    - iterminal
    - Sublime Text
    - Visual Studio Code
    - git remote 搭配 - -h
        - help：會列出相關 git remote 指令
    - raycast

## Discussion Topics

1. 什麼是好的 coding style?
    1. 1 個 swift 檔案裡面寫 1 個 class 功能就好
    2. 把檔案分成 MVC
    3. 註解的應用
        1. 用 // mark 建立書籤
        2. 用 //TODO: 作為小任務
            可以自己創造 //DOING 紀錄當下進行的階段，避免中離回來忘記在做什麼

            舉例：
            // 1. 拉 table view UI
            // 2. tableview 假資料
            // 3. call API (更新 tableview)
    4. snippets
    可以做自己的範本，例如 button
    可搭配 <#提醒字#> 使用

3. 什麼是 bundle id, deployment target？
    1. bundle id 是 iOS APP 的身分證字號
    2. deployment target 最低支援版本，業界通常會向下相容 2 個版本
    3. 看 iOS 版本的市占率網站：https://gs.statcounter.com/ios-version-market-share/mobile-tablet/worldwide
