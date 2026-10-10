---
title: # 安全玩水溯溪烤肉的地方
tags: GIS, edu, jothon, river
---
# 安全玩水溯溪烤肉的地方

## 緣起
- 戲水安全區、戲水安全知識
- 虎頭蜂通報

## 可以做的事
1. 溺水熱點由各縣市消防局公布，可以串連所有資料顯示
2. 縣市政府資料沒有經緯度，只有地點敘述時，可以轉化成圖資格式（經緯度等等）
3. 溺水時緊急回報 or 緊急救援工具放置位置（例如 AED）

## 資料蒐集

### 親水地點
- 台灣各瀑布、野溪景點：https://tw.followxiaofei.com/page/%E5%B0%8F%E9%A3%9B%E7%9A%84%E8%87%BA%E7%81%A3%E6%BA%AB%E6%B3%89%E8%88%87%E7%80%91%E5%B8%83%E5%9C%B0%E5%9C%96

### 水域示警資料
- 摘自貼文：成功大學近海水文中心透過分析2013至2017年的468幅衛星影像，以學理上邊緣判識技術萃取碎波帶斷裂帶，分析出台灣本島海岸計有46處海灘為離岸流發生熱區。
    - https://www.facebook.com/belikeafish/posts/pfbid02NfYrtRyAcuJkfMVbRrrhLUrHiNh5Ubn1v8cg64ATyKUgpJQHyhWr2owgpANx581wl
- 內政部消防署，公布的溺水事件
  - https://www.facebook.com/groups/718089658359103/permalink/2274213259413394/
- 海洋遊憩風險
  - https://goocean.namr.gov.tw/home/index
      - https://www.facebook.com/asgis/posts/pfbid025KUZAXJ42or8AEueVb7B2jr73w7LEDBYPNZa9Bxucg5iuhHAAzGGRxxd8SM9Zyedl
- 學生溺水熱點（教育部校安通報）：https://topic.udn.com/event/drowning_prevention

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_79f3626432244741ae2df4973de80d35.png)
<iframe src="https://www.google.com/maps/d/embed?mid=1K3i_daGxwnDhNyeQJwGZpeb1FJVMOFMw" width="640" height="480"></iframe>

- 由縣市政府公布
    - 桃園市禁止或限制水域遊憩活動區域法令：https://data.gov.tw/dataset/142766
        - 欄位：名稱(名稱)、主管機關(主管機關)、限制活動(限制活動)、備註/選填(備註/選填)、違規罰則(違規罰則)、法令依據(法令依據)、坐標系統(坐標系統)、限制區域座標(限制區域座標)、限制區域文字敘述(限制區域文字敘述)、公告連結(公告連結)、法令連結(法令連結)
    - 臺中市危險水域，19 筆資料
        - https://data.gov.tw/dataset/83641
        - 欄位：編號、行政區、主要危險水域地點、水域主管機關、限制活動、違規罰則、法令依據、座標系統、限制區域座標、限制區域文字描述、公告連結1、公告連結2、法令連結1、法令連結2
    - 臺南市政府消防局公布臺南市 109 年度溺水地點https://data.tainan.gov.tw/dataset/drowning-waters/resource/4813f4db-537b-43bd-87aa-5b0fe94a7a09
        - 有地點說明，沒有經緯度
        - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_f9606412ec0b68ca60b9fc52a48df43a.png)
    - 宜蘭縣政府禁止或限制水域遊憩活動區域：https://data.gov.tw/dataset/145928
        - 欄位：名稱、主管機關、限制活動、備註、違規罰則、法令依據、座標系統、限制區域座標、限制區域文字敘述、公告連結、法令連結
    - 宜蘭縣消防局描述宜蘭縣轄內危險水域地點，位置採用文字描述方式
        - https://fire.e-land.gov.tw/News_Content.aspx?n=9F9B301A4FE69455&sms=8E11D1298D7A19C8&s=885CCF40A7FF0826
    - 花蓮縣政府禁止或限制水域遊憩活動區域資料
        - https://data.gov.tw/dataset/148826
        - gasolin> 
            - CSV 轉成 Google spreadsheet https://docs.google.com/spreadsheets/d/1TODu2xT109y_BeDCUaK2WGxDb1NIXZefc7zB8SJTJRE/edit?usp=sharing
            - 花蓮水域遊憩活動管理辦法及公告 https://td.hl.gov.tw/Detail_sp/0642ec9e034f400b820160c5299dd1a1

### 虎頭蜂通報地點

新北市虎頭蜂通報地圖
https://www.facebook.com/share/p/qHyTGNXyQEh7jC12/

## 政策意見蒐集 / 資料分析探討

- 如何打造更安全友善的水域遊憩活動環境，歡迎提供建議與看法！
    - 發布於 2022-03-15，主(協)辦單位 交通部
    - https://join.gov.tw/policies/detail/d8631a3e-3280-4542-8ac0-bb8def64d06e
- 水域有多危險？從水域救援公開資料來分析 by 蓋索林 Gasolin
    - https://blog.gasolin.idv.tw/life/2021-water-rescue/
- 摘：山區散步有時途中會路過一些溪流，我習慣會先上網到經濟部水利署的水文資訊站查一下我要經過的溪流
    - https://www.facebook.com/yuntien/posts/pfbid0KUtj9crSrTSQ7am2W7yk5pH4SvSgBvAa84Fj24ozpDLb96rDMgaJoEfDNokcqYgMl?locale=zh_TW
    - 摘：墜落、蜂螫、雷擊、落石及涉溪沖走這五件事是立即性的風險，瞬間就能致命，連救都不用救，請朋友們一定要用心面對。
- 溪流攔沙壩構造物，對於戲水者產生溺斃危險的肇因探討 https://www.facebook.com/share/p/sPJKX7U5rPgGhUrg/
- 水洞 https://www.facebook.com/share/p/TcAEerfjGxv284AZ/
- 離岸流說明 https://www.facebook.com/share/zL4gZAbRhCwuUiLC/
- 泳衣顏色的辨識度 https://www.facebook.com/share/Gd2xHfZ7hxYtS1Sq/