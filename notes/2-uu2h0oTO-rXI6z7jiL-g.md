# Git, Gitlab 說明文件
## 參考資料

## 壹、Git語法說明
### 一、指令說明
1. `init`: 將該資料夾列入git管控

2. `clone`: 複製專案到本地端，基本上專案在新的地方僅用一次，後續使用`pull`或`fetch`進行更新動作。

3. `status`:

4. `add`: 將有異動的檔案放到staging區域內

5. `commit`: 將staging檔案提交到git本地端

6. `push`: 將git本地端資料提交到git server

7. `pull`: 本地端專案更新，遠端數據庫的內容會自動合併
    * ex: `git pull --rebase`
    > [name=黃俊智] `git pull = git fetch + git merge`
    > 一般使用`git fetch --all`進行更新動作
8. `fetch`: 本地端專案更新，可以取得遠端數據庫的最新歷史記錄。
    * ex: `git fetch --all`
9. `branch`:

10. `checkout`:

11. `rebase`:

12. `reset`:

13. `log`:

14. `show`:

15. `merge`:

16. `tag`:

17. `rm`:
    * `git rm --cached`
    * 
18. `mv`:

19. `grep`:

20. `diff`:


### 二、工具說明
1. GitKraken
2. gitk


### 三、相關介紹

---
## 貳、Gitlab 說明
### 一、相關文件介紹
1. `.gitignore`
2. `.gitattributes`
3. `.gitlab-ci.yml`
4. `.editorconfig`
### 二、CI/CD
#### 1. gitlab-ci.yml Demo Code
```yml

```
### 三、

