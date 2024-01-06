# ASTRO CAMP 6th Day-2 (10/27)

分支
不同分支合併會造成新節點
分支貼紙去除會將該貼紙下的commit隱藏
可用代號取回，若代號不見可以用git reflog查詢軌跡
HEAD可用移到代號上 =>直接co 到代號

合併衝突
git merge --abort 取消合併
手動確認衝突點 -> 修改衝突點-> add -> commit ->結束合併


Rebase
rebase 將分支接到預期的HEAD後方達到合併
git rebase aaa   將HEAD放到aaa後面 
實際狀況=> 在aaa後面建新的commit- >aaa內容物移過去->原本的分支隱藏->結束
好處->不會疊太多分支
壞處->歷史紀錄不見，誰rebase誰不知道

Reset
git reset aaa 不要當成"重新設定" 當成"去" 帶著HEAD跟分支移動

Tap
git tap xxx aaa    x="暱稱" a="代號" tag類似分支但不會動
切tap 只有HEAD移動
通常tap作為里程碑 分支作為階段標記


git hub
ssh=>各給一把鑰匙 上傳不用再打密碼
public key 
private key
ssh-keygen 
cat查詢檔案內容
