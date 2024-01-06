# 小小聚#2 20200609 <span class="label label-success">小小聚</span>

時間：20200609
地點：線上
線上：https://meet.google.com/vnf-brkz-idc

## 參與者簽到：
- deeper
- sonia
- darren

## 待討論
- 公文生成需求釐清 

## 會議記錄
- 確定立委聯絡方式爬完沒
- 希望在 django 後台選完 N 個工廠輸出成一個 odf 或 doc 公文
- 希望在 django 後台增加公文受文者、副本受文者欄位
- 流水號：從「109001」開始編，一個案件可能有多份公文，可跳號
- 副本受文者可能會有特例（eg. 里長）但是會手動編輯 
- 大宗交寄存根／執據希望也一併生成在同一個檔案，並刪除重複的受文者（內政部 etc.）
- 生成地址標籤（cf. 後台使用情境）
- 用繁體「臺」
- 公文有正本副本，要在不同檔案 (low priority)

## 下次待討論事項
- 看能否標記有效照片
- Sample data for test?
- 選擇公文負責人的欄位 & email 會存在哪