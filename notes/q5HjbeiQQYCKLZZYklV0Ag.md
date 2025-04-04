---
tags: Law
---

立法院法律沿革查詢工具
=============

想要來做一個能幫較容易查到立法院每一個法條的立法理由，在當初立法時有同時提了哪些版本，哪些人支持哪個版本，當初在立這法條時在院會或委員會是否有說明的記錄

資料來源
-------
* [立法院國會圖書館法律系統](https://lis.ly.gov.tw/lglawc/lglawkm)
    * [爬出來的版本](https://github.com/ronnywang/tw-law-corpus)
    * [上面資料的爬蟲](https://github.com/ronnywang/twlaw)
* [法規資料庫](https://law.moj.gov.tw/)
    * [全國法規資料庫Open API](https://law.moj.gov.tw/api/)
    * [開放資料](https://law.moj.gov.tw/api/swagger/ui/index#/)


相關知識
-------
* [法條對應](https://github.com/ronnywang/twlaw/blob/master/laws.csv)
    * Ex: 01176 => 著作權法
    * 法案名稱可能會修改
        * Ex: 01065 飛航安全調查委員會組織法 => 國家運輸安全調查委員會組織法
        * Ex: 02084 飛航事故調查法 => 運輸事故調查法
    * 不同的法律可能有同樣名稱
        * 02001 和 02050 都是 「交通部公路總局組織法」
        * 02001 的「交通部公路總局組織法」在 1943/3/20 制定
        * 02001 在 2002/5/22 廢止
        * 02050 在 2002/1/21 公布，當時名稱為「交通部公路總局組織條例」
        * 02050 在 2016/11/16 改名為「交通部公路總局組織法」 
    * 只有草案還未通過的法沒有代號
        * Ex: 全國性公民投票不在籍投票法
    * 子法和施行細則沒有代號
* 條文對應
    * 層級 編 => 章 => 條 (編、章不是一定會有)
        * 可能會有之幾
    * 條為基本單位
        * 條可以連結到「立法理由」、「引用條文」、「被引用條文」
        * 條的順序可能會變動
* https://law.moj.gov.tw/Law/LawSearchLaw.aspx
* 法律種類
    * 法
    * 細則、規程、辦法、編制表、準則
* 法律分類
* 相關目標
    1. 可以查詢各法條的修訂歷程
    2. 可以查詢各法條在立法院提案的版本
    3. 可以查詢各法條在委員會審查後的版本
    4. 可以查詢這法條過去有哪些提案沒有被通過
    5. 可以包含未修訂好的法條
    6. 草案階段可能有不同名稱也可以被記錄
    7. 施行細則或子法也希望有修改歷程
* 法學資料庫異動動作
    * 修正　17174
    * 全文修正 35725
        * 新舊法的條號已經無法對上
    * 刪除 1056
    * 制定 42427
    * 增訂 3468
* 議案相關
    * BillNo: 用在議案系統網址上、審查報告的關係文書上面也會有
        * 如果一個議案涉及多個法律時，可能會有多個 BillNo 連結到同一議案
            * [1091013070100100](https://ppg.ly.gov.tw/ppg/bills/1091013070100100/details) 已三讀議案，一共有 33 條法律受到十八歲成年影響
            * [1091013070100101](https://ppg.ly.gov.tw/ppg/bills/1091013070100101/details) 所得稅法部份
            * [1091013070100102](https://ppg.ly.gov.tw/ppg/bills/1091013070100102/details) 遺產及贈與稅法第十七條條文修正草案
            * [1091013070100103](https://ppg.ly.gov.tw/ppg/bills/1091013070100103/details) 兒童及少年福利與權益保障法第二十六條條文修正草案
            * [1091013070100104](https://ppg.ly.gov.tw/ppg/bills/1091013070100104/details) 特殊境遇家庭扶助條例第十二條條文修正草案
            * [1091013070100105](https://ppg.ly.gov.tw/ppg/bills/1091013070100105/details) 全民健康保險法第二條條文修正草案
            * ...
        * 關係文書裡面一次包含 30 幾個法案對照表
    * 立法種類
        * 增訂條文
            * 標題：xxxx增訂第xx條條文草案
        * 制定條文
            * 標題：xxxx法草案
        * 修正條文
            * 標題：xxxx修正草案對照表

資料規劃
-------
- 法律： 
    - 說明：法律的主體
        - PK: 法律代碼
    - 法律代碼
        - 以國會圖書館的代碼為基底，國會圖書館有的法律就在前面加上 01 後面接上國會圖書館代碼，Ex: 著作權法 => 0101176
        - 如果國會圖書館沒有的法律就用 00 開頭
    - 最新名稱
        - 如果是現行母法和現行子法會有確定的名稱，如果只是草案的話名稱可能先以院版本為主？
    - 其他名稱
        - 列出所有不同版本的名稱
    - 現行版本號
        - 連結到「法律版本」資料的「版本號」
    - 種類
        - 現行母法
            - 此種類會有三讀過程資料、相關提案等
            - Ex: 著作權法
        - 現行子法
            - 此種類不會過三讀
            - Ex: 著作權法施行細則
        - 草案
            - 還未變成現行法，目前還有各種草案中
            - Ex: 全國性公民投票不在籍投票法
    - 狀態
        - 施行中、已廢止
    - 立法院代碼
    - 法務部代碼
- 法律版本群組：
    - 說明：
    - PK: (法律代碼, 群組代碼)
    - 法律代碼
    - 群組代碼
        - 以第一個法律版本當作群組代碼？
    - 群組成員
- 法律版本：
    - 說明：法律的修法版本
    - PK：(法律代碼, 法律版本號)
    - 法律代碼：連結到「法律」的「法律代碼」
    - 版本種類：
        - 三讀：「種類=現行母法」時，確定修法的版本
        - 提案：「種類=現行母法　or 草案」時，委員或是政府提出的版本
            - 會有「提案者」的資訊
        - 修正：「種類=現行子法」時，
    - 法律版本號：
        - 以 「bill-{billNo}」為格式名稱，後面 billNo 最後兩碼必為 00 結束
        - 如果是三讀，以三讀通過時間為主
            - 版本號會是 「20210930-三讀」
        - ~~如果是提案和修正，以提案時間為主~~
        - ~~如果同一日期同一提案單位有多個提案，後面可再加上序號~~
        - ~~（確認中）後面可以加上議事公報網的 billNo 嗎？~~
    - 前版本號
    - 法律名稱
        - 這版本內的法律名稱，因為不同版本可能也有不同名字
    - 法條列表
        - 列出所有的法條代碼
- 法律版本法條
    - 說明：版本內的法條變化
    - PK：（法律代碼、法律版本號、法條代碼）
    - 法律代碼
    - 法律版本代碼
    - 法條代碼 
        - 以「20210930-第一條」為代碼，前面日期為這一條第一次提案的日期，後面為提案時的條號（有可能因為之後刪了幾條之後，代碼內的條號跟實際條號會有落差
    - 條號
        - Ex: 第一條、第二條
    - 母層級
        - Ex: 編、章
    - 動作
        - 新增
        - 修改
        - 刪除
    - 內容
        - 直接完整內容，去除條號
    - 此法版本
        - 這版內容是從哪個版本開始的，會連結到法律版本號
    - 前法版本
        - 前一法的內容是哪個版本開始的，會連結到法律版本號，若沒有前一版可以是空白
    - 說明
