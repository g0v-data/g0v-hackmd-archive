# 前端開發工具-Angular基礎知識

Angular 12 開發環境說明-保哥
https://gist.github.com/doggy8088/15e434b43992cf25a78700438743774a

Apple-Mac-開發環境指南
1. 安裝Homebrew https://brew.sh/index_zh-tw
    1-1: ```brew help``` 顯示有哪些指令可用
    1-2: ```brew list``` 顯示已安裝多少軟體
    1-3: ```brew search keyword``` 搜尋keyword套件
    1-4: ```brew uninstall keyword``` 移除keyword套件
    1-5: ```brew upgrade keyword``` 更新keyword套件
2. ```brew install git``` 用Homebrew安裝git
    2-1:```git --version``` 查詢git版本, 確認安裝成功
3. 安裝Node Version Manager(nvm) https://github.com/nvm-sh/nvm
    3-1: ```nvm --version``` 查詢nvm版本, 確認安裝成功
    3-2: ```nvm ls-remote``` 用nvm查詢有哪些node版本可以安裝
    3-3: ```nvm install v15.14.0``` 用nvm安裝node
    3-4: ```node -v``` 查詢node版本, 確認安裝成功
4. 安裝編輯器 Visual Studio Code https://code.visualstudio.com/Download
5. ```npm install -g @angular/cli``` 安裝 angular
6. ```ng --version``` check Angular version
7. Angular Document - https://angular.tw/
8. ```ng new project-name --routing --style css --strict=true``` Create Angular project
---

Angular add NgRx library steps-Windows:
1. ```npm install @ngrx/store --save```
2. ```npm install @ngrx/effects --save```
3. ```npm install @ngrx/entity --save```
4. ```npm install @ngrx/store-devtools --save```
5. ```npm install @ngrx/schematics --save-dev```
6. ```ng config cli.defaultCollection @ngrx/schematics```
7. ```ng g store ./store/AppState --root --module ../app.module.ts```
8. ```ng g entity ./store/reducers/entity-name/entity-name --skipTests=true```
9. ```ng g effect ./store/reducers/entity-name/effect-name --root --module app.module --skipTests=true```
10. ```ng g selector ./store/reducers/entity-name/selector-name --skipTests=true```
11. ```ng add @ngrx/store-devtools```
---
Angular add NgRx library steps-MacOS:
1. ```npm install @ngrx/{store,effects,entity,store-devtools,schematics} --save```
2. ```ng config cli.defaultCollection @ngrx/schematics```
3. ```ng g store ./store/AppState --root --module ../app.module.ts```
4. ```ng g entity ./store/reducers/entity-name/entity-name --skipTests=true```
5. ```ng g effect ./store/reducers/entity-name/effect-name --root --module app.module --skipTests=true```
6. ```ng g selector ./store/reducers/entity-name/selector-name --skipTests=true```
7. ```ng add @ngrx/store-devtools```

---
Git 指令:
1. ```git clone project-path ``` 將專案複製一份到自己的電腦上
2. ```git init ``` 啟用Git追蹤
3. ```git status ``` 查看Git狀態
4. ```git checkout -b branch-name``` 新建立分支並切換過去
5. ```git checkout branch-name``` 切換分支
6. ```git add .``` 把修改檔案加入至已暫存區域
7. ```git commit -m "Initial commit"``` 提交commit點
8. ```git merge branch-name``` 合併本機端的分支
9. ```git merge origin/branch-name``` 合併遠端的分支
10. ```git pull origin branch-name``` 拉回遠端branch進度
11. ```git pull --rebase origin branch-name``` 拉回遠端branch進度, 合併不產生commit點
12. ```git push origin branch-name``` 將本地進度推上遠端
13. ```git reset --soft"``` 回到已暫存狀態
14. ```git reset --mixed``` 回到已修改狀態
15. ```git reset --hard ``` 回到已修改狀態
16. ```git branch -d branch-name ``` 刪除branch 狀態

---
Terminal 指令:
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e76579073bda40aed3ddfd2ea2da75e0.png)

|      Apple-Mac        | Widnows-命令提示字元 |      Widnows-Git Bash       |   說明   |
| --------------------- | ------------------ | --------------------------- | ------- |
|     ```ls -al```      |  ```dir /a:h```    |```dir -al``` 或 ```ls -al```|列出隱藏檔案|
|     ```pwd```         |  ```cd```          |          ```pwd```          |列出當前目錄|
|```command``` + ```c```|```ctrl``` + ```c```|   ```ctrl``` + ```ins```    |   複製   |
|```command``` + ```v```|```ctrl``` + ```v```|   ```shift``` + ```ins```   |   貼上   |

---

連猴子都能懂的Git入門指南: https://ppt.cc/fbxlFx

Git運作流程: https://ppt.cc/fbuDpx

Windows Git安裝教學: https://ppt.cc/flCDsx

Git安裝網站: https://git-scm.com/

為你自己學Git-高見龍: https://gitbook.tw

專案練習: https://github.com/bohung/pixroller