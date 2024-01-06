                             
# **指令參考**


## 常用指令
```shell
$ cd .             目錄原地         #. = 原地
$ cd ..            回目錄的上一層    #.. = 上一層
$ cd -             回上一動作的目錄層
$ ls -l            顯示這個目錄內的物件 
$ ls -al           顯示這個目錄內包含隱藏檔的物件
$ mkdir abc        建立 abc 資料夾
$ mv a b           將 a 檔名改成 b
$ cp a b           將 a 檔複製後命名成 b
$ cat a            查 a 檔案內容
$ echo "b" >a.xxx  將 "b" 寫進 a 檔案內
$ pwd              確認當前目錄所在層
$ rm  a            移除 a 檔案
$ rm-rf            強制移除  # 慎用
                   "f"orce = 強制 
                   "r"ecursive = 層遞 
                   空格代表 and
 
$ touch a          新增 a 檔案
$ touch abc/def    在 abc 底下新增 def 檔案
$ vim a            更改 a 檔案內容
$ man man          使用手冊
ctrl+w             一個段落刪除
ctrl+u             整行刪除
ctrl+l             清理排面
ctrl+r             查詢字串
```


## Git指令

#### 基本指令
```shell
$ git init            將資料夾初始化給 Git 版控
$ git status          版控後查詢狀態
$ git add a           將 a 檔案加到暫存區
$ git add .           將本層全部加到暫存區 
$ git add *.html      將 .html 這個類型檔案都加到暫存區  # * = 任意
$ git add --all       從初始化的那個目錄開始包含全部
$ git rm --cached a   將 a 踢出暫存區
$ git commit          暫存區全部加到本地儲存庫
$ git commit -m "a"   暫存區加到本地儲存庫並做命名 a
```

#### 查詢指令
```shell
$ git log                 檢視當前 branch 所有 commit 紀錄
$ git log --oneline       簡短檢視當前分支 commit 紀錄
$ git log --oneline --all 簡短檢視當前全部 commit 紀錄
$ git blame  a            查詢 a 檔案的全部撰寫紀錄
$ git log -p b            查詢 b 目錄底下所有檔案的 commit 紀錄
$ git reflog              查詢 HEAD 底下所有歷程 commit 紀錄 #保留30天
```
```shell
^ ~ 倒退原則
^  = caret = -1  n 個^就往前 n 個版本
~n = tilde = -n  直接往前 n 個版本(可取代^)

例:
^1 = Parents1
^2 = Parents2
~1 = Parents1
~2 = Parents1 再往後
HEAD^   = Parents 1
HEAD^^  = Parents 1 的 Parents 1
HEAD^^2 = Parents 1 的 Parents 2
```


#### 分支指令
```shell
$ git checkout a      切換 HEAD 到分支 a     #新版本 可用 switch 替代
$ git checkout b      還原 b 檔案            #新版本 可用 restore 替代
$ git checkout -b a   建立並切到 a 分支
$ git check HEAD-n a  還原到 n 個版本前的 a 檔案 

$ git branch          查分支
$ git branch a        原地新增 a 分支
$ git branch a id     在 id 地址新增 a 新分支
$ git branch -d a     刪除分支 a   # -D硬刪
$ git branch -f a id  將 a 移到 id 地址
```


#### 合併指令
```shell
$ git merge a          HEAD 位置去合併(吃掉) a 分支
$ git merge a --no-ff  合併過程取消快轉合併 #強制生成完整分支線
$ git merge --abort    取消該次合併

merge合併衝突時
手動確認衝突點 -> vim 修改衝突點 ->  add ->  commit -> 完成合併
rebase合併衝突時
手動確認衝突點 -> vim 修改衝突點 ->  rebase --continue  ->  完成合併
$ git rebase a        將 HEAD 位置放到 a 分支後面延續
```
#### 還原指令
```shell
$ git reset a                帶著 HEAD 跟分支同時回到 a 分支版本
$ git reset a --mixed        版本差異間的檔案丟回工作目錄
$ git reset a --soft         版本差異間的檔案丟回暫存區
$ git reset a --hard         版本差異間的檔案全部捨棄
$ git reset ORIG_HEAD --hard 回到最後一次危險操作
$ git reset id               前往 commit id 的版本      # id=版本號碼
$ git reset id^              前往 commit id 的前一個版本 
$ git reset id~n             前往 commit id 的前 n 個版本 
```

