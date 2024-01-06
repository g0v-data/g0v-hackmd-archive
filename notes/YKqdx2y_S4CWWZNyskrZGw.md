---
title: "快速上手 idea 暫存區"
tags: hackpad
---

# 快速上手 idea 暫存區

> [點此觀看原始內容](https://g0v.hackpad.tw/3pf1YLgoVl2)

讓 non-programmer 快速加入 g0v 專案協作

（以下從 irc 貼過來，有空再整理... hychen++ 都快做完了 XD）

## tools

圖解工具
[https://www.draw.io/?fileId=0B00j8_vTJFGUSGNaRTFEdDNxY2M](https://www.draw.io/?fileId=0B00j8_vTJFGUSGNaRTFEdDNxY2M)
[http://www.graphviz.org/](http://www.graphviz.org/)
[http://www.yworks.com/en/products\_yed\_about.html](http://www.yworks.com/en/products_yed_about.html)


## pre training

hlb        clkao: 話說 hackathon 之前都 pre training 好像不錯
hlb        clkao: 簽下賣身契，教你用 git 之類的
ipa        徵求掛irc不斷線教學
ipa        或是誰要在放隻bot進來，這樣可以輪流壞掉（誤）
ipa: logbot 不曉得有沒有 source code，直接掛到 g0v 的 server 底下應該比較不會死
ipa        iamblue: [http://lzy-blah.blogspot.tw/2007/08/screen-irssi-irc-q.html](http://lzy-blah.blogspot.tw/2007/08/screen-irssi-irc-q.html)
ipa        用這個可以掛irc不斷線 但要有自己的server先
Jedi_        iamblue: 如果沒有自己的伺服器，但是有一台可以穩定一直連線的電腦擺在什麼地方的話.... 可以用用看 [http://quassel-irc.org/](http://quassel-irc.org/)

## dev environment instant setup

架 linux 的話, virtualbox+vagrant 好用 [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) \+ [http://downloads.vagrantup.com/tags/v1.2.2](http://downloads.vagrantup.com/tags/v1.2.2)
最適合不熟 linux 的人的 linux 是 ubuntu 對嗎？
至少是社群最大的(之一)
如果是用 vagrant，可以跳過界面，putty/ssh 進虛擬機就好了
\[13:42\]        ETBlue        還沒裝 /OoO/ 再猶豫要裝啥... 推上有善心人士推薦 mint，[http://www.vagrantbox.es/](http://www.vagrantbox.es/) 裡面有好幾種 ubuntu，真令人困擾
我要把 g0v 的專案資料夾跟 vm 裡的 ubuntu 分享然後在 linux 底下跑 local server \\_/\[14:00\]        clkao        ETBlue: 就.. 12.04 吧
        13.04 也許比較好 不然 nodejs 還要去弄 ppa
想要用 GUI 時再開 virtualbox -- 然後可以弄成和 Windows 7 長的一樣 [http://www.pcworld.com/article/2028896/how-to-make-ubuntu-linux-look-like-windows-7.html](http://www.pcworld.com/article/2028896/how-to-make-ubuntu-linux-look-like-windows-7.html)
\[11:30\]        au        vagrant 是簡化 virtualbox 設定的工具
        可以一鍵裝好 Ubuntu 帳號密碼等並提供 SSH port 連線
        ETBlue        所以是讓我在多台不同電腦之間把各自的 virtualbox 設定成一樣... 喔喔喔
        au        可以透過 shared folder 共用資料夾。
        you got it
\[11:31\]        # [http://blog.roachking.net/blog/2012/12/28/introduce_vagrant/](http://blog.roachking.net/blog/2012/12/28/introduce_vagrant/)
\[11:32\]        ETBlue        ssh port 連線是幹嘛用的 @@? 從 A 電腦連到 B 電腦嗎
        au        是，或從 host machine 連進 virtual machine
        = command line
        ETBlue        疑！！！說到 vagrant也就是說！！！！只要你們把 vagrant file寫好 push 到 github 上面而我 pull 下來，我就可以無腦安裝成跟你們一樣的環境嗎？
而且 clkao 似乎是有寫 Chef file
\[11:38\]        像 liquid-feedback 投票系統之類都可以一鍵安裝
        ETBlue        au: 疑，這麼說來有 vagrant 的話我是不是就不用把 vm 的磁碟位置特別設定到 D 槽了，反正要是暈倒死重灌的話用備份的 vagrant 檔案可以一鍵安裝 virtualbox + ubuntu
\[11:53\]        au        看哪個槽空間大
        沒有差別
\[12:15\]        ETBlue        不同的 g0v project 需要放在不同的 vm 裡面嗎？還是只要開一個 ubuntu 的 vm 然後把不同 project 放在不同資料夾 @@?
\[13:13\]        au        ETBlue: 只要開一個 ubuntu 的 vm 然後把不同 project 放在不同資料夾
\[22:56\]        說到這個環境的問題，au 貼的那個 vagrant 可以解決嗎？clone 下來以後 vagrant up 就自動架好環境，讓我們這些正常人可以快速動手做事 =3=
\[23:03\]        au        有
 [http://www.habdas.org/developing-modern-web-applications-on-windows-vagrant/](http://www.habdas.org/developing-modern-web-applications-on-windows-vagrant/)
        kcwu        au's url: \[Developing modern web applications on Windows with Vagrant - habdas.org\]
        au        就是在講這件事。
\[23:04\]        好像應該來找找有沒有已經組好的
\[00:46\]        au        ETBlue: 既然 tka 醒來了那試著把 vagrant ssh + PuTTY 弄好看看?
        hychen        ETBlue, ubuntu 如果有問題可以問我, 我在Canonical工作
        hychen        clkao, 那我出個g0v專用12.04? 內建新的node.js
\[02:14\]        hychen        preseed 寫好了, 不過還沒測, [http://g0v.github.io/d-i/](http://g0v.github.io/d-i/)
([https://github.com/g0v/d-i](https://github.com/g0v/d-i))
\[07:43\]        hychen        用vagrant不知道會不會比較簡單?
\[08:02\]        不過還是要自己先弄一個virtualbox exported tarball..
        那還是先做一個auto installation preseed 先....

g0v 用vagrant box: [https://dl.dropboxusercontent.com/u/4339854/g0v/g0v-ubuntu-precise64.box](https://dl.dropboxusercontent.com/u/4339854/g0v/g0v-ubuntu-precise64.box) (12.04 cloudimg+nodejs+ruby+compass+sass+chef)

理論上開工只要4個步驟做設定
- install vagrant (> 1.1.x
- vagrant box add g0v  [https://dl.dropboxusercontent.com/u/4339854/g0v/g0v-ubuntu-precise64.box](https://dl.dropboxusercontent.com/u/4339854/g0v/g0v-ubuntu-precise64.box)
- git clone ${git repository}
- vagrant up

這樣就可以打開瀏覽器連到 localhost: 6987 看專案的網頁了. (如果這是一個做網站的專案)

為了達成這點，所有的專案要撰寫自己的Vagrantfile
- 使用的base box
- port frwarding (在hack.g0v.tw裡面，把brunch server的port 3333 mapping 到 6987)


