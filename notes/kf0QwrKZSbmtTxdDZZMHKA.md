---
tags: DD技術讀書會
---
> DD技術讀書會 
> # 命令模式 Command Pattern 
> [name=Ada][time=Fri, Nov 22, 2019] [color=#907bf7]

---
<i class="fa fa-file-text"></i> 目錄：
- [Reference](#Reference)
- [導讀](#導讀)
----
## Reference

| 成員 | Reference | 語言 |
| ------ | ----------- | ----------------- |
| John | https://refactoring.guru/design-patterns/command/php/example#example-0|   |
| 堪哥 | https://www.jianshu.com/p/e2af8c325f15 |  |
| Kevin | https://www.jianshu.com/p/5901e76a6348 |  |
| Han | https://www.jianshu.com/p/ebb8f513f5a5 |  |
| Joy | https://www.jianshu.com/p/0fb670d41139 |  |
| Ada | https://codertw.com/%E5%89%8D%E7%AB%AF%E9%96%8B%E7%99%BC/218145/ |  |


----
## 導讀

### + 命令模式：
:::info
【 命令模式 】
命令模式把一個請求或者操作封裝到一個對象中。命令模式允許系統使用不同的請求把客戶端參數化，對請求排隊或者記錄請求日誌，可以提供命令的撤銷和恢複功能。

簡單來說：
每一個命令都是一個操作，將命令封裝，把「發出命令的責任」和「執行命令的責任」分隔開，委派給不同的對象。

這些命令可以被：
* 重複多次
* 取消
* 取消後又再重做
:::

+ **時機**：
  


---

+ **命令模式涉及到五個角色，他們分別是：**：
* 客戶端角色(Client)：創建一個具體命令ConcreteCommand對象並確定其接收者。
* 請求者角色(Invoker)：負責調用命令對象執行請求，相關的方法叫做行動方法。
* 命令角色(Command)： 聲明一個給所有具體命令類的抽象接口。
* 具體命令角色(ConcreteCommand)：定義一個接收者和行為之間的弱耦合；實現execute()方法，負責調用接收者的相應操作。execute()方法通常叫做執行方法。
* 接收者角色(Receiver)：負責具體實施和執行一個請求。任何一個類都可以成為接收者，實施和執行請求的方法叫做行動方法。

+ **結構圖**：
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_2fd0444baf2af8b9a983cc345659e17f)




### + 範例：
+ **烤羊肉串範例**：

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_fc92ba6dac6ea6ef698102d18a1c9d12)



