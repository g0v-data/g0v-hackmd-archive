# MAC初體驗
可以先用手機熱點下載比較快，RUTEN 5G很慢

## 安裝篇
- [Homebrew](https://brew.sh/index_zh-tw)
    - Node `brew install node@12` (LTS=12)
    - Yarn `brew install yarn`
    - [NVM](https://github.com/nvm-sh/nvm)
- [Skype](https://www.skype.com/zh-Hant/get-skype/)
- [Chrome](https://www.google.com/intl/zh-TW/chrome/)
- [Sublime](https://www.sublimetext.com/3)
    - 可以用套件[**PackageSync**](https://packagecontrol.io/packages/PackageSync)將舊電腦的套件清單export出來!
    - 如果有使用**emmet**的，換mac之後要改裝[**emmet2**](https://github.com/emmetio/sublime-text-plugin#installation)
    - Mac版的sublime為了看big5除了要安裝ConvertToUTF8以外，還要安裝Codecs33套件（一樣在Package Control找得到）
- [vscode](https://code.visualstudio.com)
    - 使用setting sync同步套件/設定
    - Project Manager // package
- [iTerm2](https://iterm2.com/)
    - [oh-my-zsh + powerlevel9k(主題)](http://bit.ly/2FHIP1u)
    - [homebrew-cask-fonts](https://github.com/Homebrew/homebrew-cask-fonts)
    - [Pure](https://github.com/sindresorhus/pure) // 主題
    - [autojump](https://github.com/wting/autojump) // plugin
    - [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) // plugin
    - [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) // plugin

## 推薦App(非必要)
- [鼠鬚管輸入法](http://bit.ly/30kPRTy)
    - 如果你也覺得 Mac 輸入法非常難用鼠鬚管是你最後的解脫
    - 需要做一些設定，可以直接找我要by Kevin
- [Alfred](https://www.alfredapp.com/)
    - 阿福管家 號稱有了他你才真正善用了 Mac (但我也不太會用XD)
    - 但至少比內建的 spotlight 好用
    - [阿福配ssh iterm](https://yaoyuanyy.github.io/2019/05/13/%E5%BC%80%E5%8F%91%E6%95%88%E7%8E%87%E7%A5%9E%E6%8F%90%E5%8D%87%E4%B9%8Balfred%E9%9B%86%E6%88%90ssh+iterm/)
- [CheatSheet](https://mediaatelier.com/CheatSheet/)
    - 按住cmd可以顯示當前 APP 的所有快捷鍵
- [Snappy](https://apple.co/2NmpdUO)
    - 截圖軟體 比原生好用
- [Keka](https://www.keka.io/zh-tw/)
    - 解壓縮 就當作是 mac 的 7-zip 即可
- [magnet](https://apps.apple.com/tw/app/magnet/id441258766?mt=12)
    - 分割畫面工具
- cornerstone svn tool
    - [破解](https://blog.csdn.net/u012475191/article/details/103023177)
- [SmartSVN](https://www.smartsvn.com/download/)
    - 我們家svn server版本過舊，有點不相容
    - 目前可以用來看svn log (但是要用它checkout到本機)
    - 提供30天試用，等到過期後照理說有免費版讓你繼續用，等一個月後我再看看

`export HOMEBREW_NO_AUTO_UPDATE=true` 關閉brew install時的自動更新

## 快捷鍵
* ⌘ is the `Command` () key.
* ⌃ is the `Control` key.
* ⌥ is the `Option` (alt) key.
* ⇧ is the `Shift` key.
* ⇪ is the `Caps Lock` key.
* fn is the `Function` key. 
* ⌘ + ⇧ + 3 擷取全螢幕 + 4指定範圍 不指定範圍放開 + space 視窗

## 連線篇
* 開啟 iterm2
    * userName請換成自己的samba帳號
```shell
ssh userName@172.30.0.41
```
* 設定開機自動連線網路磁碟(GUI)
    * [步驟](https://kejyuntw.gitbooks.io/mac-osx-for-newbie/network/network-smb-connect-file-service.html)
    * [補充，有時候螢幕解鎖就斷掉可以參考這篇](https://apple.stackexchange.com/a/306796)
    * 在terminal app裡輸入`defaults write com.apple.finder ShowMountedServersOnDesktop -bool true`可以將掛載的網路硬碟放在桌面
* 同場加映 有alfred的同學看這邊
    * [一行連線 ssh 教學](https://juejin.im/post/5d4d4ce55188255d803f9479)
    * 設定完成有多簡單 大概就這麼簡單
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_ce7705a9f4a0ef78ac5e2099e63b49bc)

* VSCode 有個套件 "Remote Development" 可以在 VSCode 上直接遠端工作 但需要 ubuntu@16.4 (許願更新中)
* 憑證 chrome > security 拖曳下載 > 打開匯入系統 > 打開鑰匙圈 修改憑證為永遠信任
    * [憑證下載](http://git.ruten.tw/devTools/certificate)
* 如何同時使用 wifi && 乙太網路
    * [教學](https://superuser.com/questions/424862/how-do-i-make-certain-web-addresses-use-a-specific-network-adapter-on-mac-os-x/444254#444254)
    * ![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bbf4ba93abd3454c6d2a0ea3594dae1b)
```bash
sudo /sbin/route add -net 172.30.0.0/255 -interface en0
```
