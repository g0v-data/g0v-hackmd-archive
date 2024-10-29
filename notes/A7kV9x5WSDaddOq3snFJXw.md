# 7580-3000 筆記

* **Table ASSY**

1. COMPANY_NAME： 1001 ; PLANT_CODE: 1011
2. PP model's SCHEDULE：week(2) + CUST_CODE(2) + 流水(2)
3. WIP 表：EC_CRM_T_WIP_STATUS (含Bank, WIP, FG Bank)
4. WIP's Key Value：SCHEDULE + TT_YEAR
5. Bank's Key Value：RTNO + PLANT_CODE + MATERIAL
6. Asst's Bank TABLE：(1)TRSAC (2)INVENTORY (3)WAFERIC_INV

* **Table TEST**

1. COMPANY_NAME：1002 ; PLANT_CODE: 1021
2. PP model's SCHEDULE： year(1) + week(2) + Cust_Code(2) + 流水A(2) + 流水B(1)
3. WIP 表：R_CWIP_01 (含Bank, WIP, FG Bank)
4. WIP's Key Value：SCHEDULE + Z_YEAR + CUST_ID
5. Bank's Key Value：SCHEDULE + Z_YEAR + CUST_ID

* **Common TIPS**

1. WIP 有可能代表兩種情況：(1) BANK + WIP +FG (2)WIP → 所以要問清楚
2. INTERNAL Turnkey：A → A ; T → T
3. EXTERNAL Turnkey：A → T
4. MM model's SCHEDULE：RTNO + PLANT_CODE + MATERIAL_TYPE (一開始和成品的 RTNO 會不同)
5. PP model's common TABLEs：(1)ZOT_20 (2)ZOT_22 (3)ZOT_23 (4)ZOT_25
6. MES model's common TABLEs：(1)WIP_TXN (2)WIP_LOT
7. CHARG = RTNO
8. 材料廠 PLANT_CODE: 1012