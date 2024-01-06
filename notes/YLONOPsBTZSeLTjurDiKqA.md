# Day 16 - 開啟被動收入(ㄧ)

沒錯！今天就要開啟重要的篇幅，實作金流！

## 理解
最麻煩的部分大概就屬於準備這塊了
此次會使用藍星來做為金流的服務商

首先就是申請帳號
另外，必須要先看過文件，包含如何加解密，API 代號與詞彙等細節
~~簡單說就是分開看都懂，拼起來就不懂了，尤其是範例還是 PHP QQ~~

過程中會有需要測試，藍星會提供測試 API 供你確認是否正確的實作
在應用這端則是要做出金流的處理器將資訊的處理器加密後的資料送出，並處理接收回來的內容透過資訊處理器解密後，來做各種應對
所以這裡會用到 ServiceObject 做出下面兩者
1. 包裝處理「金流的 Request / Response」的處理器
2. 加解密的處理器

以上就是對整個實作目前理解

## 準備
在開始動手做處理器之前，要先在藍星申請商店
![https://ithelp.ithome.com.tw/upload/images/20231001/20142040uXIbeqDNMX.png](https://ithelp.ithome.com.tw/upload/images/20231001/20142040uXIbeqDNMX.png)

![https://ithelp.ithome.com.tw/upload/images/20231001/20142040hBRnDwkpBi.png](https://ithelp.ithome.com.tw/upload/images/20231001/20142040hBRnDwkpBi.png)

申請完之後等待申請的期間，先來規劃要提供的服務方案
這邊預期先以單次刷卡的狀況設計，設計兩種服務
1. 永久服務 10塊
2. 單次服務（一個月）1塊

根據這個需求來處理相關的設定
```
rails g model plans
```

```
class CreatePlans < ActiveRecord::Migration[7.0]
  def change
    create_table :plans do |t|
      t.string :name
      t.integer :price

      t.timestamps
    end
  end
end
```

並且會需要紀錄購買記錄（訂單），所以之後也需要開一張表
1.訂單編號
2.訂單金額
3.購買時間
4.訂單種類
5.訂單狀態

```
rails g model orders
```

```
class CreateOrders < ActiveRecord::Migration[7.0]
  def change
    create_table :orders do |t|
      t.string :number, null: false
      t.integer :amount, null: false
      t.integer :state, null: false
      t.bigint :plan_id

      t.timestamps
    end
  end
end
```

關聯也一起做好設定
這樣就做完初步的處理了，明天開始根據文件來實作 ServiceObject
