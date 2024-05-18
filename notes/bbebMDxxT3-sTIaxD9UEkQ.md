# Git 指令
### 初始化 
* git init

### 查看檔案狀態
* git status

### Staged
* git add <filename>
* git add . 

### Unstaged (取消被add過的檔案)
* git reset -- <filname>


### discord changes（還原成add前的內容）
1. git reset -- <filename>
2. git checkout -- <filename>


### 提交Commit
* git commit --m "commit內容"

### 取消上次的commit
使用情境：當commit訊息打錯，會選擇要commit的檔案時，可以退回。
* git reset --soft HEAD~1

HEAD~1代表退回前一次commit
HEAD~2代表退回前二次commit



### 查看commit log
git log

### 開新分支
* git branch -M main 


### 遠端連結到github
* git remote add origin https://github.com/ElaineF2e/first-repos.git
* git push -u origin main
