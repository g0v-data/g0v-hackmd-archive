---
title: "projecthub redux"
tags: infras, infrath0n, hackpad
---

# projecthub redux

> [點此觀看原始內容](https://g0v.hackpad.tw/9U6DLtdZc48)


## metadata

- 列表 \- [https://github.com/g0v/awesome-g0v](https://github.com/g0v/awesome-g0v)
    - 整理舊的列表進入 awesome
    - primary key: ":owner/:repo"
    - rules:
        - H1: 四大類
        - H2: 人工分類
        - H3: nested project, 取締一個 li 當 primary, 其他的 part of primary
    - [https://github.com/g0v/awesome-g0v/blob/master/](https://github.com/g0v/awesome-g0v/blob/master/awesome-g0v.json)[awesome-g0v](https://github.com/g0v/awesome-g0v/blob/master/awesome-g0v.json)[.json](https://github.com/g0v/awesome-g0v/blob/master/awesome-g0v.json)

- 列表 \+ g0v.json or civic.json -> api endpoint (先用一堆 json 檔)
    - additional metadata
        - 從 awesome g0v 的結構加註新的 metadata
        - gh-pages 下的 CNAME
    - github.com/g0v/foo (g0v.json) -> (filesystem) g0v/foo.json
    - [x] (先放到 [g0v-data/regsitry](https://github.com/g0v-data/registry))
    - [ ] 自動定期更新
    - [ ] repo-hook -> 有 commit 更新

- defined required fields
```
name - a string specifying the project's name.
name_zh -
status - a string indicating the status of the project. The value MUST be one of:
"Ideation" - brainstorming phase.
"Alpha" - initial prototyping phase and internal testing.
"Beta" - a product is being tested in public.
"Production" - finished Product, with development and maintenance ongoing.
"Archival" - finished Product, but no longer actively maintained.
tags - an array of tag strings to help people search for your project, which SHOULD have at least one item.
license
```
> string value, identifier in : [https://spdx.org/licenses/](https://spdx.org/licenses/)
> [name=Kirby W]

pilot:
- env.g0v.tw
- budget.g0v.tw
- 公司關係圖 ( no g0v.json )
- 立委投票指南
- 急診 ( no g0v.json )
- [http://g0v.tw/en-US/projects.html](http://g0v.tw/en-US/projects.html)

## metadata editor


one client side single page editor, which takes:
- url params for pre-filled content
- desired target repo (optional)
- resulting repo and g0v.json location

shows:
- prefilled form for metadata (like [http://open.dc.gov/civic.json/builder.html](http://open.dc.gov/civic.json/builder.html)
- diff from existing g0v.json

produces:
- [x] final g0v.json
- with github account linked, produces:
- [x] PR for existing g0v.json or civic.json at the target repo)
    - [x] Create a [commit](https://developer.github.com/v3/git/commits/#create-a-commit) and a [branch](https://developer.github.com/v3/git/refs/#create-a-reference)
    - [x] Create a [pull request](https://developer.github.com/v3/pulls/#create-a-pull-request) where base is master head is the branch just created
- create repo if not exists

WIP: [https://poga](https://poga.github.io/metadata-editor/)[.github.io/metadata-editor/](https://poga.github.io/metadata-editor/)

## given hackpad / google sheet search prompt + prefill in editor


find hackpad (via [kcwu backup](https://github.com/g0v-data/hackpad-backup-g0v)) with keywords:
### 專案簡介、要解決的問題


- open issue in awesome-g0v if not exists (use hackpad key)
    - link at a [master awesome-g0v issue](https://github.com/g0v/awesome-g0v/issues/1)
    - also tag the primary hackpad editor if possible
    - provide a link to the editor with pre-fill (TBD)
        - the PR created by editor will link back to this issue
    - editor should have a callback to add comment to the issue with the resulting repo of this issue, add this to the awesome markdown
WIP: [https://github.com/g0v/hackpad-parser](https://github.com/g0v/hackpad-parser)
Result: [https://gist.github.com/jessy1092/0025f7638792f2bc34e382bc969e43fe](https://gist.github.com/jessy1092/0025f7638792f2bc34e382bc969e43fe)

## g0vhelper

See: [g0vhelper](https://g0v.hackpad.tw/g0vhelper-Uv5pR2OeZgm)

## issues aggregator


### Archeology


original hackpad: [g0v tasks queue ](https://g0v.hackpad.tw/1ngNLPX3mLr)
> Current implementation is powered by some code fragment in hack.g0v.tw: [https://github.com/g0v/hack.g0v.tw](https://github.com/g0v/hack.g0v.tw) .
> [name=Jeff H]

new hackpad: [g0v issue tracker](https://g0v.hackpad.tw/iZZmyUdY57c)

[g0v  issue label 定義](https://g0v.hackpad.tw/g0v-issue-label--L23ntanWnv7)

repo: [https://github.com/youchenlee/g0v-issue-tracker](https://github.com/youchenlee/g0v-issue-tracker)

### Wish List


for people to find tasks, filtered by:
- repo language
- required skill (from issue label)

repo issue label sync:
- [https://github.com/repo-utils/org-labels](https://github.com/repo-utils/org-labels)

- [ ] Decide new list of labels [g0v/dev#15](https://github.com/g0v/dev/issues/15)
- [ ] show aggregated issues from repo listed in awesome-g0v
- [ ] allow filtering by:
    - [ ] language
    - [ ] label
- [ ] triage unlabelled

### Design


hack.g0v.tw 加一頁 issue list, 提供 label 列表，按下後在 iframe 中開出 github issue search

#### Leverage github.com advanced search


利用 github.com 的 [advanced search](https://github.com/search/advanced)  找出符合條件的 issues。
> 這樣就不用養 backend 提供搜尋功能
> [name=Jeff H]


Advanced search form 使用 GET method，form parameters 有：
> 這個 form 看起來對應到 github 的 search api:  [https://developer.github.com/v3/search/](https://developer.github.com/v3/search/#search-issues)[#search](https://g0v.hackpad.tw/ep/search/?q=%23search&via=9U6DLtdZc48)[-issues](https://developer.github.com/v3/search/#search-issues)
> [name=Jeff H]


| name | id | data-search-prefix | type | default | example / placeholder |  |
| --- | --- | --- | --- | --- | --- | --- |
| utf8 |  |  | hidden | ✓ |  |  |
| q |  |  | hidden |  | state:open label:OCR |  |
| type |  |  | hidden |  | Repositories |  |
| ref |  |  | hidden | advsearch |  |  |
|  | search_from | user: | text |  |  |  |
|  | search_repos | repo: | text |  | twbs/bootstrap, rails/rails |  |
|  | search_date | created: | text |  | YYYY-MM-DD, YYYY-MM-DD |  |
| l | search_language | language: | select |  |  |  |
|  | search_stars | stars: | text |  | 0..100, 200, >1000 |  |
|  | search_forks | forks: | text |  | 50..100, 200, <5 |  |
|  | search_size | size: | text |  | Repository size in KB |  |
|  | search_push | pushed: | text |  | <YYYY-MM-DD |  |
|  |  | fork: | select |  | options: not, and (true), only (only) | Return repositories \[*\] including forks. |
|  | search_extension | extension: | text |  | rb, py, jpg |  |
|  | search\_file\_size | size: | text |  | 100..8000, >10000 | duplicate with search_size? |
|  | search_path | path: | text |  | /foo/bar/baz/qux |  |
|  |  | fork: | checkbox |  | Return code from forked repositories | duplicate with search_fork |
|  | search_state | state: | select |  | options: open/closed, open (open), closed (closed) |  |
|  | search_comments | comments: | text |  | 0..100, >442 |  |



範例：找出 github.com/g0v 下所有 projects 裡，有標 OCR 的 open issues:
    - From these owners: g0v
    - In the state: open
    - With the labels: OCR
會得到這個 link:  [https://github.com/search?utf8=%E2%9C%93&q=state%3Aopen+label%3AOCR&type=Repositories&ref=advsearch&l=&l=](https://github.com/search?utf8=%E2%9C%93&q=state%3Aopen+label%3AOCR&type=Repositories&ref=advsearch&l=&l=)
再點 Issues 得到這個 link: [https://github.com/search?l=&q=state%3Aopen+label%3AOCR&ref=advsearch&type=Issues&utf8=%E2%9C%93](https://github.com/search?l=&q=state%3Aopen+label%3AOCR&ref=advsearch&type=Issues&utf8=%E2%9C%93)

> 上次聊了 cors 的問題，所以可能的解法還是得讓 server 去 call advance search, 然後 parse html dom。
> [name=JmeHsieh]



### 最新進度

根據前面討論使用 github adv search 的話，會遇到兩個問題
1.  repo 帶在 url params 裡面會遇到 url too long 的 error
2.  會有 cors 的問題，所以還是會需要一台 server 作為 proxy

所以目前採用自架 server 的方式
1.  固定一段時間去 call github api 去的 repo, issues 的 json
2.  把 json 寫進 database
3.  提供 api 介面可 query by labels / language

github repo: [https://github.com/JmeHsieh/issue_aggregator](https://github.com/JmeHsieh/issue_aggregator)
demo: [http://g0vissues.jmehsieh.com/](http://g0vissues.jmehsieh.com/)




## project browser


existing:
- [https://www.codeforamerica.org/brigade/projects](https://www.codeforamerica.org/brigade/projects)
- (待捕)

### Default, allow search for everything

for participants: show everything and allow filtering ?

- allow showing sub-project
- 一鍵加入列表或更新內容 Link to editor

### Featured projects


for public: (show only ones with thumbnails, or projects in beta or production)

show subprojects (derived from g0v.json: with partOf: field)

### 瀏覽器外掛

- 爬蟲類圖鑑 (metadata contains: parserFor:zxxx.gov.tw, serviceFor:ooo.gov.tw)
    - eg: 求職小幫手: 瀏覽勞動部時顯示：講個秘訣
    - eg: 教育部辭典: 顯示：講個秘訣，萌典很好用


    -
## g0vzilla

## status / dashboard

    - beta 版需要的東西
        - g0v domain
        - ga
        - etc...
        -

## tools for migrating g0v.json to civic.json


- review current spec: [g0v.json spec](https://g0v.hackpad.tw/c07sSfauWSc)
- 之前的 g0v label issue [g0v/dev#15](https://github.com/g0v/dev/issues/15)

spec by et: (待捕)


