# 1.3.1單一處理系統
多年來,大多數系統都使用內含一個處理核心CPU的單一處理器。**核心(core)**是指令執行和暫存器儲存資料的地方。
CPU主要的核心功能為執行通用指令集，包含指令的程序。
並使用磁碟、鍵盤和圖形控制器作配合。

這些特殊用途處理器執行有限的指令集,並且不執行使用者行程。有時,它們被作業系統管理,作業系統傳遞給它們下一個工作訊息並且監督它們的狀態。例如：磁碟控制氣微處理器微處理器由主CPU接收一序列的要求,並執行自己的磁碟佇列和排班演算法。這種安排減輕了主CPU的磁碟排班負擔。

個人電腦在鍵盤中有處理器可以將按下的鍵轉換成編碼,並送到CPU。在其它系統或環境中,特殊用途處理器是低階元件組成的硬體。作業系統與這些處理器無法聯繫；它們獨立自主地作業。使用特殊用途微處理器很普遍,但這不是將單一處理器系統變成多處理器系統。如果只有一個一般用途的單核心中央處理器,
則系統是單一處理器系統。然而,依據這個定義,很少現代電腦系統是單一處理。

# 1.3.2多處理系統

# 1.3.3叢集式系統
叢集式系統(clustered system)：集合許多CPU
和多處理器不同的是他們是由兩個或更多別系統---或節點---連結在一起所組成;
