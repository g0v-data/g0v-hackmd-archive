# Grafana

## 參考資料
https://github.com/grafana/grafana/issues/17080

https://corpglory.com/s/grafana-react-plugins/

https://blog.csdn.net/Candy_home/article/details/102665934
https://community.grafana.com/t/access-table-data-from-react-plugin/22080
https://www.npmjs.com/package/@grafana/ui
https://zh-hant.reactjs.org/tutorial/tutorial.html
https://technology.amis.nl/2019/10/30/creating-a-custom-plugin-in-grafana-using-react/
https://baurine.netlify.com/2019/11/14/how-make-a-grafana-panel-plugin/
https://fufu.gitbook.io/kk8s/task-memory/15.grafana-info
https://kknews.cc/zh-tw/code/2kg6oqe.html
https://community.grafana.com/t/html-panel-connect-to-data-scource/21409/5
https://juejin.im/entry/5dd1e45c6fb9a0200e1a9abf

https://www.youtube.com/watch?v=Y31wnP_jDBY

https://github.com/grafana/simple-react-panel
https://github.com/MarcusCalidus/marcuscalidus-svg-panel
https://github.com/grafana/clock-panel/blob/master/src/clock_ctrl.ts
https://github.com/grafana/grafana/blob/master/contribute/developer-guide.md


https://grafana.com/blog/2016/04/08/timing-is-everything.-writing-the-clock-panel-plugin-for-grafana-3.0/
https://grafana.com/grafana/plugins/scadavis-synoptic-panel
https://grafana.com/grafana/plugins/ryantxu-ajax-panel
https://grafana.com/grafana/plugins/digrich-bubblechart-panel
https://grafana.com/blog/2019/03/26/writing-react-plugins/

--- 
## 開發事項
* 設定檔位置:
    * grafana ini設定檔案位置: `/etc/grafana/grafana.ini`
        * plugin path修改位置: `[paths]`區塊, `;plugins = /var/lib/grafana/plugins`, 
        若修改請重起grafana server `service grafana-server restart `
* yarn 相關事項:
    * **先進行npm更新後 在進行yarn指令(npm與yarn會衝突)**
    * yarn install: 將套件安裝進去
    * yarn dev: 進行套件編譯
    * yarn watch: 進行套件編譯,並保持編譯狀態(修改後即時顯示)
    * yarn build: 進行編譯
> [name=黃俊智] 若yarn出現"There are no scenarios ; must have at least one"訊息, 則需要重新安裝yarn
> ``` cmd
> sudo apt remove cmdtest
> sudo apt remove yarn 
> curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
> echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list 
> sudo apt update
> sudo apt install yarn
> ```
* npm 相關事項:
    * grafana 相關套件: 
        * `npm i @grafana/data`
        * `npm i @grafana/ui`
        * `npm i @grafana/toolkit`
        * `npm i @grafana/runtime`
        * `npm i @grafana/slate-react`
    * react chart.js 安裝: `npm install --save react-chartjs-2 chart.js`

* [grafana react simple](https://github.com/grafana/simple-react-panel)

---

[node 版本更新參考網址](https://tecadmin.net/upgrade-nodejs-via-npm/)
``` cmd
# node版本需要更新到v10以上 才不會出現Loading Error
node -v 
sudo npm cache clean -f 
sudo npm install -g n 
sudo n stable
sudo ln -sf /usr/local/n/versions/node/12.14.1/bin/node /usr/bin/node
# npm 版本也需要更新
sudo npm update npm -g
```

Panel製作內容
---
* 主要檔案皆放在src內
* plugin.json: 定義logo, name等相關資料
* module.ts: 程式碼
* module.html: 呈現畫面(上)
* options.html: 設定畫面(下)


---
開機自動啟動
sudo update-rc.d grafana-server defaults

斷電重起後的自動登入
上次秒數設定 寫死在db內 
由react 設定刷新秒數
自動秒數設定

react ajax
grafana 位置
/usr/share/grafana/public/views
自動登入？
https://stackoverflow.com/questions/57389522/automatic-authentication-using-grafana-api

# grafana.ini
client_id 為連線後的dashboard網址內取得
client_secret 設定key後取得(目前還沒確認)
設計四個頁面 提供自動登入用
``` ini
#################################### Generic OAuth ##########################
[auth.generic_oauth]
enabled = true
name = OAuth
allow_sign_up = false
client_id = kuwZ2OUWz
client_secret = eyJrIjoibW9QUk83MkZoMW5TTmVZZ0NJRWthSTZGZExNUGZxdHQiLCJuIjoidGVzdGtleSIsImlkIjoxfQ==
scopes = user:email,read:org
auth_url = http://172.16.101.105/oauth/auth.php
token_url = http://172.16.101.105/oauth/token.php
api_url = http://172.16.101.105/oauth/user.php
```