# Day 15 - 在少少的戶頭裡轉呀轉呀轉（二）

昨天提到最後一項要刪除轉帳紀錄，因為目前刪除的連動沒有百分百正確對應的方式
所以這裡需要增加一個欄位來做對應來做到正確對應，否則對應錯誤，刪除錯誤的帳務紀錄是很糟糕的一件事(茶

## 移除轉帳紀錄

```
class AddUuidToAccounting < ActiveRecord::Migration[7.0]
  def change
    add_column :accountings, :uuid, :string
  end
end
```

```
# app/models/accounting.rb

class Accounting < ApplicationRecord
  ...

  after_initialize :set_uuid

  def set_uuid
    self.uuid ||= SecureRandom.uuid
  end

  ...
end
```

因為初始化之後就給予 `uuid` 且在 `AccountingProcessService` 內部運作是用 `dup` 的方式製作對應的收支紀錄，所以 uuid 就可以達到一致的目的
所以設定完後其他都不用動，就最起碼能知道「兩筆轉帳收支的對應」這件事

接著要處理刪除的部分，根據相同的 `uuid` 來做撈出後刪除

```
class AccountingsController < ApplicationController
  def destroy
    Accounting.transaction do
      Accounting.where(uuid: @accounting.uuid).each(&:destroy!)
    end

    ...
  end
end
```

這樣就完成了轉帳的初始的三個要求
1.能自主辨識支出的對象為自己的帳戶
2.自動生成一筆對應的「收入」
3.要自動刪除對應的收支

雖然完成了但還想稍微修改一下畫面，因為畫面上不太需要知道兩筆紀錄存在，說實話挺混肴的
所以這邊整體上要針對轉帳的紀錄顯示做點微調，程式碼的部分很細碎就不紀錄了
總之就是顯示時拿掉其中一筆，並且不計入單日加總，而且正負號也拿掉，只留數字做提醒

還有因為之前 `Date` / `DateTime` 拿錯類別了，這裡也順便修正一下這個 Bug ，這樣圖表部分就能正確抓取時間範圍

![https://ithelp.ithome.com.tw/upload/images/20230930/20142040DS4x1i0H1z.png](https://ithelp.ithome.com.tw/upload/images/20230930/20142040DS4x1i0H1z.png)
![https://ithelp.ithome.com.tw/upload/images/20230930/20142040Z4SmFmVRne.png](https://ithelp.ithome.com.tw/upload/images/20230930/20142040Z4SmFmVRne.png)