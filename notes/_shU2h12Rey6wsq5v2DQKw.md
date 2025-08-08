# STM32 NUCLEO-F446RE

![](https://g0v.hackmd.io/_uploads/SJOXvNe_lx.png)

![](https://g0v.hackmd.io/_uploads/rygYAFVxulg.png)

![](https://g0v.hackmd.io/_uploads/H1bj94l_ge.png)

![](https://g0v.hackmd.io/_uploads/r1OYjExuxe.png)

![](https://g0v.hackmd.io/_uploads/BJcLRNg_xx.png)

STM32 Nucleo USB 驅動程式：https://www.st.com/stm32nucleo
(若沒裝USB驅動，某USB裝置會顯示為Unkown)

![](https://g0v.hackmd.io/_uploads/r1fZlBgdee.png)

![](https://g0v.hackmd.io/_uploads/rkVDbSxuge.png)

![](https://g0v.hackmd.io/_uploads/HkMubHldgx.png)

![](https://g0v.hackmd.io/_uploads/SkJbhKgdgg.png)

![](https://g0v.hackmd.io/_uploads/BkNmQceOgg.png)

Solder Bridges (SBxx) 焊點短接，改變電路功能
ON （接通）：焊錫將兩端相連 → 導通
OFF（斷開）：不焊或去除焊錫 → 不導通

1.User Manual（使用者手冊） → 像 NUCLEO-F446RE 這種開發板的 UM1724
說明板子的接腳對應、跳線、USB、LED、按鈕等硬體配置。偏向「教你怎麼用這塊板子」。

2.Datasheet（資料手冊） → DS10693 針對 STM32F446xx 晶片本身的規格
腳位功能表、電氣特性、記憶體容量、最大時脈、封裝尺寸等。偏向「晶片規格與限制」。

3.Reference Manual（參考手冊） → RM0390
詳細描述晶片內部每一個外設（UART、SPI、Timer…）的暫存器、控制位元、運作流程。偏向「工程師調硬體、寫韌體時的技術聖經」。

