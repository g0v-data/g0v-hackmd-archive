#  UCB授信菜單 => ?UCB.LOANMK

## 12/18 Lending BPA
LOANSTATUS=>AA不是這個，要調整
產品群組與扣款順序、及跟能切換產品有關

LIMIT.PARAMETER
有參數沒用到：8300、2400、8080
未來額度要用新的額度號
如果是循環額度的舊案件要繼續動撥就用新的額度號
EOD=>提息、PE/PS
SOD=>產新的bill

Alternate account => 未來LD DM 時在AL上紀錄LD號碼

## 12/19 Lending BPA
分批動用的設定
提前還款違約金
* charge and fee
    * 一次性用FT收
    * 留欄位輸入額度、Loan編號、保單編號

如未來有新增其他幣別產品，需要在產品別新增幣別，但是也要注意charge也要新增幣別，interest也要

RC.DETAIL=>扣款明細表
如果是來分行進行人工還款並指定某一筆放款帳號，該筆金額只會還該筆放款

## 12/20 Lending BPA
MB的查詢跟交易，Joe先提供功能畫面，後續討論規格
ADVICE =>撥款通知書、繳息還本通知書、部分還本通知書、清償證明

RE.STAT.RANGE
RE.STAT.REP.LINE => Line mapping表

## 12/21 Lending BPA
1. 盤點ROD，提供欄位相關資訊=>給Candy
2. 因Limit的Version是使用核心的，後續升級需要確認
3. TUS 會提供要確認的Version需要升級或是沿用
4. MB要用的eqnuiry格式=>給Joe
5. ENQ LIAB=>核心的額度查詢
6. 提供RC的還款順序
