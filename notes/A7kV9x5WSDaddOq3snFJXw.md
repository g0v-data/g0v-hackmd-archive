# 7580-3000 筆記

* **Table ASSY**

1. COMPANY_NAME： 1001 ; PLANT_CODE: 1011
2. PP model's SCHEDULE：week(2) + CUST_CODE(2) + 流水(2)
3. WIP 表：EC_CRM_T_WIP_STATUS (含Bank, WIP, FG Bank)
4. WIP's Key Value：SCHEDULE + TT_YEAR
5. Bank's Key Value：RTNO + PLANT + MATERIAL
6. 大致上的流程：INTRA(Lot在Die Bank且未建工單) → DIE_BANK(Lot在Die Bank且已建工單) → WIP(Lot進入製程) → FG BANK(Lot入成品庫)

* **Table TEST**

1. COMPANY_NAME：1002 ; PLANT_CODE: 1021
2. PP model's SCHEDULE： year(1) + week(2) + Cust_Code(2) + 流水A(2) + 流水B(1)
 → **2000年、2010年、2020年 etc. → 年碼不為0，以A取代之**
3. WIP 表：R_CWIP_01 (含Bank, WIP, FG Bank)
4. WIP's Key Value：SCHEDULE + Z_YEAR + CUST_ID
5. Bank's Key Value：SCHEDULE + Z_YEAR + CUST_ID
6. 大致上的流程：IN_TRA(Lot在018%倉，跨廠運送中) → UN_ISS(Lot在Die Bank) → ISS(Lot進入WIP) → TSTK(Lot在餘數架) → TDRP(Lot入成品庫)

* **Common TIPS**

1. WIP 有可能代表兩種情況：(1)BANK + WIP +FG (2)WIP → 所以要問清楚
2. INTERNAL Turnkey：A → A ; T → T
3. EXTERNAL Turnkey：A → T
4. MM model's SCHEDULE：RTNO + PLANT + MATERIAL (一開始和成品的 RTNO 會不同) → 就是 Bank 啦
5. MM model's common TABLEs：(1)TRANSACTION (2)INVENTORY (3)WAFERIC_INV
6. PP model's common TABLEs：(1)ZOT_20 (2)ZOT_22 (3)ZOT_23 (4)ZOT_25
7. MES model's common TABLEs：(1)WIP_TXN (2)WIP_LOT
8. CHARG = RTNO
9. 材料廠 PLANT_CODE: 1012


* **Turnkey**

1. 須熟悉 ZOT20, ZOT22, ZOT23, ZOT25
2. ISSU：指的是產品/物料的「挪動」 → 通常在溝通時的用法有兩種：(1)下線[ISSU] (2)出貨[GOOD ISSU]
3. GOOD ISSU 通常就是指產品/物料離開 ASE
4. Bank 內的貨 → RT(某箱貨的意思) = BATCH = LOT
5. ASSY / BUMPING 在 ORDER STATUS = 60 時會碰 SCHEDULE
6. TEST 在 ORDER STATUS = 30 時會碰 SCHEDULE
7. Create Lot 指的是 MES 開啟此道程序，但並未開始著手進行 WIP。(若開始進行前則為Start Lot )
8. MM 特性質Table：(1)GRP_MM_T_ZASE_WP (2)GRP_MM_T_ZASE_FG (3)GRP_MM_T_ZASET_WP (4)GRP_MM_T_ZASET_FG
9. 承8.，所有 MM 特性質 Table 的 Key 必須是 MATNR, WERKS, CHARG  (通常要抓最晚入表的一筆才合法)
10. 下 BANK 串上一段資料：用 GRP_MM_T_ZASE_WP
11. 下 MES 串上一段資料：用 GRP_PP_T_ZOT22 (Internal TK，資料較少) 或 GRP_PP_T_ZOT25 (External TK，資料較多)


| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 | Column 6 |
| -------- | -------- | -------- | -------- | -------- | -------- |
| Text     | Text     | Text     | Text     | Text     | Text     |

	R_CWIP_01	DC2(4)	SCHEDULE	Z_Year	RTNO	收料到開DN(Test) [Test WIP 表]		
	EC_CRM_T_WIP_STATUS	DC1(3)	SCHEDULE	TT_YEAR		收料到出貨(Assy) [Assy WIP 表]
   
    GRP_MM_T_INVENTORY	DC1(3)	PLANT	MATERIAL	RTNO	SLOC可判斷當下物料、成品等目前的庫存量 (Bank) 				
	GRP_MM_T_WAFERIC_INV	DC1(3)	PLANT	MATERIAL	RTNO	僅Wafer當下庫存量 (Bank)				
	GRP_MM_T_TRANSACTION	DC1(3)	PLANT	MATERIAL	RTNO	物料於各倉別進出之歷史紀錄 (Bank)				

	GRP_PP_T_ZOT20	DC1(3)	Z_SCHEDULE	Z_YEAR	WERKS	工單，製造成品紀錄	KUNNR客二碼	KONZS群組碼(客三碼)		
	GRP_PP_T_ZOT22	DC1(3)	Z_SCHEDULE	Z_YEAR	WERKS	Order status = 10 建立，Lot資料 (20原料) [原料]			
	GRP_PP_T_ZOT23	DC1(3)	Z_SCHEDULE	Z_YEAR	WERKS	Batch (投料) 資料 (22來源) [原料的batch屬性值]			
	GRP_PP_T_ZOT25	DC1(3)				下線時 (Order status80) 建立，收費用，TurnKey記錄				
	
    GRP_SD_T_DN_HEADER	DC1(3)	F_DN			出貨(DN)主檔				
	GRP_SD_T_DN_ITEM	DC1(3)	F_DN	F_DN_ITEM	F_SUB_LOT	出貨(DN)明細，出貨內容				
	GRP_SD_T_DN_HEADER_ZLF4	DC1(3)	F_DN			出貨主檔,純ZLF4相關(入庫收費用的，假DN主檔資料)				
	GRP_SD_T_DN_ITEM_ZLF4	DC1(3)	F_DN	F_DN_ITEM		出貨明細,純ZLF4相關(入庫收費用的，假DN細項資料)				
	GRP_SD_T_PL_MST	DC1(3)	F_DN			包裝主檔data				
	GRP_SD_T_PL_DTL	DC1(3)	F_DN	F_DN_ITEM		包裝明細，包裝data				
	GRP_SD_T_BILLING_HEADER	DC1(3)	F_BILL_NO			帳單主檔				
	GRP_SD_T_BILLING_ITEM	DC1(3)	F_BILL_NO		F_SUB_LOT	帳單項目明細				
	GRP_SD_T_BILLING_CONDITION	DC1(3)	F_BILL_NO			帳單項目計價細項				

