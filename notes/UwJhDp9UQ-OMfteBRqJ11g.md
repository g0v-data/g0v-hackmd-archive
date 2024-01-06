---
title: "台灣企業集團母子公司關係與環境社會責任"
tags: 企業集團
---

# 台灣企業集團母子公司關係與環境社會責任


## 動機

台灣企業集團的影響力越來越大、結構越來越複雜：近年來台灣企業集團的規模不斷擴大，而且對於一般民眾的影響也越來越全面，例如台塑企業下面有石化、醫療、生機等企業。對許多企業社會責任議題來說，總是難以加總與釐清企業集團的總體責任。

## 目標

1.  建立台灣企業集團資料爬蟲, 可定期更新集團資訊.
2.  提供台灣企業集團架構查詢界面,
3.  結合環保, 勞工資料, 使監督層面能夠擴及企業集團

## 資料來源

1.  公開資訊觀測站: 根據財報
    - 列入合併財務報表之子公司(table_1)
    - 被投資公司名稱、所在地區…等相關資訊(table_2)
    - 轉投資大陸地區之事業相關資訊(table_3)
        - (solved) problem 1: table_1 沒有location.
        =>註記"不明"
        - problem 2: table\_1, table\_2, table_3 名字不一致. 例如
            - (solved)table\_1名字為"台灣通運倉儲股份有限公司（台灣通運公司）", talbe\_2 為"台灣通運公司"
            - (solved)table\_1 名字為"金昌石礦股份有限公司", table\_3為"金昌石礦公司"
        =\> 以table_1 全名為主, 台灣通運倉儲股份有限公司（台灣通運公司）-> 台灣通運倉儲股份有限公司, 台灣 通運公司->台灣通運倉儲股份有限公司
            - (solved)table\_1為本公司/本集團, table\_2為"台灣水泥公司"
        =\> 本公司/本集團的對應表定義於stock_map.json. 需**人工幫忙校正**
            - (can't solve) table\_1為"力豪公司", table\_2為"力豪投資股份有限公司"
        =\> 無法判定為一樣的公司
        - (solved)名字包含"及"或是"及其"或是"、". 例如
            - Natural及Daywinn, 需拆開成"Natural" and "Daywinn" 兩家公司
2.  [http://company-graph.g0v.ronny.tw/](http://company-graph.g0v.ronny.tw/)[:](http://company-graph.g0v.ronny.tw/:) 根據董監事資料
    - 可能問題: 兩家公司出現在這邊不代表是同集團，例如 [中華職棒事業股份有限公司](http://company.g0v.ronny.tw/id/23609506) 的董事有 [統一企業股份有限公司](http://company.g0v.ronny.tw/id/73251209) 和 [味全食品工業股份有限公司](http://company.g0v.ronny.tw/id/11347802) ，但是統一和味全並不是同一集團
    - 根據董監事資料, 可以得知集團母公司，例如從台泥與中橡的董監連坐可得知為同一集團
3.  [data.gov.tw](http://data.gov.tw)
    - 登記工廠名錄
4.  財政部
    - 統一編號, 總機構統一編號(工廠統編可能與公司統編不一樣), 行業別
5.  公司股票代號與全名：利用董監事表, parse title
    - 步驟：
        - download\_category\_xml：下載產業財報 zip
        - 把zip解開
        - parse\_stock\_list: 把財報filename裡的股票代號找出來, 產生stock_map.json (只有股票代號）
        - download_board: 根據股票代號清單, 下載board html
        - parse\_stock\_name：parse board html, 找出公司全名
    - 下市公司： [http://mops.twse.com.tw/mops/web/t51sb01_1](http://mops.twse.com.tw/mops/web/t51sb01_1)
    - 找不到的, 可以查財報裡的"會計師查核報告"表單,  會有公司全名

## 輸出資料格式

- output 1: json format
年度(year)、股票代碼(stock)、子公司列表(sublist) \[母公司(source)、子公司(target)、持股(holder)、target所在地區(location)、source是否為集團核心(is\_coreSource)、表單來源(table\_source1, table\_source2, table\_source3)\]
- output 2: 列入合併財務報表之子公司
- output 3: csv format, 核心公司董監事及法人代表
年度(year)、股票代碼(stock)、公司名稱(target)、總董事席次(totalboard)、總監事席次(totalsupervisor)、董事法人法人代表(source)、董事席次(boardnumber)、監事席次(boardnumber)
- output 4: json format, 轉投資大陸地區之事業相關資訊(包含備註)
年度(year)、股票代碼(stock)、備註詳表(notelist)、子公司列表(sublist) \[ 子公司(target)、備註(note)、持股(holder)、投資方法(method)\]
- output 5: 名稱

## 流程

- 編輯config file
    - 目標年份: config\['start'\]
    - 種類: kind包含: sii(上市), otc(上櫃), rotc(興櫃), pub(公開發行)
        - config\['kind'\]: parse財報與處理董監事資料, 需指定特定種類
        - config\['kind\_list'\]: 下載財報時, 會根據kind\_list 裡的種類依序下載zip
    - 儲存位置:
        - config\['zip_folder'\]: 財報zip
        - config\[kind\]\['xml_folder'\]: 財報解開來的xml存放位置. 各種類的位置分開
        - config\[kind\]\['board_folder'\]: 董監事board html,
        - config\[kind\]\['stock\_map\_json'\]: 公司股票代號與全名的對應表
        - config\[kind\]\['mops_folder'\]: 財報處理後的json
> 可以編輯數份config, 例如四個種類的config, 或是數個年份的config
> [name=stardog]

- 從公開資訊關測站下載財報
    - python3 parser.py -t download\_category\_xml -c config.json
    - -c：可以指定config name. config file, 需要放在porject_config下
    - 會根據kind_list 裡的種類依序下載zip
    - zip會儲存在config\['zip_folder'\]
- 把zip解開, 放到config\[kind\]\['xml_folder'\]
- 產生公司股票代號與全名(目前專案下面已經有處理好的stock_map file. 這個步驟可以省略)
    - 把財報filename裡的股票代號找出來, 產生stock_list.json (只有股票代號）
        - python3 parser.py -t parse\_stock\_list -c config.json
        - stock\_list json會儲存在config\[kind\]\['board\_fodler'\]下
    - 根據股票代號清單, 下載board html
        - python3 parser.py -t download_board -c config.json
        - board xml會儲存在config\[kind\]\['board_folder'\]
    - 從董監事html, 找出公司全名
        - python3 parser.py -t parse\_stock\_name -c config.json
        - stock\_map.json會儲存在config\[kind\]\['stock\_map_json'\]
        - Possible Error case:
            - parse\_stock\_name fail=
> 有些公司名字沒有出現在董監事名字中, 我們還可以去財報裡面取得. 但財報的內容沒有統一格式. 需要再人工校對結果
> [name=stardog]

    - 從財報中找出公司全名
        - config\[kind\]\['stock\_map\_missing_list'\]: 從董監事html找不到全名的股票代號
        - python3 parser.py -t parse\_missing\_stock_name -c config.json
        - 產生的stock\_map會產生在config\[kind\]\['missing\_stock\_map\_json'\]
        - 把內從與config\[kind\]\['stock\_map\_json'\]合併
- parse財報, 產生json output
    - python3 parser.py -t parse_folder -c config.json
    - json files會儲存在config\[kind\]\['mops_folder'\]
        - 每個股票代號下面會有三個檔案:
            - {stock}_{year}.json, {stock}_{year}\_name.json, {stock}\_{year}_china.json
    - Possible Error case:
        - We can't find some stock in stock_map, missing stock=
> _stock\_map file在config\[kin\]\['stock\_map\_json'\]. 用來取代財報裡面會出現的"本公司", "母公司". 如果未來有一些新上市的公司財報, 有可能股票所代表的公司不在此檔案裡, 那麼就要更新sotck\_map json file (步驟參考"_公司股票代號與全名")
> [name=stardog]

- 處理董監事資料:
    - python3 parser.py -t parse\_board\_folder -c config.json
    - board.csv會產生在config\[kind\]\['board_folder'\]
    - 檢查董監事資料是否完整: 比較board.csv裡面的股票代號與stock_map裡的股票代號是否一致.
        - python3 parser.py -t check\_board\_status -c config.json
        - Possible Error case:
            - There are some missing stock in board=
        - 檢查失敗原因
        - python3 parser.py -t check\_board\_fail_reason -c config.json
            - 可能導致失敗的結果:
                - 董監事資料顯示查無資料
                - 董監事資料不繼續公開發行
                - 其他原因: 需再細查
- 處理統一編號:
    - 整理公司全名: 例如富強輪胎工廠(股)有限公司->富強輪胎工廠股份有限公司 (人工)
    - 與ronny_wang資料比對([http://company.g0v.ronny.tw/](http://company.g0v.ronny.tw/)), 找出統一編號
- 處理中國子公司的母公司資料 (人工)
    - 比較sublist裡的"note", "method"與notelist的註解
    - 例如
    {
        "target": "上海亞力水泥製品有限公司",
        "holder": "0.9000",
        "note": "",
        "method": 2
    }
    "notelist": \[
    "註一： 係依據同期間經與中華民國會計師事務所有合作關係之國際性會計師事務所查核簽證之財務報表為認列基礎。",
    "註二： 投資方式之種類係(2)透過第三地區公司（亞洲水泥（中國）控股公司）再投資大陸公司。",
    "註三：涉及外幣者，除投資損益係以105年度之平均匯率外，係以105年12月31日之匯率換算為新台幣。"
    \]
    - 上海亞力水泥製品有限公司的母公司為"亞洲水泥(中國)控股公司"
- 建立集團資料
    - 連結子公司列表與董監事資料, source/target出現在公司列表或是董監事法人, 視為同一集團
- 集團資料偵錯(人工)
    - 利用關係圖, 檢查有無斷點. 同一集團內的公司應至少有一持股關係

## 視覺化資料處理

- 將csv轉成(1) 資料呈現用的json (2) 畫關係圖用的json (3) 集團名稱列表
    - edit config: company_folder
    - python3 analysis.py -t generate\_group\_company_folder -c config.json
- 資料用json format
    - company\_summery: 集團代號(group\_no), 集團名稱(group\_name), 集團公司數量(company\_amount), 集團是否有裁罰記錄(has\_fine), 集團內有裁罰記錄的公司數量(fine\_company\_amount), 集團裁罰記錄數量(fine\_record\_num), 集團裁罰金額(fine\_penalty_amount)
    - company\_list:集團內公司關係表(taxcode\_source, source, taxcode_target, target, holder)
    - fine\_company\_list: 集團內有裁罰記錄的公司列表(name, taxcode, penalty\_amount, fine\_num)
    - target\_list: 集團內子公司列表(taxcode, source\_list(holder, name))
- 關係圖用json format
    - nodes: taxcode, no\_holder, is\_core, source (holder, name)
    - links: holder, target(node\_index), source (node\_index)
- 公司股票/公司簡稱列表
    - [http://mops.twse.com.tw/mops/web/t163sb05](http://mops.twse.com.tw/mops/web/t163sb05)
- 集團名稱列表
    - name：核心公司前兩家公司簡稱組合, 例如G1101=台泥中橡集團
    - name_list: 集團內所有上市/上櫃/興櫃/公開發行的公司簡稱列表
    - fine_num: 集團裁罰記錄數量

## 視覺化

    選單: 年份, 整合內容: 1\. 企業關係下載與查詢 2. 透明足跡(環保署) 3. 重大違規名單 4. 租稅減免 5. 立委金主 6. 商標呈現
- 企業關係下載與查詢
    - UI：集團列表->集團公司列表
    - 功能列表：加上filter (例如省略控股公司, 省略沒有統一編號的公司(可能不在台灣),
        - 下載： 整個集團json zip下載（TBD）
            - todo: 整理集團json, 按照年份與集團擺放
        - 查詢：(1) 查詢某家公司, 列出所屬集團
            - todo: 建立DB, DB column: stock, company name, group ({2013: "G1101", 2014: "", 2015 ...})
            - API query:
                - post body: {"year", "company"}
                - response: {"group\_no", "group\_name"}
        - 關係圖呈現：用圖示表示公司關係 (TBD)
            - todo: 產生畫圖所需的json file
            - filter: 只秀出某間公司相關的關係圖
- 透明足跡：
    - UI： 集團列表->集團公司列表->工廠列表->裁罰記錄
        - filter: 列出有工廠列表的集團, 標上有無裁罰記錄
        - 查詢：(1) 查詢某家集團, 列出有無裁罰記錄. 如果有, 列出裁罰記錄
            - todo: 建立DB, DB column: group\_no, group name, violate\_record
- 重大違規名單: 
    - UI：列出有公司在重大違規名單的集團->列出重大違規的公司列表
- 租稅減免:
    - 資料來源：立委辦公室, 僅是申請名單, 不是核准名單, 也不知道細項
    - UI： 集團列表->有申請租稅減免的公司列表
- 立委金主：
    - UI： 集團列表->贊助立委名單
- 商標呈現：
    - UI： 集團列表->集團公司列表+商標

- 可能需求

## 程式碼

- 財報parser
git@github.com:starsdog/companyParser.git
- 透明足跡UI整合
git@github.com:starsdog/thaubing_UI.git
- 成果
git@github.com:starsdog/openGroups.git

## 資料

[https://drive.google.com/drive/folders/0B1VcEjNwxq8ScW9wNloyYWFXdVE](https://drive.google.com/drive/folders/0B1VcEjNwxq8ScW9wNloyYWFXdVE) （if you need folder access right, please contact yiling, email is yiling.chen@gmail.com)

> 感謝整理，先把本篇 pad 收進 [GXV: Guan Xi Visualized 關係視覺化](https://g0v.hackmd.io/ZLjJxxzSSAelKvbaQbhDIQ) 的 g0v 專案中～
> [name=venev]


