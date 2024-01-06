# Coding Guildline Sharing

## Eric.T
* 絕對不try catch後不做任何處理
* 若物件有可能是null的地方都要做防呆
* 若物件不應該是null但有可能是null的地方要預先作驗證, 並且在拿到null的時候噴出有意義的錯誤
* Function名稱必須包含動詞
* 絕對不要使用Magic Number & Magic String
* 絕大部分狀況不應該把整個資料表取回來後在程式中處理分頁與篩選邏輯
* 不應該用外部服務的Model貫穿內部系統
* 自動產生的程式碼絕對不應該手動去修改
* 有判斷式的地方都應該要寫進Debug Log
* 呼叫API時永遠要假設他會出錯並且作對應的處理
* 只要有可能沒有值都應該統一用null(ex. DateTime? int?), 不要用min Date or 0當作沒有值
* 要用.First() or Array[0]之前都應該做驗證確定有值可以取
* 盡量避免在迴圈中呼叫API或是存取DB, 盡量把需求收集起來一起存取, 若真的無法避免則應該考慮搭配使用快取
* DB Table統一使用Guid作為唯一值, 再搭配使用RecordId作為ClusterIndex
* 有要呼叫外部API的時候應該要把request & response寫進debug log
* 若有使用Raw SQL, SQL Cmd & Paras要寫進debug log
* 若使用EF之類的ORM來操作DB, Paras要寫進debug log
* 避免DataObject因為共用而導致部分屬性要透過特定方式取得才會有值
 
 ## Andy Lin - Personal principle
 - function的參數必須檢查，不符合規定的參數必須拋出敘述明確的exception
 - SRP (Single Responsibility Principle)
 - function 名稱必須有明確的意圖，甚至必須包含業務需求 
 - 區域變數要小寫開頭
 - 全域常數要全大寫，例如： `CONST_VARIABLE`
 - 全域變數會以 `_` 開頭，例如： `_privateVariable`
 - 盡量不要把 database model 傳到前端
 - 寫邏輯時不求最簡潔的寫法，要把業務邏輯表達清楚(Code as Document)
 
 ## Ray
 * DB Table設計時盡量加上具時序性特性的欄位(RecordId, CreateDate)，就算程式用不到，對於資料管理(ex.備份or刪除)也具有重要的作用。
 
 
 ## ZongYan 
 ### Unit Test
 * 為你自己新寫的程式碼加上測試
 * 測試案例要讓能看得懂，要符合需求的情境，測試程式要重構，並且讓人很容易閱讀你的測試情境
 * business flow main主要商業邏輯替他加測試
 * 實務上最常使用的程式碼先加測試
 * 最常被改到的程式碼加測試
 * Bug / Defect 加測試
 * 跟錢有關的產品(可以馬上賣錢的)、risk、人命、商譽 加測試
 * 測試導入自動化
 * 以上 Message by 針對遺留代碼加入單元測試的藝術 91課程