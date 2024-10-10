* 	監控單位(網頁):
1. 國防部 www.mnd.gov.tw、www-mnd-gov-tw-01-d3hddnfbecgmc7d0.a01.azurefd.net 
1. 陸軍司令部 army.mnd.gov.tw、army-mnd-gov-tw-01-dwajdzgbf0ckafft.a01.azurefd.net 
1. 海軍官校 www.cna.edu.tw、www-cna-edu-tw-01-d6g6fmgzhgdranbk.a01.azurefd.net 
1. 海軍司令部 navy.mnd.gov.tw、navy-mnd-gov-tw-e5b7gwa2cab0cfbm.a01.azurefd.net 
1. 全民防衛動員署 adma.mnd.gov.tw、adma-mnd-gov-tw-h3d3a3gqb4b8dnbb.a01.azurefd.net


* 情境語法:
1.	針對陸軍司令部的WAF日誌查察1600-1800前10大攻擊手法
AzureDiagnostics
| where Category == "FrontDoorWebApplicationFirewallLog" and ( host_s == "army.mnd.gov.tw" or host_s == "army-mnd-gov-tw-01-dwajdzgbf0ckafft.a01.azurefd.net" )
| where TimeGenerated between (datetime(2024-10-01T08:00:00Z) .. datetime(2024-10-01T10:00:00Z))
| summarize count () by ruleName_s
| top 10 by count_



