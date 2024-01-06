## 利率資料存入mysql
1.在資料庫中依照銀行名稱.利率名稱等資訊insert資料(rate_value先設為0)
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1dec278518d695167a44a4dcf87cfbd8)
-程式碼範例
```sql
SELECT * FROM bhitter.rate;
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`, `amount`,`rate_value`) VALUES ('12', '定期儲蓄存款', '一年', '固定', '3000000','0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`, `amount`,`rate_value`) VALUES ('12', '定期儲蓄存款', '一年', '機動', '3000000','0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`,`amount`, `rate_value`) VALUES ('12', '定期儲蓄存款', '十三個', '固定','3000000', '0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`,`amount`, `rate_value`) VALUES ('12', '定期儲蓄存款', '十三個月', '機動','3000000', '0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`, `amount`,`rate_value`) VALUES ('12', '定期儲蓄存款', '二年', '固定', '3000000','0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`, `amount`,`rate_value`) VALUES ('12', '定期儲蓄存款', '二年', '機動', '3000000','0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`, `amount`,`rate_value`) VALUES ('12', '定期儲蓄存款', '三年', '固定', '3000000','0');
INSERT INTO `bhitter`.`rate` (`bank_id`, `rate_name`, `rate_time`, `rate_status`, `amount`,`rate_value`) VALUES ('12', '定期儲蓄存款', '三年', '機動','3000000', '0');

```
2.將爬下來的字串轉為浮點數，以便存入資料庫
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_1e60a19fc1ca6caa0a1ad41c478d67a4)
3.利用pymysql模組連接建立在專教的mysql
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_7b4c39a567fb903a3d04d2b21dea90ad)
4.利用rate_id定位要更新的那筆資料，更改rate_value的部分
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_c3bba56b4c4ad6a6bed5c4d070fc4eff)
5.七家銀行利率資料已建置完畢，共579筆資料
![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_8e51bc983e2270e9d34e655a7f8043da)