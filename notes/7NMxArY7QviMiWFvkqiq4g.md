# 軟體工程實務HW2

> 作業說明：使用

## 錯誤列表

### #1 Bug

:::danger
**問題說明**：
只有從 左上 往 右下 拉才有辦法生成選取範圍
:::
:::info

1. 哪個Case出問題：UseCase C.2
2. function路徑：UMLEditor\UMLEditor\Modes\SelectMode.UpdateSelectArea
3. 根本來源：在計算四個變數的時候只考慮左上往右下的方向
![程式碼來源](https://g0v.hackmd.io/_uploads/H1zEjOlsJg.png)
:::

:::success
**解決辦法**：將取原點的方式取最小值

![正確辦法](https://g0v.hackmd.io/_uploads/B1MG8YgiJg.png)
:::

### #2 Bug

:::danger
**問題說明**：
刪Line會畫面當掉
:::
:::info

1. 哪個Case出問題：G.2
2. 在哪個function(路徑)：UMLEditor\UMLEditor\Pseudo\Combination.Destroy()
3. 根本原因：因為line的combination從未被刪除所以判斷式一直成立

>combination.count從不為0
>![failed](https://g0v.hackmd.io/_uploads/Bk4oZceikx.png)

:::
:::success
將line也寫上刪除combination
![success](https://g0v.hackmd.io/_uploads/SJykfcxiJl.png)

:::
### #3 Bug
