# 交通事故通報

2020 年台灣交通事故死亡來到 3000 人，對比鄰近日本 2020 一整年 2839 人死亡，我們的人口只有日本的 1/5 但交通事故死亡居然會比日本還多，由此可見國內交通事故的嚴重性。

今年開始也看到內政部警政署釋出了更多交通事故相關統計資料，所以就想要試著運用這些資料做出更多應用，藉此提醒大家問題的嚴重性；目前主要有下面幾個資料集：
* [即時交通事故資料 (A1類)(json格式)](https://data.gov.tw/dataset/57023)
    * 每週一更新，一般是接近下班時間，遇假日順延
    * A1 的意思是事故發生後有 1 個以上的人在 24 小時內死亡
* [即時交通事故資料 (A2類)(json格式)](https://data.gov.tw/dataset/57024)
    * 半個月更新一次，一般是每月 1 / 16 更新，遇假日順延
    * A2 的意思是事故發生有人受傷，或是有人超過 24 小時死亡
    * 但基本上這份資料只有受傷人數，不會更新符合 A2 定義的死亡數字
* [即時交通事故資料(A3類)](https://data.gov.tw/dataset/87495)
    * 每月更新，但這個資料沒有座標，因為也不涉及傷亡就沒有特別處理

目前應用：
* 地圖 - https://kiang.github.io/NPA_TMA/
* 交通事故通報 - https://github.com/kiang/NPA_TMA/tree/master/report/city

徵求：
* 設計師 - 同樣的資料能夠用什麼方式呈現產生最大的警示效果？目前由 ijs 協助比照衛福部疫情通報風格每週發布交通事故通報，也許可以有其他的延伸
* 事故當事人 - 如果有事故資料對應的當事人願意分享事故發生經過，或許我們可以進一步發展能夠蒐集與呈現這類資料的方式，藉此作為個別區域爭取改善的基礎資料

相關專案：
* 2020 全國交通事故地圖 - https://dubidub.github.io/traffic_accident_2020/zh_tw