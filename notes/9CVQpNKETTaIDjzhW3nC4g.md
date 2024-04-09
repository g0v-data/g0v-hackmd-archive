## 原始資料(心智圖)
![image](https://files.furthersoftware.com.tw/assets/Tourmap/xmind.png)

## 需求
- 前台要顯示優惠相關文案在日曆下方
- 連續入住N天要獲得優惠 x %
- 連續購買N筆要獲得優惠 x %
- 優惠計算方式為 訂單總金額 - SUM(適用項目金額 * 適用的優惠總和%)
- 預設影響範圍: 每種產品視為一種項目

## 表格
### 折扣表(暫定)
| Id  | 優惠類型  | 連續天數/購買筆數 | 優惠百分比 | 適用對象類型(目前僅有'產品') |
|-----------------|------------|----------------------|--------------|--------------|
| 1                      | 連續入住  | N 天                        | x %             | 產品      |
| 2                      | 連續購買  | N 筆                        | x %             |  產品    |


## 其他
Peter提供之範例
```
1、連續入住超過3晚給5%的折扣
2、同時訂購5間以上給予3%的折扣

假設張先生使用線上訂房系統訂了A房型2間住3天，B房型1間住3天，C房型5間住5天，請問折扣如何計算？


Ans：

連續入住超過3晚給5%的折扣。
同時訂購5間以上給予3%的折扣。
讓我們來計算張先生的折扣：

A房型2間住3天：

未達到連續入住3晚的要求，因此沒有連續入住折扣。
未達到同時訂購5間以上的要求，因此沒有房間數折扣。
B房型1間住3天：

未達到連續入住3晚的要求，因此沒有連續入住折扣。
未達到同時訂購5間以上的要求，因此沒有房間數折扣。
C房型5間住5天：

符合連續入住超過3晚的要求，可獲得5%的折扣。
訂購了5間以上的房間，因此符合同時訂購5間以上的要求，可獲得3%的折扣。
所以，張先生的折扣計算如下：

A房型：無折扣
B房型：無折扣
C房型：連續入住折扣5% + 房間數折扣3% = 總折扣8%
請注意，這些折扣是可以累加的，但只有符合折扣條件的部分才會獲得相應的折扣。
```

## 實體規劃

### 折扣策略實體規劃
---

![折扣策略實體規劃](https://files.furthersoftware.com.tw/assets/Tourmap/productDescountRule.png)

```c#

public class ProductDiscountRule
{
    public Guid Id { get; set; }

    //目前為productDefinitionId
    public Guid OwnerId { get; set; }

    //數量
    public int Count { get; set; }

    //規則名稱
    public string Title { get; set; }

    //規則描述
    public string Description { get; set; }

    //優惠百分比 0~100
    public int DiscountPercentage { get; set; }

    //是否啟用
    public bool IsEnable { get; set; }

    //計算方法名稱
    public string ProviderKey { get; set; }

    //策略顯示名稱
    public string ProviderName { get; set; }

}
```

目前考慮連續入住和連續購買為全域設定，所以綁在productDefinition上  
且共用實體，DisplayName為策略名稱，且由系統設定，不可修改  
Description為策略名稱，且由系統設定，不可修改  
CountName為數量名稱，由系統設定，不可修改  
DiscountStayName 為計算策略方法名稱，由系統設定，不可修改

舉例:連續入住套用在實體上會變成以下資料

### 連續入住規劃
---

實體規則 :  
預設一定會有一筆連續入住天數為1的資料，並且優惠百分比為0，代表不打折
系統會檢查這筆資料是否存在，若不存在則自動新增

當建立多筆時，系統會檢查是否有符合的連續天數，若有則以最大天數為主(天數不可重複)

舉例:
| Id  | 連續天數  | 優惠百分比 | 是否啟用 |
|-----|------------|----------------------|--------------|
| 1   | 1          | 0%                        | true         |
| 2   | 3          | 5%                        | true         |
| 3   | 5          | 10%                      | true         |

若連續入住天數為4天，則以3天的5%為主
若連續入住天數為6天，則以5天的10%為主
若連續入住天數為2天，則以1天的0%為主

![連續購買實體規劃](https://files.furthersoftware.com.tw/assets/Tourmap/consecutiveStayRule.png)

### 連續購買規劃
---

實體規則 :  
預設一定會有一筆連續購買數量為1的資料，並且優惠百分比為0，代表不打折
系統會檢查這筆資料是否存在，若不存在則自動新增

當建立多筆時，系統會檢查是否有符合的連續購買數量，若有則以最大數量為主(數量不可重複)

舉例:
| Id  | 連續購買數量  | 優惠百分比 | 是否啟用 |
|-----|----------------|----------------------|--------------|
| 1   | 1              | 0%                        | true         |
| 2   | 3              | 5%                        | true         |
| 3   | 5              | 10%                      | true         |

若連續購買數量為4，則以3天的5%為主
若連續購買數量為6，則以5天的10%為主
若連續購買數量為2，則以1天的0%為主

備註: 目前規劃為同個營區算連續購買，即使是不同專案也算連續購買

![連續購買實體規劃](https://files.furthersoftware.com.tw/assets/Tourmap/consecutiveBuyRule.png)

## 計算provider 介面規劃

### provider所需的input及output
---

``` c#
public class CalculateProduct{
    public Guid CategoryId { get; set; }
    public decimal Amount { get; set; }
    public DateTime Date { get; set; }
}

public class CalculateProductInput{
    public OwnerId { get; set; }
    public List<CalculateProduct> Products { get; set; }
}

public class CalculateProductInfo{
    public decimal TotalAmount { get; set; }
    public decimal DiscountAmount { get; set; }
}
```

### provider介面
---  

``` c#
//為連續入住及連續購買提供計算服務
public interface IDiscountStrategy{

    //折扣優先權，數字越大越優先
    int Priority { get; }

    Task<decimal> CalculateAsync(CalculateProductInput input);
}

//用provider把註冊的折扣策略都執行一遍
public interface IDiscountProvider
{
    DiscountProductInfo DiscountCalculateAsync(CalculateProductInput input);
}

public class DiscountProviderConfiguration{

    //是否合併折扣，不是則用優先權最高的折扣
    public bool IsMergeDiscount { get; set; }
}
```


### 折扣規則問題

連續購買的達成條件可能多天同時達成，這樣的話要怎麼計算折扣

方案一 : 以最大連續購買數量為主
舉例: 連續購買數量為3,5,7，分別是不同的天數進行購買，則以7個那天的折扣為主

方案二 : 把所有連續購買數量的折扣都加總
舉例: 連續購買數量為3,5,7，分別是不同的天數進行購買，則把3,5,7的折扣都加總

情境參考:
  根據您提供的折扣規則：

  連續入住超過3晚給5%的折扣。
  同時訂購3間以上給予2%的折扣，同時訂購5間以上給予3%的折扣。

我在2021/01/01買了A1 A2 A3，折扣為5%
我在2021/01/02買了A1 A2 A3 A4 A5，折扣為10%
我在2021/01/03買了A1 A2 A3 A4 A5 A6 A7，折扣為15%

方案一 : 以最大連續購買數量為主
以2021/01/03為主，折扣為15%

方案二 : 把所有連續購買數量的折扣都加總
總價 * 3% + 總價 * 5% + 總價 * 7% = 折扣的價格


### 4/9待討論事項
1.確認同一產品，裸房與專案房可否使用相同的折扣規則  (暫定 相同規則)
2.
購物車商品價格相關欄位，目前瑩為單項的價格計算為 

產品單價 + 加人加價 * 加人數量

這不包含附加服務的部分，目前規劃是把所有營位加總後再計算折扣，目前不考慮附加服務也加入計算
