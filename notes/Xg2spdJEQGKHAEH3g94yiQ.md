---
title: "hack.g0v.tw integration"
tags: hackpad
---

# hack.g0v.tw integration

> [點此觀看原始內容](https://g0v.hackpad.tw/2V47VStOLt8)


## 想法：與「專案列表」頁整合


1.  Issue List + Tag Cloud 放在專案列表右邊當做一個 widget (section)，見 [https://github.com/g0v/hack.g0v.tw/issues/21](https://github.com/g0v/hack.g0v.tw/issues/21)
    1.  可以依據 tag 來  filter 要顯示哪些 issues，效果可以跟 hub 右(大半)邊很像。
    2.  專案名稱自動變成可以 toggle 的 tags。
    3.  github api 應該可以做到所有事情
        1.  因為都是 public repo，所以無需 authentication 即可用 api 讀取內容
        2.  換言之，可以純靠前端 js 拉資料回來，不過要小心有 rate limit，所以拉資料要記得必須 incremental 慢慢增加
            看狀況有可能需要弄個後端當 cache
> Agreed
> [name=isacl]

> Cache 可以像其他專案一樣，用 Firebase 來做
> [name=Jeff H]

> Firebase 用量不會超過吧？
> [name=isacl]

> 或是靠 au 的 ethercalc 也行，哈。
> [name=Jeff H]

> XD cool
> [name=isacl]

2.  專案列表裡，每個專案裡也可以放一些屬於該專案的坑讓大家直接跳
    1.  所以要有個 js (jquery) function，註冊要塞 issue 的 dom element (因為需要 incremental)
    2.  可以傳入 tags, number of issues 等參數，選擇哪些 issues 會被拉回來
3.  整個專案列表這一頁的上方，可以有個 dropdown 之類的東西，讓人們選擇自己本身的(能力)屬性
    1.  這一頁裡許多顯示 issue list 的地方，就可以自動依據 viewer 的屬性，過濾或排序 issues，讓顯示出來的坑更適合跳進去
4.  可以有個「 I'm feeling lucky 」的按鈕，讓系統隨便幫你挑個坑來跳
5.  Question: 該做成 jQuery Plugin 還是 AngularJS controller 呢？
    - 作成 jQuery Plugin 可方便在其他網站 mash up
    - 做成 Angular JS controller 在 hack.g0v.tw 裡整合比較方便
> 我會先做成 angularjs controller，先整 hack.g0v.tw，東西先出來大家比較好想像怎麼改會更好。再說，要 porting 成 jquery-plugin 版簡單多了，angularjs 好複雜。XDD
> [name=Jeff H]




## 畫面截圖

已 push 成新的 branch: [issues](https://github.com/g0v/hack.g0v.tw/tree/issues)

Widget 的樣子
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_19466a449c23fc948e92daea760fb2fb)

Filter 按鈕
瀏覽者可依據自身能力屬性，選擇 filter 條件
- [ ] 瀏覽者的選擇會記憶在 cookie 裡
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_4ec8387580dc52cf882393d14448d5dd)

專案列表按鈕
列出 firebase 裡註冊進 hack.g0v.tw 並且有 github url 的專案。
(不只是 mockup 了，已可與 firebase 連動)
- 顯示專案(中文)名稱
- 因為 github repo name 不一定與 firebase 裡註冊的專案名稱相同，所以以 tag 的形式顯示，同時也暗示了 issue 下面的同一顏色的 tag 亦代表了所屬專案。
- [x] 依據選擇改變按鈕文字。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_0bc3dd2fddc3eec644be543f627e983b)

可以列出 issue 列表了
不過目前僅限 hard code 的兩個專案。
- [x] 與 firebase 抓到的 project list 整合
- [x] 分頁
- [x] ~各專案應該平均分散~應該依據特定條件 sorting 所有 project 的 issues，而非依據 fetch 順序顯示。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f05fd7417afb5259a74a3a1f3e7e5f82)

Issue 的分頁功能
- 使用 angular-ui bootstrap 提供的 directive。
- [x] First/Last/Previous/Next 無法用 &laquo;、&raquo;、&rsaquo; 和 &lsaquo;，應該是因為 & 會被 angular 擋下來。
> 寫成 next-text="'&rsaquo;'" 即可，(angular?!) expression 要 quote 起來。
> [name=Jeff H]

- [ ] 因為有些 issue 的 title 會用到兩行來顯示，所以換頁後，pagination bar 會上下跳動。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2d4fbec98539a1c7f0636dea52cfb6e8)

與 firebase 上的 project list 整合
- 已經可以自動抓到 firebase 上設定好的所有 hosting 在 github 上的專案的 issues。
- 有些 projects，如 kuansim-{frontend,backend} 將 github 上的 issues 功能關掉了。會跳過這些 repositories。
    - [x] 「all projects」也應該 skip 掉這些專案
- [x] 當捲到第 10 頁以後，因為多了一位數字，所以 pagination bar 會因為太長而被截斷換行。
    - 應該要用 &laquo;、&raquo;、&rsaquo; 和 &lsaquo; 來顯示，比較省寬度。
- [ ] 顯示速度變很慢
    - 猜測需等所有 repo 的 issues 都載入後才會顯示。
    - 可能跟寫法有關係。\[ 不熟 angularjs... :-( \]
> 目前觀察有兩個停頓點，我猜測第一個可能跟 Hub.projects 有關，第二個原因尚未明朗。
> [name=Jeff H]

    - [x] 先顯示 loading indicator
> 感謝 dannvix
> [name=Jeff H]

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_574f5de993ff39832cd0822c385336de)

Filter by Project
- Dropdown 裡的 project 改從 model 抓，這樣才能僅列出真的在 github 上有 enable issues 的 project。
- [ ] 僅有一句「底下是一些您可以幫忙的事項，歡迎跳坑。」大概新朋友會看不懂。需要文案支援。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_e08d613d3fcf6343b1717f253e988f4d)

- [ ] 在還沒有載入前，next/last 居然可以按
- 試過預設 $scope.currentPage = 0; 但會變成 first/previous 可以按，且 issue 變成無法載入。

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_61553d553d80d001c30de195758ff868)

Filter by Single Label
- [x] 多選

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_43acce2e60d5b5bf4eff040fcaa36d17)

Filter by Multiple Labels
- [x] dannvix 建議用 [Chosen](http://harvesthq.github.io/chosen/)  來選 labels。
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9d2998adb9e7d732b1d2ba2183b29191)

Filter by Multiple Labels with [Chosen](http://harvesthq.github.io/chosen/)
- dannvix++
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_f29f3bfbaea55bf6b1e33d7816c1fa94)

Filter by Labels from Configuration/Github
- Multi-labels filtering takes AND instead of OR semantic.
- Configure predefined labels in app/jsenv.json
- Group labels in dropdown with predefined/others
- Colorize labels with bundled color value (from jsenv or github)
- [ ] Colorize dropdown items
- [ ] Show label / text like in project dropdown?!
- [x] FIX: light font color in light background-color: [g0v/hack.g0v.tw#32](https://github.com/g0v/hack.g0v.tw/issues/32)
- [ ] Leverage the url field => link to page that describe the label

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_bcae3efa6f1d19aae9ab7fa6b087b724)


## 程式結構


[Jeff Hung](https://g0v.hackpad.tw/ep/profile/viqcwaJVLAO) : 底下是關於程式結構與設計的筆記，歡迎加入討論。
> 我的前端是半調子，懇請大家指教。:-)
> [name=Jeff H]


希望能做成兩段：一個是 jquery-based class 當作 model，另一個是 angularjs controller 負責把 model 跟畫面串接起來。未來希望 model 的部分可以在其他地方被 mash up。

不全用 angularjs 的原因是，mash up 比較簡單，不會 depend on angularjs，不過 jquery 我就假設到處都有了。但是這樣做會比較難利用到 angularjs 的 promise、$timeout 之類的工具。而且能否利用與否還是其次，畢竟 jquery 也不是沒有類似的工具，但怎樣和 controller 串接會比較好，倒是需要弄清楚。
> 這地方我還不太熟，所以得靠慢慢 refactoring 把結構弄好。反正就是 release early，醜媳婦先見公婆啦。歡迎大家多加建議如何改進。
> [name=Jeff H]


- [ ] Angular controller 的部分，未來可以 refactor 出去，變成一個獨立的檔案，與 model 拆開。
    - [ ] Controller (module) 可以改名為 issues
    - Model 部分以後可以給其他專案使用
    - [ ] Controller 可以改寫為 livescript
    - 但 model 仍應維持是 .js，因為其他專案不一定用 angular
    - 與 presentation 相關的東西，應放在 controller 就好。
        - [x] 將 get\_label\_color_type() 移進 controller

等到 model 部分比較確定之後，就可以開始來研究怎麼與 [eo4](https://github.com/miau715/eo4) ([mockup](http://miau715.github.io/eo4/)) 合作了。

目前 paging 是靠 angular-ui bootstrap 的 pagination directive 幫忙。但實際內容的 paging 是在 controller 裡面做，這樣其實不太好，應該做在 model 裡才對。
- [x] 應該這麼說，實際的 issue 資料應該放在 model 裡，controller 依據目前在第幾頁，跟 model 要該 page 的資料來顯示就好。
- 然後 filtering、ordering 與 grouping 等，需由 controller 傳選項入 model 裡，由 model 負責計算。
    - [x] Filter by Project
    - [x] Filter by Single Label
    - [x] Filter by Multiple Labels
    - [x] Filter by Predefined Labels
        - [x] Define Predefined Labels: [g0v/dev#15](https://github.com/g0v/dev/issues/15)
        - [x] predefined labels 放前面，接著一個 divider (in dropdown)，然後是剩下其他的 labels
            - 這樣就可以兼顧 predefined labels 以及其他 label 了。
            - predefined labels 以後也可以改，刪掉也無所謂，就變成「其他 label」繼續留在 issue 跟 dropdown 裡。
            - 因為 Chosen 的限制，改用 <optgroup> 呈現。
        - [x] 有個 json 定義 predefined labels，讓 tool script 跟 frontend 可以共用。
            - 應該弄成跟 github api 給的結構類似，這樣程式好寫。
    - [ ] Filter by Role (so user see only what he can contribute to)
> May not necessary
> [name=Jeff H]

- 我後來又把 paging 交回去給 controller 做了，model 僅負責 filtering、ordering 與 grouping。

現在的 model 也沒有處理 multiple repository backends 的能力，而是在 controller 裡面拉。未來也應該改為由 model 負責。不過因為抓 issues 是 async，當抓到內容後，怎樣與 angular controller 串接，是另一個問題：一邊是 callback based，另一邊則可以是 promise-based。
- [x] 讓 model 可以設定 on_update callback，controller 於此 callback 設定 $scope 即可，也無需 promise-based 了。(即，通通都是 callback-based。:-p)

根據在 irc 上面的討論，資料的更新決定為單向，要改變 issue 內容與狀態，請直接連到 github 上進行。另外，目前暫定也不做 live reload 定時抓 issues 新狀態，因為 issue 的變化還沒有那麼多。










